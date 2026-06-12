---
title: "Zenbook UX31E Dual Boot/Restore Partition Backup"
date: 2014-01-16
forum: Installation &amp; Upgrades
---

### Post by Jacob_Gerlach on 2014-01-16
I'm currently running a 12.04 virtual machine inside windows 8 and decided to take the plunge and set my system to dual boot. I was a little reluctant to do this because of GRUB issues I had on an old laptop when I didn't have enough time to really fix the problem.


Until I tried to boot my liveUSB, I had never heard of UEFI...


I've read the guides [here]("https://help.ubuntu.com/community/UEFI") and [here]("http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported") to try to educate myself.


I'm hesitant to move forward because of the extra layer of complexity and the relative newness of dealing with these issues on Ubuntu.


I was able to boot a USB stick by following steps 1-3 [here]("https://help.ubuntu.com/community/UEFI"). I did have to disable SecureBoot (I got a GRUB menu with SecureBoot enabled, but selecting "Try Ubuntu" just gave me a black screen).


My biggest concern is preserving my ability to restore back to a factory Windows install if I have problems with my Ubuntu install. Since I have no restore disks, I'd like to back up my recovery partition (to external HD) before I install Ubuntu, but I'm not sure how to do that.


Looking at my disk with Compmgmt in windows shows the following:


```
Size        Status
300 MB    EFI System Partition
600 MB    Recovery Partition
103 GB    OS (C:) Boot, Page File, Crash Dump, Primary Partition
111 GB    Data (D:) Primary Partition
4 GB      OEM Partition
20 GB     Recovery Partition
```

My questions are:
Can anyone vouch for successfully setting up a dual boot on a UX31E?
How can I back up my restore partition? Why are there two partitions labeled restore? Do I need both? Will repartitioning for my Ubuntu install affect my ability to restore?
Is there anything else I need to be aware of or thinking about?

Thanks!


System Information
I have an Asus Zenbook UX31E. It came with Windows 8 preinstalled.
Running Confirm-SecureBootUEFI in Windows powershell retrns "True."
My computer uses the Aptio utility for managing UEFI settings.
(1) 256 GB SSD

---

### Post by Zhivargo on 2014-01-20
That looks very strange to me... 

I have Win8 on my first internal ssd and Ubuntu on my second internal ssd. 

partitions are like this in my windows drive
1. Recovery
2. C:

that is all i can see from linux....

---

### Post by oldfred on 2014-01-20
With UEFI you have all those partition.
One recover is really the Windows repair/recovery and the other is the vendor recovery.

Best to backup efi partition and your install. And make a Windows repair flash drive. 
Your links on UEFI install are the first two in my link in my signature. Review that also in case you have any of the other special configurations, Ultrabook, Intel SRT(RAID), dual video etec.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

Other Asus, may be similar?
      
 ASUS Zenbook Prime UX32VD
[http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1)
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)
 Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)

---

### Post by Jacob_Gerlach on 2014-01-24
Thanks for the replies guys. I assumed that I had email notifications set up and didn't realize anyone had responded to this thread.

I did some more searching and figured out how to create my windows recovery USB.

Went ahead with the Ubuntu install and everything happened as described on the community UEFI page (Windows wouldn't boot after install until I ran boot repair).

I did have to disable secureboot. I think that I correctly submitted a bug report against shim as the UEFI page asked.

Thanks again.

---

