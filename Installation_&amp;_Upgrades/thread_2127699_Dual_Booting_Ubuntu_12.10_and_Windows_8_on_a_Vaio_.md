---
title: "Dual Booting Ubuntu 12.10 and Windows 8 on a Vaio T13 - Great success!"
date: 2013-03-20
forum: Installation &amp; Upgrades
---

### Post by redmccarthy on 2013-03-20
Hello folks,

I have spent several days getting 12.10 and Windows 8 to happily dual boot on a Vaio T13 (SVT13124CXS) and I figured I might be able to help others do the same, since it seems like a lot of people are having trouble with it.

The installation process was actually painless... Getting the machine to boot the Ubuntu installer flash drive was the part that took forever. 

Before starting, I used the Windows partition manager to shrink the NTFS volume and made a FAT32 partition for Ubuntu and a 2GB FAT32 partition that I planned to use as swap. Keep in mind that the Vaio has a "Hybrid drive" which is marketing-speak for a 32GB SSD used as a cache for the regular 500GB disk.

Now for the fun part.

BIOS settings: Secure Boot disabled, boot mode set to UEFI (NOT legacy). You get into the settings by shutting the machine off and then holding down the "Assist" button for a few seconds. 

Attempting to temporarily select the USB drive to boot from resulted in massive failure and a wonderful "Unable to find a medium containing a live boot image" (paraphrasing here). I finally got the thing to work by setting the boot order to external first, then just letting it boot normally. But wait! It only worked when the USB disk was plugged into the blue port (the one that allows charging USB devices with the PC is off)

After the live Ubuntu was up and running, I used the manual partition settings in the installer to format the smaller FAT32 partition as swap and the larger as EXT4; everything went smoothly after that. Once the system rebooted into Ubuntu I used the boot repair tool to make Windows bootable again. Success!

While Ubuntu was working fine, I was feeling adventurous and it was bugging me that Windows was hogging the SSD even though the only reason I kept Windows was for this ExamSoft program I need for school (which will not work in Wine). Using GParted, I erased the SSD and created a 2GB swap partition and a 30GB EXT4 partition. I then rebooted into Windows expecting it to be broken, but it worked perfectly fine, as if the SSD had never existed. I created a large FAT32 partition on the regular hard disk to store my various media, then reinstalled Ubuntu on the SSD and repeated the boot repair after it was done. Both OSes are currently working fine. The multitouch trackpad, wifi, sound, touchscreen, and even sleep/hibernate work flawlessly in Ubuntu.

Anyway, sorry for the lengthy post, but I hope this might be helpful to someone trying to make a similar setup.

---

### Post by littlebobbytables on 2013-04-03
I am SO indebted to you right now - two weeks of frustration over! If you're ever in NYC I will buy you a beer. 

You just fixed: [http://askubuntu.com/questions/277611/initramfs-unable-to-find-a-medium-containing-a-live-file-system](http://askubuntu.com/questions/277611/initramfs-unable-to-find-a-medium-containing-a-live-file-system)

If you put it as an answer I'll click accept :)

---

### Post by aksacz on 2013-05-21
Hi there! Im trying to install Ubuntu but that wont work with me...i tried to change settings like you and many others options but i have only 2 ends - 1. no boot from USB - load W8 or 2. i start vaio with ASSIST key and start Boot from external device and then i get error "Operating system not found". I used LiLo for creating USB Ubuntu stick...thanks for help

---

### Post by jiaowg02078 on 2013-08-18
Sorry to ask, I also purchased a VAIO T13 notebook, Windows8 operating system pre-installed, I installed Ubuntu12.04 on the SSD, dual system can be started normally, but USB2.0 and touch screen does not work, Can you help me ?

---

