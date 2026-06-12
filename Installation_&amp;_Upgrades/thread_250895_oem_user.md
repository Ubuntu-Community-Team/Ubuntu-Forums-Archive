---
title: "oem user"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by cetheriel on 2006-09-04
i just installe dubuntu, there is the oem user and i want to know what to do. should i create another user? is there anyway the default options for files are made read write execute for all files?

---

### Post by taurus on 2006-09-04
Sounds like you are using the alternate CD to install Dapper!!!  Log in as oem user (with the password that you create) and you need to run a command which I don't remember right now.  However, if you read the instructions when you installed it, it told you to run that command, something like oem-prepapre-configure or something close to that.  When you run that command, it will create a regular user with root privilage meaning you can use sudo.  Then, it will erase the oem account so no need to remove it by hand...

---

### Post by linear on 2006-09-04
OEM instructions are here: [https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

---

### Post by CesarBlue on 2006-09-05
I installed Ubuntu and after installation tried to remove the oem user with the command that the installation tells you to try but then after setting up the new user account with password ubuntu will not let me log on with it.It says incorrect user name or passowrd.As if the account does not exist at all.So then I try to use the oem account and that one does not work either.So now I can't log on with either account. Any suggestions?

---

### Post by taurus on 2006-09-05
> **CesarBlue said:**
> I installed Ubuntu and after installation tried to remove the oem user with the command that the installation tells you to try but then after setting up the new user account with password ubuntu will not let me log on with it.It says incorrect user name or passowrd.As if the account does not exist at all.So then I try to use the oem account and that one does not work either.So now I can't log on with either account. Any suggestions?
Boot your machine into recovery mode from GRUB.  Then at the prompt, check to make sure your login name is correct by

```
more /etc/passwd
```
Then, change the password to that account with

```
passwd john (assuming john is the login name of your account!!!)
```
Reboot and see if you can log in to john with the new password...

---

