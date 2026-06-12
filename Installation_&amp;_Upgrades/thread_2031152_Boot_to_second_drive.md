---
title: "Boot to second drive"
date: 2012-07-21
forum: Installation &amp; Upgrades
---

### Post by skyradio on 2012-07-21
I have a PC with two disks.  I have Win 7 installed on the first disk.  Then I unplugged the disk and installed umbuntu on the second disk.  If I plug both in the system boots to Win 7.  If I unplug the first disk, the system boots to umbuntu.  If I have both plugged in and go to the bios and ask to boot from the second disk, the bios cannot find the operating system.  If I ask the bios to boot from the first disk Win 7 comes up fine.  

My Umbuntu partition on the second disk is /dev/sda1.  

How do I create a boot cd or usb that will boot to Umbuntu?

---

### Post by drs305 on 2012-07-21
You can alter the information on the sda so that even when it boots first you will get the Grub menu. Normally it would be preferred to leave the Windows bootloader on sda and have GRUB on sdb. That way if problems occur you can revert to the other bootloader by switching BIOS settings. 

However, since you are having problems with getting sdb to boot first, you can put GRUB on both drives. A note though - you will lose the Windows bootloader if you take this step.

This is normally not an issue, and if you need to get the Windows bootloader back it can be done from an Ubuntu OS. You should have a Windows option in the GRUB menu.

If you would like to code the sda MBR to boot GRUB, boot Ubuntu and then:
```
sudo grub-install /dev/sda
```
This should write to the sda MBR and GRUB should appear the next time you boot. Just make sure NOT to include the partition number in the command.

---

### Post by skyradio on 2012-07-21
The install command completed with out an error, but it didn't fix the problem.
 
I think part of the problem is I unplugged the first disk and then installed Umbuntu on the second disk. Cosnequently, the formatting process used sda for the second disk.  
 
I did the grub-install to /dev/sda.

---

### Post by drs305 on 2012-07-21
Since GRUB uses UUIDs to identify things the removable drive issue isn't always a problem.

Probably the best next step would be to install Boot Repair and click the Recommended Repair button. Link is in my signature line. 

If it can't fix it post the link to the info script file it creates.

---

