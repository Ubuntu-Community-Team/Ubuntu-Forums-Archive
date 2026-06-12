---
title: "After upgradation...Unable to mount Windows Partitions..."
date: 2016-05-10
forum: Installation &amp; Upgrades
---

### Post by visitnag on 2016-05-10
Hi 

I have upgraded my Windows10 32 bit to Windows10 64 bit and simultaneously reinstalled ubuntu 15.10 64bit version. After then
I am unable to mount windows partitions. Whenver I am trying to mount the windows partition it giving message as "Conecting to network"
and after some time ‘Failed to Retrieve Share List from Server’

Mine is desktop pc with dual booting. Not in a network.

Even after upgrading to 16.04 the problem  persists.

Please help.

---

### Post by Bucky Ball on 2016-05-11
Mount the Windows partition how? When you boot the machine, have you got the choice to boot either Windows or Ubuntu and you can boot either without problems?

---

### Post by visitnag on 2016-05-11
This is not booting problem. Grub gives both options and I can boot either of the two OSs. But when I am in Ubuntu 16.04 , i cannot mount the windows partitions.

---

### Post by Bucky Ball on 2016-05-11
> **Bucky Ball said:**
> Mount the Windows partition how?

How are you trying to mount the Windows partition and what error are you getting? You have ONE Windows partition, where Windows is installed. The others are probably NTFS storage partitions, so they are no 'Windows' partitions.

Just to confirm, you can't mount the Windows partition or any NTFS partition?

---

### Post by visitnag on 2016-05-11
Yes. They are NTFS partions. But earlier when it was 32bit i could mount the windows partitions in ubuntu. The problem started after upgrading both OS (ubuntu and windows10) to 64bit.
I could see the partions (volumes) on side bar of ubuntu but when I click they are not mounting.

the eror showing is "Failed to retrieve share list from server: No such file or directory", but my system is a personal computer and not connected to any network.

---

### Post by Bucky Ball on 2016-05-11
Could you post the output of this file inside code tags, please (see the green link in my signature):

```
nano /etc/fstab
```

Thanks.

---

### Post by visitnag on 2016-05-11
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=46da6dd6-c565-49a3-9cce-071da3fb4812 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda10 during installation
#UUID=d15bfe83-152f-420a-a965-20d47c6e2751 /boot           ext4    defaults        0       2
# /home was on /dev/sda8 during installation
UUID=c89c11f5-57f4-484d-9a7d-0621fb08c667 /home           ext4    defaults        0       2
# /usr2 was on /dev/sda12 during installation
#UUID=617bf3af-c085-4d94-9b1e-f3f0b4013bbd /usr2           ext4    defaults        0       2
# /var was on /dev/sda11 during installation
UUID=e177c0cd-8243-4e97-b550-224558807992 /var            ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=33293498-8751-4cb8-adae-c158dd750e57 none            swap    sw              0       0
UUID=d15bfe83-152f-420a-a965-20d47c6e2751	/boot	ext4	defaults	0	2
```

---

### Post by Bucky Ball on 2016-05-11
Thanks. I omitted to ask for the output of this as well.

```
sudo blkid
```

Thanks. (Between code tags, please!)

Also, you have the entry for /boot, sda10, hashed out in the main body of the file, but you've added the same entry at the end.? One or the other. Unhash the one in the body of the text and get rid of the 'orphan' entry you've added at the bottom.

---

### Post by visitnag on 2016-05-16
I have done it, but even then unable to mount windows partitions ....
The explorer window showing the partitions as "+ Other Locations" 
when I click on the link it is giving message on status bar as "Connecting to network.." and after some time
unable to connect.

Mine is PC not connected to any network. Please help!

---

### Post by Mark Phelps on 2016-05-17
You can't mount the Win10 filesystem partitions inside Linux because they are hibernated -- by default!  

Win10 uses a new form of hibernation known as FastStartup and this causes the partitions to remain mounted even when Windows is not running.  This will prevent Linux from then attempting to mount the partitions a second time.

There are two ways to disable FastStartup in Win8/10; (1) through the Control Panel, and (2) through an elevated command prompt.

Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup

Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F

In both cases, reboot Windows.

NOW, FastStartup is disabled.

Good Luck

---

### Post by visitnag on 2016-05-17
Thanks a bunch. It worked. I forgot this after upgrading windows 10 to 64bit.

---

