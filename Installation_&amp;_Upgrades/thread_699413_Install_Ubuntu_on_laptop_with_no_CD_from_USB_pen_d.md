---
title: "Install Ubuntu on laptop with no CD from USB pen drive."
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by moka on 2008-02-17
Hello all, im new here.

I have very basic knowledge of unix but am willing to learn. 

I have just started a UNIX unit at university and they require us to install UBUNTU on our PC's. The problem for me is that i want to install it on a Laptop with no CD drive. I am aware of two alternative methods, a network install and an internet install. I am also aware of running Ubuntu from a usb drive. I have quite a slow connection and already downloaded the ISO for ubuntu so i was wondering if i could install ubuntu from the USB drive? Surely this can be done?

Please can someone point me in the right direction to a noob friendly set of instructions? Or if you know yourself kindly tell me :)

Any advice i am grateful for.

Moka :popcorn:

---

### Post by jan quark on 2008-02-17
here a guide how to install ubuntu on a usb flash drive
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

and here how to install from a flash drive

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by moka on 2008-02-17
Can someone help me, i followed the instructions to install UBUNTU from a usb stick as follows...

Formatted USB Stick (FAT)
Downloaded syslinux-3.61.zip
extracted to C:\1\
Issued this command - C:\1\win32\syslinux.exe -s F:
Issued this command - xcopy /e /h /k e:\*.* f:
Moved all files from /isolinux to the root directory
Moved vmlinuz and initrd.gz from casper to the root dir
Removed the /casper/ or /install/ by using REPLACE /casper/ and REPLACE /install/ in notepad2 (i replaced them with "" (nothing)).
Renamed the isolinux.xfg to syslinux.cfg

I then pop the usb stick into my laptop, set the usb drive to boot first and receive the message 

"Invalid or damaged Bootable partition"

Please help me, the instructions were confusing enough i do not think i would be able to find out what i did wrong.

Additional Info

1GB USB STICK 
DELL D400 LAPTOP (with winxp-pro installed)

---

### Post by dstew on 2008-02-17
Where did you get those instructions? Is your USB drive formatted FAT16 or FAT32? If is is FAT32, can your computer boot a FAT32 USB drive? Some BIOSes will only boot FAT16 drives.

---

### Post by moka on 2008-02-18
Hello, thanks for your reply.

I got those instructions from the link jan-quark posted.

I actually cannot remember if chose fat32 or fat. I will try fat later on tonight.

---

### Post by moka on 2008-02-18
Ok, the drive was FAT, not FAT32. I tried it in my main PC and it come up with the same error.

Are there any programs out there that will make a USB stick bootable? Then i can just copy over ubuntu?

I also have a server in the house running windows, could i install ubuntu from that? If so how?

---

### Post by dstew on 2008-02-19
I am not too familiar with Windows, so if you want to make the USB stick bootable using the Windows instructions, I can only offer you generic advice. It seems to me that the logical place to begin is after the command```
C:\1\win32\syslinux.exe -s F:
```Check and see if the file **ldlinux.sys** is present in the root directory of the flash drive.

It seems easier to make the drive bootable (and runnable) under Linux using the isotostick script as in the documentation.

---

### Post by moka on 2008-02-19
I went ahead with a network install using unetbootin-ubuntu710rev113.exe.

It restarted my laptop and i choose unetbootin 
Went through the instructions
Started downloading files
Crashes (stopped on 6%)
Restarted
Dead laptop :(

Not a great start to my linux adventure. :(

---

### Post by Timn on 2008-02-19
Hi Moka,

I have been messing around with installing linux distros myself from thumb drives. To start out try following the steps you used before except run the syslinux command at the very end instead of in the middle. So the steps should look like this:

Formatted USB Stick (FAT)
Downloaded syslinux-3.61.zip
extracted to C:\1\
Issued this command - xcopy /e /h /k e:\*.* f:
Moved all files from /isolinux to the root directory
Moved vmlinuz and initrd.gz from casper to the root dir
Removed the /casper/ or /install/ by using REPLACE /casper/ and REPLACE /install/ in notepad2 (i replaced them with "" (nothing)).
Renamed the isolinux.xfg to syslinux.cfg
Issued this command - C:\1\win32\syslinux.exe -s F:

Let me know if this helps you. Don't let this discourage you from getting into Linux especially Ubuntu. The community is one of the best and will get this working for you.

Timn

---

### Post by solarwind on 2008-02-19
The two tutorials posted are old and don't work properly. I made a howto specifically to fix this.

[http://www.blog.solarwind.metafy.org/2008/02/17/setting-up-a-usb-stick-on-windows-to-act-like-an-ubuntu-installation-cd/](http://www.blog.solarwind.metafy.org/2008/02/17/setting-up-a-usb-stick-on-windows-to-act-like-an-ubuntu-installation-cd/)

Works. Guaranteed, I just installed it a few days ago. Enjoy! Tell me how it goes!

---

### Post by dstew on 2008-02-20
My last net install appeared to stall at about 6%, with "Please wait..." sitting there. So, after an hour or so, I aborted. Then I re-started the net install, but chose the Server (base install) instead. This went in fairly quickly. After that, I booted into the Ubuntu Server (which is text-mode only) and did```
sudo apt-get install ubuntu-desktop
```This installed the desktop, but gave continuous feedback that let me know it was progressing. It took about 1 and 1/2 hours over a DSL connection. After that, I entered ```
startx
```and I had my Ubuntu system running.

I think that during the net install, the installer is actually retrieving packages while is sits there and says "Please wait..." but maybe you have to wait a really long time. Anyway, doing the base install first, then ubuntu-desktop worked fine, and it was fun to watch the messages.
EDIT: I think you use the _generic_ kernel with the base-server install to get the desktop working. If you use the server kernel, you might have problems.

---

