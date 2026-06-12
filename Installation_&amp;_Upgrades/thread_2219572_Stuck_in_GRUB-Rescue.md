---
title: "Stuck in GRUB-Rescue"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by Dennis_Bean on 2014-04-24
[TABLE]
[TR="bgcolor: transparent"]
[TD="class: votecell, bgcolor: transparent"][CENTER][COLOR=#777777]
[/COLOR][COLOR=#808185][/COLOR]
[/CENTER]
[/TD]
[TD="class: postcell, bgcolor: transparent"]I have 2 Hard drives installed in my computer. On one hard drive, I had Ubuntu 14.04 and the other was a Windows 7 HDD. Today I had to delete the Ubuntu HDD. I did this from my Win7 Partition manager. 

Now when I try to boot my computer from the Live usb, it sends me int GRUB Rescue mode. If I try to load my Win7 HDD, it sends me to GRUB Rescue mode. No matter where I set my boot device/partition, I land in GRUB Rescue. 

How can I get my Live USB to start, so that I can install GRUB and Ubuntu? Please go easy on me, I am very much still a noob when it comes to the world of Linux. I've only been dabbling for about 10 months now. 

Any help is very much appreciated. Thank you.


[/TD]
[/TR]
[/TABLE]

---

### Post by ubfan1 on 2014-04-24
Check your device boot order in the BIOS.  Is USB before the hard disk(s)?  If not, put it there.  Can you select which hard disk to boot from?  Were you booting from the Ubuntu disk or the Windows disk.  When you say disk, do you mean a physical disk, or a "disk" like "D:" which is really just a partition.

---

### Post by Dennis_Bean on 2014-04-24
Yes, I tried to boot the system by setting the USB to boot first. This does not work. I even changed the boot order of the 2 HDDs, so that the Win7 HDD should have booted but it sent me to GRUB-rescue.  No matter what I change, I end up in GRUB-rescue.

---

### Post by oldfred on 2014-04-24
Windows always installs its boot loader and a boot partition to the drive set as boot in BIOS. That ususually is sda. But if Windows was on a second drive, did you install Windows to that drive with only that drive connected or with BIOS set to boot that drive. Otherwise Windows may have had boot info on the Ubuntu drive.

Ubuntu always installs grub to sda, which is not always the first drive, but usually is. But if you ran Boot-Repair in auto mode before it installed grub to all hard drives.

Only if the flash drive is a valid boot device will the system boot from the USB. So if that is not booting double check that it is correct. When it is not bootable then system goes back to hard drive to boot and gives grub errors.

       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

    [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Dennis_Bean on 2014-04-24
The USB Drive is valid. I used it yesterday to install Ubuntu 14.04 and had no problems, except that afterwards, I had 2 ubuntu installs on the same HDD (this was the reason I erased ubuntu from Win7 partition manager, I could not réclame my other 135 or so GB, because SWAP was between them.)
My Win7 HDD was sdb2.  It's connected with an IEDE as slave to th DVD drive. My Ubuntu was sda, on my SATA HDD, along with GRUB. What is really annoying me is that I can't even start from the Win7 drive.  No matter how I set what in BIOS, I always get the GRUB-rescue screen.

---

### Post by oldfred on 2014-04-24
Did the Windows drive ever boot directly?
You may need to correctly set jumpers on older IDE drives to cable select and make sure you are using the newer 80 conductor IDE cable not a DVD or old 40 conductor cable.

If a real old system you may need jumpers set to master or slave. But then only master is bootable. I would then if motherboard has a SATA port then it supports cable select.

On my system USB flash drive boots as another hard drive choice not a USB choice.

---

### Post by Dennis_Bean on 2014-04-25
Yes, it did boot directly.  It used to be the only drive in the computer, though that was a while back.  

I'll have to look at the jumper settings again, even though I doubt thats the problem.  When everything was working, it always booted off of the sda (my SATA with Grub/Ubuntu) and that was fine because I had the choice of where to boot from, right from the start.

When I want my system to boot directly from USB, I have to set it to USB-HDD.  I can do this in BIOS or by pressing F12 and changing load order.

---

### Post by Dennis_Bean on 2014-04-26
Thanks for the help.  

I finally got everything working right with a little help from Unetbootin.  My Trusty Tahr is installed, updated and working like a champ.  Heck, even Windows 7 is working.  

Please mark this thread as closed.  Thanks again.

---

