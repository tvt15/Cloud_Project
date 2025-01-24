## Hyperlocal Delivery Application Architecture on AWS
![alt text](https://github.com/tvt15/Cloud_Project/blob/main/Diagram.png)


The above diagram illustrates the cloud architecture for the application, designed to be deployed over the AWS cloud. In this architecture, the system is intended to handle multiple components, ensuring scalability, performance, and security. The primary users of the application are those accessing it via API requests routed through a secure and highly available AWS infrastructure.

The system operates across multiple availability zones (AZs) within a Virtual Private Cloud (VPC), ensuring fault tolerance and disaster recovery. User requests are routed via AWS Route 53, which provides DNS-based traffic management and ensures optimal routing based on geographical proximity and resource health. Traffic is further filtered using a Web Application Firewall (WAF) to protect against common web exploits.

Requests that pass through Route 53 are directed to an Application Load Balancer (ALB), responsible for application-level load balancing, ensuring efficient content-based routing. These requests are then processed by backend workloads hosted within an Elastic Kubernetes Service (EKS) cluster. The EKS cluster dynamically scales EC2 instances in response to workload demands, utilizing Auto Scaling policies to manage resource allocation effectively.

The application relies on Aurora RDS for relational data storage, complemented by Amazon DynamoDB and S3 for structured and unstructured data requirements. Caching services are provided by AWS ElastiCache (Redis), ensuring low-latency data access and high throughput. The architecture also integrates Kinesis for real-time data analytics and SQS for buffering asynchronous data processing.

For monitoring and observability, AWS CloudWatch is employed to track resource performance and trigger alerts based on predefined metrics. Cost and budgeting insights are provided through AWS Cost Explorer and Budget tools, allowing for proactive financial management.

From a security perspective, the architecture incorporates IAM for role-based access control, KMS for encryption key management, and AWS Shield for DDoS protection. Compliance and auditing are enforced via AWS CloudTrail.

To ensure business continuity, the architecture utilizes AWS Elastic Disaster Recovery (EDR), enabling failover to a secondary region in the event of primary region failure. The system is designed for resilience, with multiple redundancies in place to safeguard application availability and data integrity.