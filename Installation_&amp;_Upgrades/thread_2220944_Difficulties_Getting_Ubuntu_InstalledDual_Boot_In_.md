---
title: "Difficulties Getting Ubuntu Installed/Dual Boot In Windows 8."
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by feyisayo2 on 2014-04-30
So I saw ubuntu running on my friend's Acer laptop, and immediately I fell in love with the entire OS.  Immediately I decided to get my copy of ubuntu on ubuntu.com assuming the whole installation process would be as easy as I expected. Ironically, I've spent over 9hrs trying to get this done on my pc, I've swept through the entire google for a solution that might help me get past the installation process all to no avail.  

I use an HP Envy M6, I got the right 64-bit version of ubuntu for my processor, used one of the Live USB tools online to prepare my USB card, pendrive linux to be precise and then the mind games began. First it wasn't stated on the official ubuntu site that ubuntu required I turn of the "Secure Boot" feature for my laptop (UEFI), and also that Windows 8 doesn't feel too well sharing its space on my laptop with anyone.  

Here are things I've done: Disabled secure boot in my pc's bios, turn on Legacy or CSM mode in my PC's bios, disabled fastboot in Windows 8, Created a partition for Ubuntu on my Hard Drive ( just a pre-requisite I read somewhere online, as the Ubuntu partitioner doesn't really do as expected I read ). Tried a different LiveUsb Tool. 

Now, on attempting the steps above, everytime I restart my laptop to boot from my USB. I get just three options. 

1. OS Boot Manager.  
2.  Boot from EFI  
3. USB Disk Drive. 

Of course I'll be going for the USB drive option, but here's what happens, once I press Enter for that option, I get errors that the OS was unable to boot and the likes, even after disabling Windows-8's annoying features. 

I then decided to go through installing Ubuntu through windows by starting wubi.exe which still asked me to reboot my pc to start the installtion from a LiveCD. 

I've not been able to access anything like the Ubuntu installation Interface I see on the ubuntu site on my PC on startup. In Windows 8, I tried accessing advanced startup settings to boot from USB drive, but I get an error that "The drive failed, press OK to continue".  

There's nothing wrong with the drive, I have no idea why Windows 8 kept giving such errors at that point. 

I've just been frustrated, I would only go through this stress only for something I've fallen in love with.  I'll really appreciate anyone's help on this.  

PS: I've got an existing installation of Windows 8, I can't afford to lose.

---

### Post by Bucky Ball on 2014-04-30
*Thread moved to **Installation & Upgrades**.*

Welcome. You might have more luck here. You will DEFINITELY have more luck if you edit your post and add paragraphs. The 'big black blob' approach can put potential helpers off ... I tend not to bother reading them and know others do the same.

---

### Post by feyisayo2 on 2014-04-30
Hi, I'm sorry. I'm posting this from my phone's browser that won't let me create paragraphs as its the only machine with access to the internet with me right now.

---

### Post by Bucky Ball on 2014-04-30
I suspected as much so I've given you a hand. ;)

These might help:

oldfred's tips:
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

