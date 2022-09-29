# Creating a new vCenter server role with cumulative privileges and permissions to use with Veeam Backup & Replication V11

This PowerShell / PowerCLI script lets you create a new vCenter server role with all the cumulative privileges and permissions to use them with Veeam Backup & Replication V11.

The privileges used are based on the recommendations out of the Veeam Help Center which you can find here:
[Cumulative Permission for VMware vSphere - Veeam Help Center](https://helpcenter.veeam.com/docs/backup/permissions/cumulativepermissions.html?ver=110)

Simply execute the script and follow the steps to fill in the relevant data like your vCenter server name, the username and your password. The script will then ask you to choose a name for your new role and automatically creates it.

![Example execution of the script](https://github.com/falkobanaszak/vCenter-role-for-Veeam/blob/master/vCenter-role-for-Veeam-Output.png)

Feel free to give me feedback on this script, as I want to further improve it.

**Already planned improvements**
 - [ ] Add a function to assign a user to the role
 - [ ] Add a function to check against an existing role, print the missing privileges and let the user decide to apply the missing privileges to the already existing role
 
You can get the script here: [New_vCenterRole_Veeam.ps1](https://github.com/falkobanaszak/vCenter-role-for-Veeam/blob/master/New_vCenterRole_Veeam.ps1)

Successful tested against: 
- VMware vCenter 6.5
- VMware vCenter 6.7
- VMware vCenter 7.0
- Veeam Backup & Replication Version 10
- Veeam Backup & Replication Version 11

<br>

# PowerCLI Installation Guide

What is PowerCLI?
PowerCLI is a command-line interface for managing and automating all aspects of vSphere management, including networking, storage, VMs, guest OS, and more.
PowerCLI functions as a collection of PowerShell modules that contain more than 700 cmdlets (commands) to manage VMware infrastructure. 

**Prerequisite** 

## PowerShell

PowerShell is installed by default with Windows OS or Windows Server. 

Step1

## Install PowerCLI

**Online** 

You can install PowerCLI directly from the ![PowerShell Gallery](https://www.powershellgallery.com/). 


```powershell
#Execute the command below to install VMware PowerCLI
PS C:\> Install-Module -Name VMware.PowerCLI
```

**Offline** 

1. Download the .zip file with the latest released PowerCLI version from [here](https://developer.vmware.com/docs/15743/).

2. To retrieve the folder(s) on your machine that contain PowerShell modules, execute the following command

```powershell
PS C:\> $env:PSModulePath 
```

3. Extract the downloaded .zip file to one of the listed folders.

4. Unblock the copied files.

```powershell
PS C:\> cd path_to_powershell_modules_folder Get-ChildItem * -Recurse | Unblock-File
```


5. Verify if the PowerCLI module is available on your system.

```powershell
PS C:\> Get-Module -Name VMware.PowerCLI -ListAvailable
```
<br>

Step 2
## Explore Cmdlets
VMware PowerCLI consists of multiple modules that you can install and use according to your needs and environments. Usually modules correspond to a VMware product.

[VIEW CMDLET REFERENCES BY PRODUCT](https://developer.vmware.com/docs/powercli/latest/products)

<br>

# Update PowerCLI

Execute the following command to update PowerCLI. 
```powershell
PS C:\> Update-Module -Name VMware.PowerCLI
```
<br>
Note: You cannot update the PowerCLI module online if you have installed it by the offline method. In this case, perform an offline installation of the latest PowerCLI version. 