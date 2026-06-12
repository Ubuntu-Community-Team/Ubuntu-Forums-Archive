---
title: "problem with Grub boot loader"
date: 2014-07-27
forum: Installation &amp; Upgrades
---

### Post by babakflame on 2014-07-27
Dear Fellows

  I had both windows 7 and ubuntu 11.10 in my system working properly. Some days ago, I re-installed windows 7. Afterwrds, it seems that windows has replaced its own boot loader instead of Grub. Accordingly, the system automatically log into windows and I have lost my access to my ubuntu 11.10 drive.

I have read this link:  
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

  According to the abovementioned link, I made a boot-repair 64 bit disk which is a Disc Image File. However, the strange thing is this CD still cannot load the ubuntu environment so that I can repair the grub. Even Imade a live USB via liliUSB. Despite, the problem still exists.

  Would some body PLZ hint me how can I solve this problem and bring back my lovely ubuntu? :p:p

   Best,
       Bobi

---

### Post by coffeecat on 2014-07-27
> **babakflame said:**
>   According to the abovementioned link, I made a boot-repair 64 bit disk which is a Disc Image File. However, the strange thing is this CD still cannot load the ubuntu environment so that I can repair the grub. Even Imade a live USB via liliUSB. Despite, the problem still exists.

How did you burn the ISO to disk? If you have a single file on the disk called boot-repair-disk-64bit.iso, then you didn't burn it correctly. You need to "burn as image", although the wording varies slightly depending on the software you use. Which burning software did you use, and in which OS?

lilUSB should have created a bootable USB, so what happens when you try to boot from it?

By the way, your Ubuntu 11.10 is long past end of life and unsupported. You need to be running a currently supported version of Ubuntu, such as 12.04 or 14.04. If you have all your personal files backed up, it might be quicker to simply re-install with 14.04 over your 11.10 installation, which would solve your dual-boot grub problem. If you do so with the 14.04 installation medium, I suggest you take care because some people are reporting that they have lost Windows. Whether this is a bug or user error, I don't know.

---

### Post by babakflame on 2014-07-27
Dear cofeecat


   Yes, You are right. I had a single file on the disk called boot-repair-disk-64bit.iso . I have used NERO software in windows 7 operating system for burning the disk. I am going to burn it as image according to your hint.

  with liliUSB, everything seems correct I mean the lights of software were green and I did exactly as the hints from the links in help.ubuntu site, however, after modifying the system to boot from external device, still nothing happens and the system again automatically log into windows.

   Best,

     Bobi

---

### Post by coffeecat on 2014-07-27
You need to repair grub in the internal drive, not set it to boot from an external device.

If you manage to repair grub with a correctly burnt CD, then you need to upgrade your 11.10 system or re-install. 11.10 is unsupported.

[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

---

### Post by babakflame on 2014-07-27
Dear coffeecat 

  many thanks for your hint on how to burn an image CD of boot-Repair-Disk. I solved my problem. Just a short question about installing the .iso on live usb:

   I did exactly according to the following lines from the link:  [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[PHP]Download and use Linux Live Usb Creator. 
Once you have usb-creator.exe,  run it and follow the same steps as described for Linux (point it at  your .iso file or your Ubuntu CD-ROM, point it at your USB flash drive,  make sure you have the right device selected, then "Make Startup Disk").  
Note 
You  won't be able to select the USB flash drive if it wasn't formatted in a  way that Windows can see it.  You may have to format it using Windows  Explorer in order for it to show up in a creator tool.[/PHP]

 Then I changed my system to boot from external drive, since I think usb flash drive accounts as an external drive. My system is VAIO VPCEA26FG. 


  However, after rebooting nothing happened and the system automatically log into windows. Can you hint me what was my mistake in that case?

 From your earlier post, I infer this point that with using live usb, I should still boot the system from Internal Hard Disk Drive. Am I correct?

  Again many thanks for your earlier hint.

  Best,

   Bobi

---

