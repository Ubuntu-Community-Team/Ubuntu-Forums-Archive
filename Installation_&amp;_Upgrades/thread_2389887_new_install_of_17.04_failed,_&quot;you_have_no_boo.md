---
title: "new install of 17.04 failed, &quot;you have no bootloader', SSD HD."
date: 2018-04-22
forum: Installation &amp; Upgrades
---

### Post by sonofsaturn on 2018-04-22
Hello

I put the latest version on a USB and tried to install it on a new HP SSD. The original hard drive freezes and hangs on startup, endlessly trying to scan for errors and go into 'recovery' mode. So I thought I would just grab a new hard drive and put a fresh copy on it, and make the old beast blazing fast. The hardware has always struggled with WinBloat anyway.

At the end of the install, the message "If you turn your computer off, it won't start again because you have no bootloader". After I found out that it was actually serious, and that my computer really will not start, I tried a few things and then came here.

 I have no idea if it copied onto the new HD. 
Details on the laptop:
[LIST]
[*]Asus G750JW 
[*]Nvidia geforce gtx 765m 
[*]core i7 
[*]originally ran Win 8 
[*]purchased in summer 2013 
[*]has a CD ROM if that helps 
[*]i still have the original C drive, it has lots of data and stuff i want 
[*]also have the original D drive 
[/LIST]

I used to be good at this stuff but I am overwhelmed and could use a hand. 

thanks

---

### Post by kerry_s on 2018-04-22
you mean 17.10 right. cause 17.04 has reached end of life & is not supported.

try installing again, sometimes it doesn't always get it right the first time.

---

### Post by yancek on 2018-04-23
If it originally came with windows 8, what does it have now?  Have you upgraded to windows 10 or do you not have windows installed?   If you have windows installed, is it UEFI or the older Legacy?   Do you still have the hard drive attached?.  Do you have Ubuntu or some other Linux system installed and have you ever installed Ubuntu/Linux?  Reason asking, are you familiar with Linux drive/partition naming conventions?  You mention C and D drives which is windows nomenclature that you will not see on Linux.  Which installation type option did you select?  Erase disk and install Ubuntu, Something Else?

The message you report is because you incorrectly installed the Grub bootloader or didn't install it at all.  How it is installed depends upon whether you are using UEFI or Legacy to boot the installation media and install.

---

### Post by sonofsaturn on 2018-04-23
If it originally came with windows 8, what does it have now? - Upgraded to 10

is it UEFI- I believe I can reach some kind of UEFI from the BIOS menu.

Do you still have the hard drive attached? I took out all but the new SSD, I have the originals but they are not installed.

Erase disk, and install.    I probably ****ed up the partitions somehow. 

I have this computer which is already running Ubuntu. I am getting away from windows, it has never run right on the gaming laptop.

---

### Post by sonofsaturn on 2018-04-23
UPDATE 
I found an old disc with Mint 15 on it. I will install that just to get a bootloader. At least I am not looking at a black screen with 'no operating system installed'. 

I should be able to put Ubuntu on after that right? This comp already has it as i mentioned. Would it make my life easier if they both run the same distro?

thanks!

---

