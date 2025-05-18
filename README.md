# Website Delivery with CloudFront

## Introducing this Project!

In this project, I set up the presentation layer of a three-tier web app.

### Services Used

- S3
- CloudFront

### Concepts Learnt

- Different website files and what they do
- Difference between static websites and web apps
- Setting up a CloudFront distribution
- Origin access control (OAC)
- S3 bucket policies

### Architecture Diagram

![Image](https://github.com/sumeet15n/website-delivery-with-CloudFront/blob/master/Screenshots/SS0.png)

---

## Project Guide

### Step 1: Create an S3 Bucket and Upload Website Files in it

First, I navigated to S3, set my region as the one closest to my geographical location (ap-south-1) to minimize the latency (best practice), and created a new bucket named 'nextwork-three-tier-sumeet'.

Next, I uploaded my website files (index.html, script.jss, and style.css) into my bucket, as shown in the below screenshot.

![Image](https://github.com/sumeet15n/website-delivery-with-CloudFront/blob/master/Screenshots/SS1.png)

### Step 2: Set Up a CloudFront Distribution

I navigated to CloudFront and created a new CloudFront distribution as described below.

I selected my created S3 bucket under 'Origin domain' and entered 'nextwork-three-tier S3 bucket' as the name of my distribution, as shown in the below screenshot.

![Image](https://github.com/sumeet15n/website-delivery-with-CloudFront/blob/master/Screenshots/SS2.png)

Next, I selected 'Public' as the 'Origin access', opted out of WAF to avoid any charges, entered 'index.html' as my default root object, and created the distribution.

### Step 3: Verify the CloudFront Distribution

After creating the distribution, I attempted to verify it by visiting the URL provided under 'Distribution domain name' but encountered the "Access denied" error, as shown in the below screenshot.

![Image](https://github.com/sumeet15n/website-delivery-with-CloudFront/blob/master/Screenshots/SS3.png)

This is because S3 buckets and objects are private by default, so CloudFront could not access them as it did not have explicit permission.

### Step 4: Update the CloudFront settings

I navigated to the "Origins" tab of my CloudFront distribution, selected my S3 bucket listed therein, clicked on 'Edit'. Under the 'Origin access' section, I changed the selection from 'Public' to 'Origin access control settings', and I then created an OAC with the default settings.

### Step 5: Update the S3 Bucket Policy

After creating the OAC, a policy document was automatically created by AWS, as shown in the below screenshot.

![Image](https://github.com/sumeet15n/website-delivery-with-CloudFront/blob/master/Screenshots/SS4.png)

I copied the policy code and pasted it into the bucket policy of my S3 bucket.

Once my S3 bucket policy was updated, I refreshed my web page displaying an error and verified the error was resolved. I could then see my web page load successfully, as shown in the below screenshot.

![Image](https://github.com/sumeet15n/website-delivery-with-CloudFront/blob/master/Screenshots/SS5.png)

### Step 6: Delete Resources

Finally, I deleted all the created resources after completing this project to avoid any further charges on AWS.

---

## Project Reflection

This project took me approximately 1.5 hours to complete. The most challenging part was troubleshooting the access denied error, and the most rewarding part was to see the web page load successfully.

Big thanks to NextWork (https://www.nextwork.org/) for this project! I highly recommend this platform to anyone who wants to learn DevOps concepts and complete more projects like this one. Happy learning!