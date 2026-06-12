---
title: "Installed 22.04 and now HDD can't be found?"
date: 2023-03-08
forum: Installation &amp; Upgrades
---

### Post by rags260z on 2023-03-08
So I purchased an old HP laptop to try my hand with Ubuntu. A little background, the laptop, a HP 2560p, had Windows 10 on it when I received it with no passwords to get into it. It did boot to the login screen. So I tried installing 22.04 using a USB and thought everything was going fine as the install said it completed. That is until the reboot. Now it apparently can't find the HDD. I did try to reinstall and it asks if I want to reinstall or install alongside the previous install so the drive can be seen. Not sure where to go from here. I guess I should say when I did the initial install, I told it to erase the disk before installing.

Any suggestions for what to try next is greatly appreciated.

Joe

---

### Post by MAFoElffen on 2023-03-08
From a livecd, Use "Try", then open a terminal and post the results of this within CODE Tags:
```

sudo fdisk -l | grep '^/dev/' | grep -v 'snap\|loop'
lsblk -T -o NAME,SIZE,TYPE,FSTYPE,MOUNTPOINTS | grep -v 'loop'

```

---

### Post by rags260z on 2023-03-08
When trying to open Terminal I get an error that asks if it wants me to send it to Ubuntu. I'll keep trying to get Terminal to open and report back if I am successful. Thanks!

---

### Post by MAFoElffen on 2023-03-08
At the Desktop, select Activities > start typing in Terminal > select Terminal Icon...

---

### Post by rags260z on 2023-03-09
ubuntu@ubuntu:~$ sudo fdisk -l | grep '^/dev/' | grep -v 'snap\|loop'
/dev/sda1     2048       4095       2048    1M BIOS boot
/dev/sda2     4096    1054719    1050624  513M EFI System
/dev/sda3  1054720 1953523711 1952468992  931G Linux filesystem
/dev/sdc1  *     2048 247201791 247199744 117.9G  c W95 FAT32 (LBA)
ubuntu@ubuntu:~$ lsblk -T -o NAME,SIZE,TYPE,FSTYPE,MOUNTPOINTS | grep -v 'loop'
NAME     SIZE TYPE FSTYPE   MOUNTPOINTS
sda    931.5G disk          
&#9500;&#9472;sda1     1M part          
&#9500;&#9472;sda2   513M part vfat     
&#9492;&#9472;sda3   931G part ext4     
sdc    117.9G disk          
&#9492;&#9472;sdc1 117.9G part vfat     /media/ubuntu/UBUNTU 22_0
sr0     1024M rom           
ubuntu@ubuntu:~$

---

### Post by MAFoElffen on 2023-03-09
> **MAFoElffen said:**
> From a livecd, Use "Try", then open a terminal and [COLOR=#ff0000]post the results of this within CODE Tags[/COLOR]:


Please go back to your last post... Edit > Advanced > Select your output > Select the "#" Icon to wrap the output in CODE Tags > Save. 

sda is the internal disk and sdc is the USB LiveCD?

---

### Post by TheFu on 2023-03-09
Looks to me like the drive and 3 partitions are there and recognized.
HP can be flaky when it comes to their EFI implementation.  Whenever installing any Linux and having issues, the first step is to google for install instructions for the specific hardware/laptop and the specific OS release being used.

So, google for "HP ENVY 13-aq0044nr install ubuntu 22.04" if that's what you have and see what the results say need to tweak. I'm seeing a few workarounds with that query.  Seems a specific boot option was needed.

---

### Post by MAFoElffen on 2023-03-09
They mentioned using 
```

acpi=off

```
As a boot parameter option...

What is your secureboot and fastboot setting in BIOS. Both should be set to disabled... As well as the TPM in that model.

---

### Post by rags260z on 2023-03-09
Lol next issue is I can't get into the BIOS as it also has a password. I've reached out to the seller to see if I can get the password. Thanks for all of the help so far!

---

### Post by oldfred on 2023-03-09
Some of the HP only boot "Windows Boot Manager" as UEFI entry.
But they do not check on actual boot file, so we often have to create an UEFI entry that says Windows, but boots grub or shim.

New HP require user to go into UEFI settings and change boot order to Ubuntu entry to have it work.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