Managing Everything UEFI:
[http://www.rodsbooks.com/efi-bootloaders/index.html](http://www.rodsbooks.com/efi-bootloaders/index.html)

EFI Bootloader Installation:
[http://www.rodsbooks.com/efi-bootloaders/installation.html](http://www.rodsbooks.com/efi-bootloaders/installation.html)

A Quick Installation Guide:
[http://www.rodsbooks.com/linux-uefi/#preparing](http://www.rodsbooks.com/linux-uefi/#preparing)


These tips might also help:

From alug_Doc in post 2 here: [http://www.linux.org/threads/partition-tables.4895/](http://www.linux.org/threads/partition-tables.4895/)

Creating an EFI partition

If you are manually partitioning your disk in the Ubuntu installer, you need to make sure you have an EFI partition set up.

1. If your disk already contains an EFI partition (eg if your computer had Windows8 preinstalled), it can be used for Ubuntu too. Do not format it. It is strongly recommended to have only 1 EFI partition per disk.

2. An EFI partition can be created via a recent version of GParted (the Gparted version included in the 12.04 disk is OK), and must have the following attributes:

1. Mount point: /boot/efi (remark: no need to set this mount point when using the manual partitioning, the Ubuntu installer will detect it automatically)

2. Size: minimum 100Mib. 200MiB recommended.

3. Type: FAT32

4. Other: needs a "boot" flag.

----

The main points, really, are that you should:

* Switch off secureboot, faststart, and anything related to the Win8 side of things before proceeding;
* Check there is already an efi boot partition (there will be if Win8 is installed in EFI and is working fine).

Have you tried Unetbootin to create the installer? Another thing to remember is that the USB stick should be totally blank and formatted to fat32 prior to creating the installer. Best way to ensure this is to format it to fat32 prior to creating the installer! Reason is that whatever is on the stick to start with WON'T be removed; the usb creator just adds the files to what is already there ...

Good luck and don't give up yet! ;)

---

### Post by feyisayo2 on 2014-04-30
Thank you so much Bucky Ball, I already tried UnetBootin with all the right features enabled and disabled, but I'm not sure I'm getting the right options in my bios. Can I take a picture of my bios boot options menu so you understand better?

---

### Post by Bucky Ball on 2014-04-30
> **feyisayo2 said:**
> Can I take a picture of my bios boot options menu so you understand better?

Sure, but please attach any pics rather than putting them in the body of the post. You can do this by clicking the 'Adv. Reply' button and then the paperclip icon in the top toolbar there.

---

### Post by newbie2244 on 2014-04-30
Greetings-
I posted on this a while back. If you look up the posts for newbie 2244, one of them will tell you what to do. And, BTW, it took me several days.

newbie2244 
 HERE IS A COPY OF THE POST referred to above.  Sorry I just should have cut and pasted. You don't need to virtualise. 
_____________________________________________
 newbie2244 is online now  5 Cups of Ubuntu 
Join Date
Mar 2014
Beans
31
 Re: How to virtualise real Windows installed? 
 Greetings Ral -- I just did this yesterday - somehow. I have an HP Pavilion with Insyde? BIOS which came with WIndows 8. Be patient with my description because I don't fully understand this myself. ----- I made a bootable USB stick with Ubuntu Linux 12.04LTS. ___ In BIOS, I enabled virtualization first. Then in BIOS, I changed the boot order so that the USB drive was first. USB loaded and Linux finally loaded (a kind of temporary mount). But I couldn't install it to HD. I was connected to the net. I did a boot repair within the loaded Linux. And then ran the installer (universal installer). Still couldn't get an Ubuntu install on HD. Disabled secure boot. Same problem. Enabled Legacy Support. Ran the installer -- and finally got Ubuntu installed on the HD. Shutdown and started. Disconnected the USB stick and booted directly into Linux. OK but I needed dual boot. Went back to BIOS and changed boot order again so that the first boot device would be OS Boot Mgr. Shutdown (not restart). Started and got GRUB menu. --Very long listing. ---- NOW GET THIS ------ my default OS was now Ubuntu. In order to boot Windows, I had to select a file named Windows UEFI bkpbootmgfw.efi, about halfway down the menu listing. ANd now Windows is embedded in Ubuntu with 207 GB of disk space. 
Edit / Delete

---

### Post by feyisayo2 on 2014-04-30
But why do I get a "Boot Error" on boot from my USB drive. ?

---

### Post by Bucky Ball on 2014-04-30
How about trying from a DVD? We're jumping the gun trying to fix the other stuff at this point. You could be doing all that right, but we'll never know until you can boot the install media ...

---

### Post by feyisayo2 on 2014-04-30
But I don't have a dvd around. :( or does it matter that its a 2GB flash? 

Anyway, I've attached pictures of my bios.

1. My PC's BIOS boot menu

2. My PC's BIOS Settings 

3. The error I get when I decide to boot from the USB Hard Drive from the first picture

4. What happens when I press any key, until I power off my pc completely for a normal restart.


[ATTACH=CONFIG]252666[/ATTACH][ATTACH=CONFIG]252665[/ATTACH][ATTACH=CONFIG]252663[/ATTACH][ATTACH=CONFIG]252664[/ATTACH]

---

### Post by Bucky Ball on 2014-04-30
Ok, in the picture of your BIOS there try choosing 'USB diskette on Key/USB Hard disk' and see what happens.

You want to be booting it in UEFI mode as that is what you want to be installing it in. Win8 is installed in UEFI so Ubuntu should be too (not legacy, as suggested, as that can screw things up with Win8, as demonstrated). If the disk is set to boot in EFI in the BIOS, that is the way to boot the USB. If it's booting in EFI it won't see the USB if it is set to boot in legacy. Thus, no boot device.

---

### Post by feyisayo2 on 2014-04-30
I'm sorry for taking long to reply, I changed my bios settings from the legacy mode and changed the boot order for devices and my PC no longer detected my usb drive anymore. 

Here's a picture. 


[ATTACH=CONFIG]252671[/ATTACH]

---

