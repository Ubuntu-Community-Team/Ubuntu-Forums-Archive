---
title: "Remove GRUB, restore windows bootloader"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by Havingadump on 2010-01-15
Basically, I used a USB stick to run ubuntu 9.10 live, then tried to install to an external 500gb HDD connected with a Sharkoon Drivelink USB adaptor. The installation went fine, but I get a GRUB error 21 when booting a lot of the time. I figure this is due to the way in which the drive is connected. I am a complete noob, and I want to just remove GRUB completely and restore my Vista bootloader. Unfortunately, I do not have an installation disk as my laptop didn't come with one, and none of the others I have for other PC's are the same version (home premium 32-bit).

If you know of a way to fix the GRUB issue/s so I can use the external drive I would love to hear them too, but the main aim of this thread is to help me remove GRUB and restore the windows bootloader. If any more information is needed, just ask and I will provide it.

HP Touchsmart TX2-1010
Windows Vista Home Premium 32-bit
External HDD: Seagate Barracuda 7200.11 SATAII (with jumper set for 150mbps)

Thanks, Dave.

---

### Post by kansasnoob on 2010-01-15
Read "How to restore the Windows Vista or 7 bootloader" here:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

It includes a link to Neosmart's recovery disc:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Regarding getting grub2 to work so your external drive will boot when plugged in without changing the Windows mbr it would be best to have you boot your Live CD with all drives plugged in and post the results of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by Havingadump on 2010-01-15
Thanks for the links, I will go through the procedures tomorrow. I am going to shrink this NTFS partition and try again at some point.

---

### Post by Irwan on 2013-01-13
You can use the Bootrec.exe tool in the Windows Recovery Environment (Windows RE) to troubleshoot and repair the following items in Windows Vista or Windows 7:

To run the Bootrec.exe tool, you must start Windows RE. To do this, follow these steps:
Put the Windows Vista or Windows 7 installation disc in the disc drive, and then start the computer.
Press a key when you are prompted.
Select a language, a time, a currency, a keyboard or an input method, and then click Next.
Click Repair your computer.
Click the operating system that you want to repair, and then click Next.
In the System Recovery Options dialog box, click Command Prompt.
Type "Bootrec /fixmbr" and then press ENTER

---

