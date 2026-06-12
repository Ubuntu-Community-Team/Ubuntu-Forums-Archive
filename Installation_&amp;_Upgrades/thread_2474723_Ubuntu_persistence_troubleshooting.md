---
title: "Ubuntu persistence troubleshooting"
date: 2022-05-06
forum: Installation &amp; Upgrades
---

### Post by Nina_W on 2022-05-06
I set-up a USB to run Xubuntu in persistence mode, downloaded a few apps and then tried to boot again.

My PC running Ubuntu and the target PC running MS Windows 11 can't see it to boot from. I can see the through the file manager and can see the at least one of the applications I installed are there. 

Is there anything I can do to troubleshoot why it is not being seen by either PC to boot from? Or do I have to go through the whole process again and hope it works second time around?

Just to be clear I did boot from it once I'd created it in order to customize the desktop and add the apps, so something has gone wrong since then.

---

### Post by yancek on 2022-05-06
If you have a 'live' USB with or without persistence, it is much simpler to select it from the boot options in the BIOS firmware to boot it.  A default Windows install won't see or be able to read or write from a Linux filesystem.  About all it is aware of is in Disk Management.  You might try the 2 options at the link below.  I've not used them myself so can't verify.  The methods described are both for one time boot.  If you want it permanently, you will have to put the entry in grub.cfg.  If you do that and run update-grub, it will overwrite the entry.  
[URL="https://askubuntu.com/questions/1100858/how-to-boot-to-usb-from-grub2-when-the-bios-keep-booting-solely-to-grub-despite"]
[https://askubuntu.com/questions/1100858/how-to-boot-to-usb-from-grub2-when-the-bios-keep-booting-solely-to-grub-despite](https://askubuntu.com/questions/1100858/how-to-boot-to-usb-from-grub2-when-the-bios-keep-booting-solely-to-grub-despite)
[/URL]

---

### Post by Nina_W on 2022-05-06
> **yancek said:**
> If you have a 'live' USB with or without persistence, it is much simpler to select it from the boot options in the BIOS firmware to boot it.  A default Windows install won't see or be able to read or write from a Linux filesystem.  About all it is aware of is in Disk Management.  You might try the 2 options at the link below.  I've not used them myself so can't verify.  The methods described are both for one time boot.  If you want it permanently, you will have to put the entry in grub.cfg.  If you do that and run update-grub, it will overwrite the entry.  
[URL="https://askubuntu.com/questions/1100858/how-to-boot-to-usb-from-grub2-when-the-bios-keep-booting-solely-to-grub-despite"]
[/URL][https://askubuntu.com/questions/1100858/how-to-boot-to-usb-from-grub2-when-the-bios-keep-booting-solely-to-grub-despite](https://askubuntu.com/questions/1100858/how-to-boot-to-usb-from-grub2-when-the-bios-keep-booting-solely-to-grub-despite)


Sorry, I should have specified I normally boot Ubuntu from a boot memory which saw the USB and booted happily from it before I customized the desktop and installed applications. Now it just doesn't see it. Likewise on the MS OS I went into the boot menu, it saw it but failed to boot from it and went into MS OS.

---

### Post by sudodus on 2022-05-06
Persistent live drives are sensitive to corruption of the file system or of some file in the partition for persistence. If you intend to use a persistent live drive during a longer period, you had better **backup** the content of the partition for persistence or at least the personal files.

If you can still read the files you want to keep, please copy them to some other media, and after that remove all files and directories  in the partition for persistence. After that you can probably start again.

If that does not work, you can start all over and create a fresh persistent live system with [**mkusb**](https://help.ubuntu.com/community/mkusb).

[hr][/hr]
A more stable alternative is an installed system in a USB drive. It is more complicated to create, but it can be maintained like any other installed system. See the following links.

[How to Create a Full Install of Ubuntu 20.04 to USB Device Step by Step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

Remember to **backup** your data also from an installed system.

---

### Post by Nina_W on 2022-05-06
> **sudodus said:**
> Persistent live drives are sensitive to corruption of the file system or of some file in the partition for persistence. If you intend to use a persistent live drive during a longer period, you had better **backup** the content of the partition for persistence or at least the personal files.

If you can still read the files you want to keep, please copy them to some other media, and after that remove all files and directories  in the partition for persistence. After that you can probably start again.

If that does not work, you can start all over and create a fresh persistent live system with [**mkusb**]("https://help.ubuntu.com/community/mkusb").

[HR][/HR]
A more stable alternative is an installed system in a USB drive. It is more complicated to create, but it can be maintained like any other installed system. See the following links.

[How to Create a Full Install of Ubuntu 20.04 to USB Device Step by Step]("https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step")

[Installation/UEFI-and-BIOS]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS")

Remember to **backup** your data also from an installed system.

Many thanks, If I can't get it to work reliably then there is no point having it. I wanted it for my Mum so she had an easier operating system but she still needs MS OS for certain things and can't go for dual boot because of some system in the PC designed to speed it up (can't remember the details) but going for Dual Boot was going to really mess that up and might stop MS from working.

---

### Post by sudodus on 2022-05-06
Persistent live as well as installed systems in external drives are sensitive to corruption, if the drive is unplugged or otherwise switched off without proper shutdown or if a writable partition gets completely full. - Live-only systems are more robust, but cannot be modified. However, it is still possible to save files to some separate partition or drive.

So there are a few alternatives to consider before you decide what to give to your mother.

---

### Post by yancek on 2022-05-06
>  because of some system in the PC designed to speed it up 

Probably fastboot/hibernatioon which will prevent Ubuntu from accessing windows but should not have any effect on booting either. 

Is the computer UEFI or Legacy?  If it has windows 11 on a GPT drive, it is certainly UEFI and you could try the UEFI option explained at the link I posted above.  It is a one time boot and will not make any permanent change to either Ubuntu or windows.

Using mkusb suggested above or doing a fulll install to the USB might work better. .

---

### Post by bobunderwood99 on 2022-05-06
I wonder if OP is referring to Optane? Dual-boot might be feasible.

---

### Post by Nina_W on 2022-05-07
> **bobunderwood99 said:**
> I wonder if OP is referring to Optane? Dual-boot might be feasible.

No, I can't remember what it was called, but it was a 3 letter abbreviation, I think it had an R and an S but it was a while back I tried it and gave up. The message I got sort of said if I went ahead with dual boot it might stop MS Windows working properly.

---

### Post by Nina_W on 2022-05-07
The reason I wanted Xubuntu was specifically so I could custom the desktop. Whilst my Mum is very good with computers she is 80, as computers get more complex her ability to deal with complex is diminishing. Also, arthritis means fine motor control isn't good so she needs icons, menu bars, scroll bars etc. a decent size. I also want to put all the stuff she usually uses on the favourites list and have all her normal internet things on the browser toolbar.

So just having a one time boot will be no use. I'm going to try putting Xubuntu on an old PC she has which was playing up, see if having Ubuntu with no MS will get it working.

---

### Post by sudodus on 2022-05-07
Installing Xubuntu on an old PC is a good idea. If you have no internal drive, and install it into an SSD connected via a USB 3 adapter, (and avoid proprietary drivers), your Xubuntu will be fairly portable. In other words, it will probably work well also when connected to your mother's new Windows computer. See the links in [post #4](https://ubuntuforums.org/showthread.php?t=2474723&p=14094253#post14094253).

---

