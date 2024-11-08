# Project on AWS S3 Service
# AWS S3 Static Website Hosting with Custom Error Pages

## Overview
This project is a static website hosted on Amazon S3. It includes HTML & CSS for a clean, interactive, and visually appealing user experience. This site demonstrates basic S3 hosting, file uploads, and downloads, with a setup for handling errors with an error page.

## Features
- **Responsive design** with HTML and CSS.
- Hosted as a **static website** on AWS S3.
- Supports **file upload and download**.
- Custom **error page** (`error.html`) for "file or page not found" errors, with a button to redirect to the home page (`index.html`).

## Prerequisites
- An **AWS account**.
- Basic knowledge of **S3 and permissions**.

## Installation & Setup

### 1. Create an S3 Bucket
- Go to the **S3 Management Console**.
- Click on **Create Bucket**.
- Enter a **unique bucket name**, select your preferred AWS region, and **disable "Block all public access."**
- Acknowledge public access by checking the acknowledgment box, and click on **Create Bucket**.

### 2. Enable Static Website Hosting
- Go to your bucket's **Properties** tab.
- Scroll to **Static Website Hosting** and enable it.
- Set the **Index document** to `index.html` and **Error document** to `error.html`.
- **Save** changes.

### 3. Set Bucket Permissions
- Navigate to the **Permissions** tab.
- In **Bucket Policy**, paste the following policy (replace `<YOUR_BUCKET_NAME>` with your actual bucket name):
    ```json
    {
      "Version": "2012-10-17",
      "Statement": [
        {
          "Sid": "PublicReadGetObject",
          "Effect": "Allow",
          "Principal": "*",
          "Action": "s3:GetObject",
          "Resource": "arn:aws:s3:::<YOUR_BUCKET_NAME>/*"
        }
      ]
    }
    ```
- Click **Save** to apply the policy and make the bucket publicly accessible.

### 4. Upload Files
- Go to the **Objects** tab of your bucket and click on **Upload**.
- Upload `index.html`, `error.html`, and any CSS for styling and interactivity.

## Usage
- Open the **static website URL** provided in the Static Website Hosting section of your S3 bucket properties to view the site.
- To test error handling, try accessing a non-existent file (e.g., `https://your-bucket-name.s3-website.region.amazonaws.com/nonexistent-page`) to see the `error.html` page.

## Configuration Notes
- **Default Encryption**: Enable server-side encryption for data protection.
- **Bucket Versioning**: Disable unless you need to keep multiple versions of objects.
- **Delete Policy**: Remember to empty the bucket before deleting it to avoid charges.

## _Screenshots_ 

### Home Page (index.html)
![Screenshot 2024-11-08 164335](https://github.com/user-attachments/assets/c960a956-d025-4399-9c1c-89247c9b91a9)

### Error Page (error.html)
![Screenshot 2024-11-08 164358](https://github.com/user-attachments/assets/2140464c-fcb2-44e1-92e2-495fdeb37d03)

### Files Interface on S3 
![image](https://github.com/user-attachments/assets/f0a8a2bc-6288-44c3-b4b8-c007db7206ac)

### S3 Bucket Overview
![image](https://github.com/user-attachments/assets/62cb1c0b-a972-4de0-aa7e-dd6f9bd7379c)

---

## Deleting Resources to Avoid Charges

To ensure there are no ongoing charges related to your S3 bucket, follow these steps to delete the bucket and its contents:

1. Empty the Bucket:
   - Go to the Objects tab within your S3 bucket.
   - Click on Empty bucket to delete all objects inside.
   - Confirm the deletion by typing “permanently delete” in the prompt.
   
2. Delete the Bucket:
   - After emptying the bucket, go to the Bucket Overview page.
   - Click on Delete bucket.
   - Confirm the deletion by typing the bucket name when prompted.
---
> *Note*: Ensure that you have saved any files or information you need before performing these steps, as this deletion process is irreversible.

By following these steps, you can prevent any unexpected AWS charges for unused resources. 

---

This completes the static website deployment guide on AWS S3, including setup, usage, and cleanup to avoid costs.



