# bowtie-clone
Clone of Bowtie website for practice purpose

This project utilizes Git submodule for multi-module control.

<a href="https://medium.com/@data.dev.backyard/multimodule-projects-in-git-part1-handling-subprojects-using-git-submodule-ab57d60d5fbe/" target="_blank">
Multimodule Projects in Git Part1: Handling Subprojects Using Git Submodule
</a>

## Table of Contents

  - [Environment Setting](#environment-setting)
    - [Initial Git Clone](#initial-git-clone)

## Environment Setting <a name="environment-setting"/>

### Initial Git Clone <a name="initial-git-clone"/>

<a href="https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic/" target="_blank">
Creating a personal access token (classic)
</a>

```bash
# 1a. SSH - personal access token is not required
git clone git@github.com:samson-personal-organization/bowtie-clone.git

# or

# 1b. HTTPS
git clone https://samson-personal-organization:<personal-access-token>@github.com/samson-personal-organization/bowtie-clone.git
```

```bash
# to git pull update from submodules, cd into submodule folders and execute git pull simply would not work
git submodule update --init --recursive
```

```bash
npm install
# or
yarn install
```

### Git Operation

Create a new branch for submodule
```bash
cd bowtie-clone-frontend/
git checkout -b develop
cd ../

## run this command
git config -f .gitmodules submodule.bowtie-clone-frontend.branch develop
## or directly modify the .gitmodules at root folder
[submodule "bowtie-clone-frontend"]
	path = bowtie-clone-frontend
	url = https://github.com/samson-personal-organization/bowtie-clone-frontend.git
	branch = develop

## then sync it to .git/config
git submodule sync

git push --recurse-submodules=on-demand
```

## Sample Reference

[CDK CodePipeline build deploy stack source code](https://github.com/aws-samples/aws-cdk-examples/blob/master/typescript/codepipeline-build-deploy/lib/codepipeline-build-deploy-stack.ts)

[Yelb multi-services ECS CDK build deploy stack](https://github.com/mreferre/yelb/blob/master/deployments/platformdeployment/AWS/ECS/cdk/lib/yelb-ecs-stack.ts)

[Medium.com - Deploy Docker Container as serverless architecture to AWS Fargate](https://medium.com/thelorry-product-tech-data/deploy-docker-container-as-serverless-architecture-to-aws-fargate-1121bafa1d8c)

[Medium.com - End-to-End CD Pipeline: Amazon ECS Deployment using AWS CodePipeline](https://medium.com/thelorry-product-tech-data/end-to-end-cd-pipeline-amazon-ecs-deployment-using-aws-codepipeline-332b19ca2a9)

[Next.JS Dockerfile official sample](https://github.com/vercel/next.js/blob/canary/examples/with-docker-multi-env/docker/production/Dockerfile)