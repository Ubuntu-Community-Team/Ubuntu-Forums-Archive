---
title: "upgradable ??"
date: 2020-11-17
forum: Installation &amp; Upgrades
---

### Post by helen314 on 2020-11-17
Please explain what is the point of "can be upgraded" and then getting the following message?


```

19 packages can be upgraded. Run 'apt list --upgradable' to see them.
f@f-SATA:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 linux-image-4.15.0-112-generic : Depends: linux-modules-4.15.0-112-generic but it is not going to be installed
E: Broken packages
f@f-SATA:~$
```

---

### Post by Frogs Hair on 2020-11-17
The output indicates broken or missing dependencies. Try the following and post any errors in code tags.  

```
sudo apt -f install 
```

---

### Post by helen314 on 2020-11-17
```

f@f-SATA:~$ sudo apt -f install
[sudo] password for f: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  grub-efi-amd64-bin shim
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-4.15.0-112-generic
0 upgraded, 0 newly installed, 1 to remove and 19 not upgraded.
2 not fully installed or removed.
After this operation, 8,223 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 245609 files and directories currently installed.)
Removing linux-image-4.15.0-112-generic (4.15.0-112.113~16.04.1) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.15.0-112-generic
/etc/kernel/postrm.d/zz-update-grub:
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) /usr/sbin/update-grub: line 1094: read: read error: 0: Bad file descriptor
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-4.15.0-112-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-4.15.0-112-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
f@f-SATA:~$ 



```

---

### Post by Frogs Hair on 2020-11-18
Are there any 3rd party repositories in use such as ppa's ? There are two packages not fully installed or removed.

```
sudo apt update --fix-missing
```

---

### Post by Impavidus on 2020-11-18
"19 packages can be upgraded" means nothing more or less than that a new version is available for 19 packages. That installing the upgrades fails is another matter. Linux is very modular. The tool that check for updates doesn't know in advance that the tool doing the actual installation will fail.

4.15.0-112 is a rather old kernel for 16.04 with HWE. It should already be at 4.15.0-123. About time it gets removed, but the error message is somewhat unexpected:```
Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N)
/usr/sbin/update-grub: line 1094: read: read error: 0: Bad file descriptor
```
I haven't seen a /boot/grub/menu.lst in ages. I though they were gone even before the days of Ubuntu 16.04. File descriptor 0 usually refers to stdin, which should be available for read, unless it was closed somehow.
I'd like to know what's in your update-grub script around line 1094:```
cat -n /usr/sbin/update-grub | head -n 1099 | tail -n 11
```Also have a look at the state of some packages:```
dpkg --list | grep -v '^ii \|^rc '
dpkg --list 'grub*'
```

---

### Post by helen314 on 2020-11-18
Thanks for replies. 
Here is result of the suggestion.

I am not aware of 3rd party repository. 

It is nice to know / confirm that some "stuff" in Linux is really not aware of other tools. 
So not to get too concerned in the future. 

linux-image-4.15.0-112-generic : Depends: linux-modules-4.15.0-112-generic **but it is not going to be installed**
So would it resolve the issue if I install ( how?)  it manually ?



```

f@f-SATA:~$ sudo apt update --fix-missing
[sudo] password for f: 
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Hit:4 http://security.ubuntu.com/ubuntu xenial-security InRelease              
Hit:5 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease    
Hit:6 http://ppa.launchpad.net/ubuntu-sdk-team/ppa/ubuntu xenial InRelease
Reading package lists... Done                     
Building dependency tree       
Reading state information... Done
19 packages can be upgraded. Run 'apt list --upgradable' to see them.
f@f-SATA:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 linux-image-4.15.0-112-generic : Depends: linux-modules-4.15.0-112-generic but it is not going to be installed
E: Broken packages
f@f-SATA:~$ 


```

---

### Post by Frogs Hair on 2020-11-18
Run the the commands posted by impavidus. The standard broken package commands may not apply here and it looks like you also have a ppa that hasn't been updated for 180 weeks.  [https://launchpad.net/~ubuntu-sdk-team/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-sdk-team/+archive/ubuntu/ppa)

---

### Post by oldfred on 2020-11-18
You uninstalled grub for UEFI boot.
And now it wants to create a menu.lst which is from grub legacy.
Grub legacy has not been used for about 10 years, but is still available in the repository as a package.

Did you install grub as a separate package?
The package name for grub legacy is grub
The package name for BIOS boot version of grub2 is grub-pc
And the package name for UEFI boot version of grub2 is grub-efi-amd64.
You should not install "grub", but install the correct version of grub2 for the way you boot BIOS or UEFI.

---

