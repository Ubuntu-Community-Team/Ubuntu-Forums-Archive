---
title: "Problem with install"
date: 2012-11-06
forum: Installation &amp; Upgrades
---

### Post by confuciousdragon on 2012-11-06
I've been trying to give my computer a dual boot with ubuntu 12.04 LTE 32 bit and Windows. However, I haven't been able to get the system installed. I've been waiting at the install screen for about 4 hours now, and it is still running without any progress being made. I am attempting to install via flash drive (I've already tried CD, and had it stop at the same place - the cd and the flash drive are not the same download).

The two messages that keep repeating are: 
[Time Stamp] ubuntu kernel: [number.number] Buffer I/o error on device sdb1, logical block 24418200?
and
[Time Stamp] ubuntu kernel: [number.number] usb 1-5: reset high-speed USB device number 12 using ehci_hcd

If I stop this installation and it is not able to continue, I know that my computer will be unable to boot Windows, as this is exactly what happened last time. I really don't want to have to reinstall windows yet again -_-

What can I do to either fix this, or prevent it from damaging the bootsector on my HDD

---

### Post by techvish81 on 2012-11-06
what error message you got while installing through cd?

---

### Post by Immolatus on 2012-11-06
maybe try unplugging all non-essential usb devices? some times the odd mouse will cause udev to hang on install. sometimes the kernel can resolve the device after the install gets moving. This happened to me once on a laptop that i had a desktop mouse plugged into. 

what is the hardware? PC or laptop? brand?

---

### Post by uclugLee on 2012-11-07
I had a very similar issue when trying to install via USB drive.  I ended up having to download the image a few times as I apparently ended up with a corrupt download.

---

### Post by mastablasta on 2012-11-07
you need to check the image after download to make sure it's a good one. if oyu use linuxliveUSB  this should be done automaticly. also if oyu donwload via torrent this will be done during download. otherwise here is how you do it manually:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
> **confuciousdragon said:**
> If I stop this installation and it is not able to continue, I know that my computer will be unable to boot Windows, as this is exactly what happened last time. I really don't want to have to reinstall windows yet again -_-
 
 
reinstalling the whole windows is not necessasy. it is enough to restore windows boot manager to master boot record. here is how you do it: 
 
win7 -  
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
 
winxp - [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)
boto into Recovery console and do *fixmbr* command.

---

### Post by Kevin McCready on 2012-11-07
I had a problem with a USB install. When I selected the option for "update over the net with the latest software as the install proceeded" or words to that effect, it worked.

---

### Post by confuciousdragon on 2013-02-09
Forgive the belated reply, but the hardware I'm using is a self-built PC. I have a lot of peripherals plugged in - 2 monitors, webcam, wireless headset, keyboard, mouse, controller, and an external hard drive. I wouldn't be surprised if this is what caused the issue. I shall try to reinstall soon (have some projects that I need to work on over the weekend that I can't risk losing). Thanks for all the advice. 

To respond about the error messages, the error messages I listed in my original post are the only messages displayed. The screen just blacks out before it repeats those error messages I listed. There is no previous warning that it will happen.

My Flash Drive is confirmed to work by LinuxLive. I redownloaded the install 4 or 5 times already as that was my immediate thought after it failed. I also discovered that if I perform the shortcut to safe restart ubuntu I can preserve the boot drive on my windows. At least that worked the last time I did it. Thanks for the advice on how to repair my boot sector, though. It makes me less weary of attempting the install again.

---

### Post by techvish81 on 2013-02-09
it could be a bad hdd too, do you have any i/o problems in windows?

---

### Post by confuciousdragon on 2013-02-11
Unplugging excess USB peripherals did indeed fix the situation. I'm finally using Ubuntu :D

---

