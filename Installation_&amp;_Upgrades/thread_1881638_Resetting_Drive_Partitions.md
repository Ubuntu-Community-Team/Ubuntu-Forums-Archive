---
title: "Resetting Drive Partitions"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by Steve823 on 2011-11-15
I'm new to Linux/Ubuntu and like trying out different distros. I've tried the live CDs, but want to install with dual boot with Win7. My computer has a Dell and Diagnostic partition in addition to the NTFS main and the installed Linux partitions. My question is how do I completely remove a Linux distro returning to Win7 so I can do it all over again? I envision deleting the Linux partitions and then expanding the NTFS partitions to fill the space, but don't know how to return the boot loader to its original state. Is there an easy way to do all of this? My system is way too used to want to restore to its factory new state. I just want to restore it to the Win7 I had before I installed Ubuntu.
Thanks

---

### Post by raja.genupula on 2011-11-15
Hi man for Dual boot install no need to uninstall installed linux version.you said you had installed Ubuntu in the system .ok now you can install the windows and then look at my signature for boot repair , from there again you can restore your grub and then you can have dual boot system .
all the best.

byusing Gparted you can edit you partition sizes . 
for that look at this
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)


all the best man.

---

### Post by darkod on 2011-11-16
If you don't have a win7 dvd download the recovery cd here:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

You just boot with the cd and select Repair This Computer or similar. That should restore the windows bootloader to the MBR of the disk.

Note that after that you will no longer be able to enter ubuntu. Get out all the data you want first.

After that and when you see win7 is booting directly as before, simply enter Disk Management, delete all the linux partition you don't need (be careful to choose the correct ones), and create a new ntfs partition, or extend the current one.

---

### Post by Mark Phelps on 2011-11-16
You can also try using Boot-Repair (see link below).  I contacted the author and he confirmed that it can be used to rewrite a Win7 MBR:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by Steve823 on 2011-11-16
> **darkod said:**
> If you don't have a win7 dvd download the recovery cd here:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

You just boot with the cd and select Repair This Computer or similar. That should restore the windows bootloader to the MBR of the disk.

Note that after that you will no longer be able to enter ubuntu. Get out all the data you want first.

After that and when you see win7 is booting directly as before, simply enter Disk Management, delete all the linux partition you don't need (be careful to choose the correct ones), and create a new ntfs partition, or extend the current one.
Darko, this is the answer I was looking for. I had thought about that as I do have a Win7 installation disk, but wasn't sure if that would affect the boot loader or just the operating system. Thanks.

---

