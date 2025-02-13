Jenkins Build Logs to S3
========================

Overview
--------

This project provides a simple and efficient way to automate the storage of Jenkins build logs by uploading them directly to an AWS S3 bucket. By leveraging AWS CLI, we can streamline log management without relying on complex log aggregation tools like ELK. This solution is cost-effective and scalable for long-term log storage.

Why Use S3 for Log Storage?
---------------------------

-   **Cost-Effective**: Unlike ELK, which requires significant infrastructure and maintenance, S3 offers a pay-as-you-go model with minimal overhead.
-   **Scalability**: S3 can handle vast amounts of data without performance degradation.
-   **Durability & Availability**: AWS S3 provides high availability and redundancy, ensuring logs are safe and accessible anytime.
-   **Easy Retrieval**: Logs can be fetched using AWS CLI or SDKs as needed.

Prerequisites
-------------

-   Jenkins Server with access to build logs.
-   AWS CLI installed and configured with appropriate permissions.
-   S3 Bucket created to store logs.
-   Jenkins Job Logs Directory (e.g., `/var/lib/jenkins/jobs/<job_name>/builds/<build_number>/log`).

🔧 Installation
---------------

1.  Clone this repository:

    ```
    git clone https://github.com/your-repo/jenkins-logs-to-s3.git
    cd jenkins-logs-to-s3

    ```

2.  Ensure AWS CLI is installed:

    ```
    aws --version

    ```

    If AWS CLI is not installed, follow the installation guide: [AWS CLI Installation](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)

3.  Configure AWS credentials:

    ```
    aws configure

    ```

🚀 Usage
--------

1.  Modify the script with your S3 bucket name and Jenkins logs path.
2.  Run the script to upload today's build logs:

    ```
    ./upload_logs.sh

    ```

⏳ Automating with Cron
----------------------

To automate daily log uploads, add the following to your crontab:

```
0 0 * * * /path/to/upload_logs.sh >> /var/log/jenkins_log_upload.log 2>&1

```

🎯 Conclusion
-------------

By implementing this simple script, we ensure efficient log storage while keeping costs low. This approach eliminates the need for complex log aggregation systems like ELK, making log management seamless and scalable.
