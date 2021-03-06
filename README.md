# Slack Bot Lambda Function

[![Build Badge](https://img.shields.io/github/workflow/status/wsskorea-ict/slack-bot-lambda/CI)](https://github.com/wsskorea-ict/slack-bot-lambda/actions/workflows/main.yml)
[![Version Badge](https://img.shields.io/github/v/release/wsskorea-ict/slack-bot-lambda?include_prereleases)](https://github.com/wsskorea-ict/slack-bot-lambda/releases)
[![License Badge](https://img.shields.io/github/license/wsskorea-ict/slack-bot-lambda)](https://github.com/wsskorea-ict/slack-bot-lambda/blob/main/LICENSE)

## How to use?

### Using Docker

```shell
docker build -t <AWS ECR IMAGE URI>:tag .
aws ecr get-login-password --region ap-northeast-2 | docker login --username AWS --password-stdin <AWS ECR REGISTRY URI>
docker push <AWS ECR IMAGE URI>:tag
```

### Using SAM

```shell
sam build
sam deploy \
    --no-confirm-changeset \
    --no-fail-on-empty-changeset \
    --stack-name slack-bot-lambda \
    --parameter-overrides \
        LambdaFunctionExecutionRoleArn=<AWS_LAMBDA_FUNCTION_EXECUTION_ROLE_ARN> \
        SlackIncomingWebhookUrl=<SLACK_INCOMING_WEBHOOK_URL> \
        KmsKeyArn=<AWS_KMS_KEY_ARN> \
        SqsArn=<AWS_SQS_ARN> \
    --s3-bucket <AWS_S3_BUCKET> \
    --s3-prefix slack-bot-lambda \
    --tags Project=Mail
```

## License

MIT License

Copyright (c) 2022-2022 WorldSkills Korea Cloud Computing

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.