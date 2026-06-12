---
title: "Can't install Ubuntu 16.04"
date: 2016-05-22
forum: Installation &amp; Upgrades
---

### Post by feschli on 2016-05-22
Hey there 

I'm new to this forum ant fairly new to Linux as well, so be patient with me ):P

I'm trying to install Ubunut 16.04 but I keep ending up in a black screen...
I'm currently running Win10 on my pc but but I want to replace it with Ubuntu. So far, I copied the ISO on a 8GB thumb drive using the Rufus tool on Windows 10. Then I bootet the USB using UEFI, where I ended up in a black "Grub" where I could choose whether to Install Ubuntu or just try it. If I choose either one, I end up in a black screen. When I tried to boot from USB in non-UEFI mode, I ended up in the purple "Grub" and after selecting Try (or Install) Ubuntu, I ended up in a black screen with a single underline on the top left (wow, much progress^^).
Google told me to disable Secure Boot and to do the "nomodeset"-thingie, but none of those helped me so far.
My hardware: Intel 6600K, ASUS Z170-Deluxe, 8 Gigs RAM, Samsung 840 Pro 128GB, Palit Jetstream GTX 680 2GB. 

What should I try next?

Greetings :D

---

### Post by grahammechanical on 2016-05-22
The first thing to keep in mind is that if Windows 10 or Windows 8 came pre-installed on that machine then it would have been install in EFI mode and that means we need to install Ubuntu in EFI mode as well. Installing Ubuntu in non-uefi mode or BIOS/Legacy/CSM mode will give us problems with dual booting with Windows.

My advice is to run the live session using the nomodeset option and not to tick the box "Install third party software." Ticking that box will bring in some third party audio & visual codecs and also a proprietary video driver and it may be the proprietary video driver that is causing this problem.

If you get the same problem when re-starting at the end of the installation process, then at the boot menu select Advanced options for Ubuntu and in the sub-menu select the recovery mode kernel. At the recovery menu select Resume. That might get to a working desktop using a fall back open source video driver where you go to System Settings>Software & Updates>Additional Drivers tab and try different video drivers. Allow time for the utility to do its work.

According to Intel that CPU has integrated graphics (HD graphics 530). So, along with the GTX 680 you have hybrid graphics. You may need to set the machine to run on either Intel or Nvidia graphics. It could be that the live session is getting confused as to which graphic adapter is being used. I do not know. I do not have hybrid graphics.

[http://ark.intel.com/products/88191/Intel-Core-i5-6600K-Processor-6M-Cache-up-to-3_90-GHz](http://ark.intel.com/products/88191/Intel-Core-i5-6600K-Processor-6M-Cache-up-to-3_90-GHz)

Regards.

---

### Post by feschli on 2016-05-22
Hi and thanks.
My machine is custom built, so there was no Windows pre-installed. But can you tell me (or give me a link^^) how to install Ubuntu in EFI mode?

I can't run Ubuntu in live mode because the screen remains black after i "click" on "Try Ubuntu without installing". It doesn't matter whether or not I press "e" and add nomodeset after "quiet splash".
I tried the to remove the GTX 680 and plug my monitors directly into the mainboard and the result was the same as above.

---

### Post by RobGoss on 2016-05-22
Hello and welcome to the forum, I see a lot of people having this issue using **Rufus, **I'm sure if it's has anything to do with the black screen but it just surprising that what you just described is also happening in many other post.

If you only have access to Windows try [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) to create your **bootable USB** that's what I also use and it works great each and every time it's worth a shot, I would also download another ISO file just in case there's some issues with the one you are using.

---

### Post by feschli on 2016-05-22
Well, I have a Ubuntu/Win10 dualboot on my notebook. 
I'll give it a try with a new ISO and pendrivelinux. I'll report back later :)

edit: Should I use YUMI or Universal USB Installer?

---

### Post by RobGoss on 2016-05-22
> **feschli said:**
> Well, I have a Ubuntu/Win10 dualboot on my notebook. 
I'll give it a try with a new ISO and pendrivelinux. I'll report back later :)

edit: Should I use YUMI or Universal USB Installer?

I would use Universal USB Installer

---

### Post by feschli on 2016-05-27
Hey there, I solved the problem.
I disconnected all my Sata devices from the mainboard and after this, everything went smoothly. :D

Funny thing: After the installation, i connected my data drives and everything still works but as soon as I connect my optical disk drive, I can't boot anymore (the same blackscreen again). Anyone got an idea how I could solve this issue?

---

