# Amazon ECS service quotas<a name="service-quotas"></a>

The following tables provide the default service quotas, also referred to as limits, for Amazon ECS for an AWS account\. For more information on the service quotas for other AWS services that you can use with Amazon ECS, such as Elastic Load Balancing and Auto Scaling, see [AWS service quotas](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html) in the *Amazon Web Services General Reference*\. For information on API throttling in the Amazon ECS API, see [Request throttling for the Amazon ECS API](https://docs.aws.amazon.com/AmazonECS/latest/APIReference/request-throttling.html)\.

## Amazon ECS service quotas<a name="service-quotas-ecs"></a>

The following are Amazon ECS service quotas\.

[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/service-quotas.html)

**Note**  
<a name="service-quotas-ecs-note-1"></a>Services configured to use Amazon ECS service discovery have a limit of 1,000 tasks per service\. This is due to the AWS Cloud Map service quota for the number of instances per service\. For more information, see [AWS Cloud Map service quotas](https://docs.aws.amazon.com/general/latest/gr/cloud_map.html) in the *Amazon Web Services General Reference*\.

**Note**  
<a name="service-quotas-ecs-note-2"></a>In practice, task launch rates are also dependent on other considerations such as container images to be downloaded and unpacked, health checks and other integrations enabled, such as registering tasks with a load balancer\. You will see variations in task launch rates compared with the quotas represented above based on the features that you have enabled for your Amazon ECS services\. For more information, see [speeding up Amazon ECS deployments](https://docs.aws.amazon.com/AmazonECS/latest/bestpracticesguide/deployment.html) in the Amazon ECS Best Practices Guide\.

## AWS Fargate service quotas<a name="service-quotas-fargate"></a>

The following are Amazon ECS on AWS Fargate service quotas\.

[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/service-quotas.html)

**Note**  
Fargate additionally enforces Amazon ECS tasks and Amazon EKS pods launch rate limits\. For more information, see [Fargate throttling limits](https://docs.aws.amazon.com/AmazonECS/latest/userguide/throttling.html)\.

## Managing your Amazon ECS and AWS Fargate service quotas in the AWS Management Console<a name="service-quotas-manage"></a>

Amazon ECS has integrated with Service Quotas, an AWS service that enables you to view and manage your quotas from a central location\. For more information, see [What Is Service Quotas?](https://docs.aws.amazon.com/servicequotas/latest/userguide/intro.html) in the *Service Quotas User Guide*\.

Service Quotas makes it easy to look up the value of your Amazon ECS service quotas\.

------
#### [ AWS Management Console ]

**To view Amazon ECS and Fargate service quotas using the AWS Management Console**

1. Open the Service Quotas console at [https://console\.aws\.amazon\.com/servicequotas/](https://console.aws.amazon.com/servicequotas/)\.

1. In the navigation pane, choose **AWS services**\.

1. From the **AWS services** list, search for and select **Amazon Elastic Container Service \(Amazon ECS\)** or **AWS Fargate**\.

   In the **Service quotas** list, you can see the service quota name, applied value \(if it is available\), AWS default quota, and whether the quota value is adjustable\.

1. To view additional information about a service quota, such as the description, choose the quota name\.

1. \(Optional\) To request a quota increase, select the quota that you want to increase, select **Request quota increase**, enter or select the required information, and select **Request**\.

To work more with service quotas using the AWS Management Console see the [Service Quotas User Guide](https://docs.aws.amazon.com/servicequotas/latest/userguide/intro.html)\. To request a quota increase, see [Requesting a quota increase](https://docs.aws.amazon.com/servicequotas/latest/userguide/request-quota-increase.html) in the *Service Quotas User Guide*\.

------
#### [ AWS CLI ]

**To view Amazon ECS and Fargate service quotas using the AWS CLI**  
Run the following command to view the default Amazon ECS quotas\.

```
aws service-quotas list-aws-default-service-quotas \
    --query 'Quotas[*].{Adjustable:Adjustable,Name:QuotaName,Value:Value,Code:QuotaCode}' \
    --service-code ecs \
    --output table
```

Run the following command to view the default Fargate quotas\.

```
aws service-quotas list-aws-default-service-quotas \
    --query 'Quotas[*].{Adjustable:Adjustable,Name:QuotaName,Value:Value,Code:QuotaCode}' \
    --service-code fargate \
    --output table
```

Run the following command to view your applied Fargate quotas\.

```
aws service-quotas list-service-quotas \
    --service-code fargate
```

**Note**  
Amazon ECS does not support applied quotas\.

To work more with service quotas using the AWS CLI, see the [Service Quotas AWS CLI Command Reference](https://docs.aws.amazon.com/cli/latest/reference/service-quotas/index.html#cli-aws-service-quotas)\. To request a quota increase, see the [https://docs.aws.amazon.com/cli/latest/reference/service-quotas/request-service-quota-increase.html](https://docs.aws.amazon.com/cli/latest/reference/service-quotas/request-service-quota-increase.html) command in the [AWS CLI Command Reference](https://docs.aws.amazon.com/cli/latest/reference/service-quotas/index.html#cli-aws-service-quotas)\.

------