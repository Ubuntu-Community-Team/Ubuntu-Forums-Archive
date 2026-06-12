---
title: "Windows 8 / Kubuntu Dual-Boot problem"
date: 2014-11-03
forum: Installation &amp; Upgrades
---

### Post by Bing_Wang on 2014-11-03
I am trying to install Kubuntu 14.04 on a Windows 8.1 machine (HP Pavilion 500-314). The installation was fine. After that, I rebooted the computer, then I got error message "Boot device not found" error. I tried to use boot-repair to fix it. No success. Here is URL

[http://paste.ubuntu.com/8807959/](http://paste.ubuntu.com/8807959/)

Thanks in advance!

Bing

---

### Post by yancek on 2014-11-03
Your boot repair output shows an EFI partition with the expected efi files for Kubuntu but nothing for windows.  Other than the efi partition, you have a swap partition and two Linux filesystems on two partitions and it looks like you installed Kubuntu on sda2 as well as sda4 as you can see from the content of the grub.cfg files for each partition.  Hope you have a windows 8 installation medium.  Which installation type option did you use?

---

### Post by Bing_Wang on 2014-11-03
I did install Kubuntu twice. The first one wasn't successful, I tried again. That's why I have two partitions for Linux. If I restart from windows 8, it will help?

---

### Post by oldfred on 2014-11-03
You do not have Windows. I hope that was your intent or that you made full backups before installing.

 Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but mulitiple drive installs must use Something Else. And fix is not in current versions.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

HP has modified UEFI to only boot Windows. So it will not boot the ubuntu entry in UEFI. 

Several work arounds:
      
 [URL="http://ubuntuforums.org/showthread.php?t=2234019"]http://ubuntuforums.org/showthread.php?t=2234019

      [/URL]
 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

    [URL="http://ubuntuforums.org/showthread.php?t=2234019"]
[/URL]
 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

[URL="http://ubuntuforums.org/showthread.php?t=2234019"]
[/URL]

---

