---
title: "I am not able to install ubuntu using usb"
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by GGGamers on 2013-04-25
I have the issue that i want to install ubuntu using usb. but i try every method but i am not able to install ubuntu with usb. 
Before that i install window 7 , xp using usb. But i dont know why i cant able to install ubuntu. Please help me. Thanks

---

### Post by varunendra on 2013-04-26
Welcome to the forums GGG!

Please tell us which version of Ubuntu you are trying to install? 32 bit or 64 bit? And which method are you using to create the Live USB? Unetbootin seems to be successful for most.

---

### Post by GGGamers on 2013-04-26
> **varunendra said:**
> Welcome to the forums GGG!

Please tell us which version of Ubuntu you are trying to install? 32 bit or 64 bit? And which method are you using to create the Live USB? Unetbootin seems to be successful for most.

Version of ubuntu is 32 bit ubuntu-12.10-desktop-i386. I am creating ubuntu live usb. But it cant work. When i make live usb using unetbootin, Universal-USB-Installer-1.9.3.1, YUMI-0.0.9.3 and many more. But no use. I also change the boot setting in bios. It also dint work. I try kingstone and hp usb but i am not able to make live usb. I install window 7 using my usb it will boot and install but not able to install ubuntu. Help me. Thanks

---

### Post by varunendra on 2013-04-26
> **GGGamers said:**
> ....unetbootin, Universal-USB-Installer-1.9.3.1, YUMI-0.0.9.3 and many more......... I try kingstone and hp usb........ I install window 7 using my usb it will boot and install but not able to install ubuntu

Quite a variety there, with the source ISO being the only common factor I guess. So did you make sure the downloaded ISO itself is not broken? To check its integrity : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the computer has enough RAM (2GB or more), you may try the iso on a virtual machine to boot it.

If you happen to download the ISO again, I would recommend to download via [torrent]("http://www.ubuntu.com/download/alternative-downloads"). It is usually faster and integrity of the downloaded content is guaranteed.

Also, if your system supports 64 bit, go for the 64-bit version for better performance and to use full potential of your hardware.

---

### Post by GGGamers on 2013-04-26
> **varunendra said:**
> Quite a variety there, with the source ISO being the only common factor I guess. So did you make sure the downloaded ISO itself is not broken? To check its integrity : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the computer has enough RAM (2GB or more), you may try the iso on a virtual machine to boot it.

If you happen to download the ISO again, I would recommend to download via [torrent]("http://www.ubuntu.com/download/alternative-downloads"). It is usually faster and integrity of the downloaded content is guaranteed.

Also, if your system supports 64 bit, go for the 64-bit version for better performance and to use full potential of your hardware.

I have checked what you say, i found no error and the file was not broken...... Can u plz tell me the step by step procedure to make a live usb. May be i do some mistakes which i dont found.

---

### Post by varunendra on 2013-04-26
> **GGGamers said:**
> Can u plz tell me the step by step procedure to make a live usb.

For unetbootin :
[http://www.pendrivelinux.com/using-unetbootin-to-create-a-linux-usb-from-linux/](http://www.pendrivelinux.com/using-unetbootin-to-create-a-linux-usb-from-linux/)
[http://maitnoobsatwork.blogspot.in/2011/07/unetbootincreate-your-own-live-usb.html](http://maitnoobsatwork.blogspot.in/2011/07/unetbootincreate-your-own-live-usb.html)

If these can't help, please post the details of steps you are taking (description, file names, drive names, etc. that you are using.) Screenshots are always better.

Also, please tell me how much RAM you have and if you can create and run a virtual machine (using vmware or virtualbox). This can clear up many doubts.

---

### Post by GGGamers on 2013-04-28
> **varunendra said:**
> For unetbootin :
[http://www.pendrivelinux.com/using-unetbootin-to-create-a-linux-usb-from-linux/](http://www.pendrivelinux.com/using-unetbootin-to-create-a-linux-usb-from-linux/)
[http://maitnoobsatwork.blogspot.in/2011/07/unetbootincreate-your-own-live-usb.html](http://maitnoobsatwork.blogspot.in/2011/07/unetbootincreate-your-own-live-usb.html)

If these can't help, please post the details of steps you are taking (description, file names, drive names, etc. that you are using.) Screenshots are always better.

Also, please tell me how much RAM you have and if you can create and run a virtual machine (using vmware or virtualbox). This can clear up many doubts.

I have run ubuntu with vmware it wasa working fine and i create a live usb using the steps given above. I also attach some images. plz check.

[ATTACH=CONFIG]241902[/ATTACH][ATTACH=CONFIG]241903[/ATTACH]

---

### Post by varunendra on 2013-04-29
Hi,

Everything looks ok to me so far. However, you said in post #3 that you were trying Ubuntu 12.10, while the screenshot shows the label to be 13.0. Are you trying the latest 13.04 now?

Since you have already tried a number of different tools with two different pen drives, have you tried the drives on any other computers yet? You can even try them on VMware which although doesn't support booting from usb drives by default, but using '[Plop Boot manager]("http://www.plop.at/en/bootmanager/download.html") iso' it will.

A couple of more things to try -
[LIST=1]
[*]Format the drive as FAT16 instead of FAT32.
[*]Using gparted, make sure the partition has 'boot' flag after being created as Live. You can check it in vmware booted with the downloaded iso. You can also check this with **sudo fdisk -l** command. In fdisk output, the partition should have a star (*) in 'Boot' column.
[/LIST]

I personally have quite a variety of experience with bootable flash drives. Some computer's BIOS are just too picky to boot with certain drive+booting OS combination. For example, I recently handled a compaq laptop which didn't boot with the owner's pen drive with 12.04 live on it (it was iBall IIRC) while it did with my kingston. OS was same 12.04 on both pen drives, installed using same method. The same laptop booted fine with the same pen drive when made bootable with HBCD (which uses DOS as base).

Initially yours sounded like a similar case to me, but since you have already tried two different brands, now I think it is different. For testing with a different boot manager, you can try Slax which uses LILO as its boot manager and is very easy to install (just double-click a .bat file in windows, or run a .sh file in linux).

---

