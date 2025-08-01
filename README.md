![tkdev_space_200](https://github.com/user-attachments/assets/31af05be-97b5-4d4e-82ef-4f23203eb7ac)

<br>


# 🧪 Lab 1 - Azure VNet Demonstration

This lab will familiarize you with editing Terraform code, using the basic Terraform CLI commands, and lastly deploying resources.  

### Resources Created:
This demo creates the following resources:

- Resource Group
- Virtual Network (VNet)
- (2) Subnets
- Network Security Group (NSG)
- An NSG Policy allowing TCP 443 Inbound

<br>

# Lab Steps

### 1. Log into Azure and open Cloud Shell

![cloudshell](https://github.com/user-attachments/assets/a24f345c-e380-4f54-8a4b-f6b8463c023e)

- In the top right corner of the UI there is a terminal looking icon.

<br>


***

<br>

### 2. Launch a Bash Cloud Shell
- You will be asked if you want to launch a bash or power shell cloud shell. Choose bash for this example.
![image](https://github.com/user-attachments/assets/e03421ca-8057-4539-bfe8-c638d9473b3b)

***

<br>

### 3. Find your Azure Subscription ID
```az account show --query id --output tsv```
<br>
- This is showing you your Azure subscription ID, this is highly sensitive.
<br>

> **_Note:_** In a real world scenario we would want to pass this variable in a more secure way.

***

<br>

### 4. Save the Subscription ID as a variable

```sub_id=$(az account show --query id --output tsv)```
<br>
- We are setting a variable in bash with the output of the az account show command.

***

<br>

### 5. Pass the variable to Terraform

*Note the variable starts with TF_VAR. This is because if we name it TF_VAR, Terraform will pick it up at runtime as an environment variable*

<br>
```export TF_VAR_sub_id=$TF_VAR_sub_id```

***

<br>

### 6. Clone the GitHub Repo
```git clone https://github.com/tkerbe2/tkdev-azure-terraform-cli-demo```

***

<br>

### 7. Open the new directory
```cd tkdev-azure-terraform-cli-demo```

***

<br>

### 8. Check the TF files in the new directory
```ls```
<br>
![image](https://github.com/user-attachments/assets/2a2ef8b4-8e83-477d-af32-9c2eb841ec8a)

***

<br>

### 9. Edit the Terraform.tfvars file
```nano terraform.tfvars```
- Here you will change the name of the env variable to "prod" and change the org to something else
- Ctrl+O to write your changes
- Ctrl+X to exit nano
<br>

![image](https://github.com/user-attachments/assets/edeac33b-d69b-4d3d-9d70-79ebf7c39b0a)

***

<br>

### 10. Verify Terraform is installed
```terraform version```

<br>

- Your output should look like what is below:

<br>

```
Terraform v1.11.3
on linux_amd64
+ provider registry.terraform.io/hashicorp/azurerm v4.34.0

Your version of Terraform is out of date! The latest version
is 1.12.2. You can update by downloading from https://www.terraform.io/downloads.html
```

***

<br>

### 11. Initialize your new directory
```pwd```
<br>
```/home/taylor/tkdev-azure-terraform-cli-demo```
<br>
```terraform init```
<br>
- If you are successful you should see something similiar to the screenshot below:
![image](https://github.com/user-attachments/assets/adb4467b-d08b-4e25-88d0-66ca8205a45c)

***

<br>

### 12. Run a Terraform plan command
```terraform plan```
- A successful Terraform plan should have similar output at the bottom:

<br>

```Plan: 3 to add, 0 to change, 0 to destroy.```

***

<br>

### 13. Run a Terraform apply command
```terraform apply```
<br>

![image](https://github.com/user-attachments/assets/cf6cdd57-8c97-4c19-8572-37cbe58c66ee)

- Type yes and hit enter to proceed

*Additionally you can use the following option to skip the validation check:*

```terraform apply -auto-approve```

- A successful apply should yield the following output:\

<br>

```Apply complete! Resources: 3 added, 0 changed, 0 destroyed.```

***

<br>

### 14. Go verify your resources in Azure UI
![image](https://github.com/user-attachments/assets/949dc15b-d8d9-483b-b7ed-dae5815b2bb8)

- Check your newly created Resource Group.
- Check your NSG and look for the policy it created.
- Lastly check your VNet and subnets.

***

<br>

### 15. Destroy your resources and unset your variable

```terraform destroy```
<br>
- Terraform destroy will run a plan to destroy all resources and apply when confirmed.
<br>

```unset TF_VAR_sub_id```
<br>
- This will unset our variable

<br>

# ✨ Congratulations!

***

You've finished this lab and have completed the following items:
- ✅ Launched a bash Cloud Shell environment.
- ✅ Saved your Subscription ID to a variable and exported it for Terraform.
- ✅ Cloned the GitHub repo.
- ✅ Modified some Terraform variables in the terraform.tfvars file.
- ✅ Initialized your directory.
- ✅ Ran a Terraform plan and applied the changes.
- ✅ Verified your resources in the Azure UI.
- ✅ Ran a Terraform destroy and unset your variables

***

