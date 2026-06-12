---
title: "Mbr"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by Blindguardian on 2010-02-23
I would like to duel multi operations system (Win XP Pro, Vista, and Ubuntu 9.10

A little insight on my set-up
I have each operating system on it own drive.
I use to have Ubuntu installed in side winblows xp pro then I un-installed it but now when I load into xp I have two options 1: Windows XP Pro 2: Ubuntu.
I can load into xp when I chose that option but not into Ubuntu

when I change the boot drive to the Ubuntu drive it loads into Ubuntu but no other options so I ran sudo update-grub.

Now when I load the drive that Ubuntu is on I have the options of loading the three operating systems I have installed.

The problem is that when I chose the xp operating system it will not load and I get an error but I can load into the other 2 (Ubuntu or Vista) when chosen.

I am thinking that if I restore the mbr of the windows xp drive then run the grub update from within Ubuntu that would fix the problem....so is there a way to restore the mbr of the windows xp pro operating system or is there a better way?

thanks for your help in this matter.

---

### Post by darkod on 2010-02-23
The mbr is fine, it doesn't get touched by wubi. The oly thing you need to do is boot XP and in C:\boot.ini delete the ubuntu line (it's a hidden file probably). That will get rid of the remained wubi-ubuntu entry that you already deinstalled.

After that try running sudo update-grub again in ubuntu to see if there is any change. Also if you were installing the OSs with all other drives disconnected ubuntu might not have a correct device.map so grub can find the disk properly.
That's why when installing ubuntu usually all drives need to be connected.

---

### Post by yogesh.girikumar on 2010-02-23
Hi,[INDENT]      > The problem is that when I chose the xp operating system it will not load and I get an error   [/INDENT]    Let me know what kind of error do you see exactly. It will help troubleshoot your issue better.[INDENT]      > I am thinking that if I restore the mbr of the windows xp drive then run the grub update from within Ubuntu that would fix the problem....so is there a way to restore the mbr of the windows xp pro operating system or is there a better way?   [/INDENT]    You can do that. But doing a grub update from within Ubuntu will override whatever you do with windows to manipulate the MBR. But it shouldn't give much trouble. If you have GRUB2 installed, ( comes installed by default with Karmic ) doing an update-grub should automatically detect all available operating systems and add it to the GRUB menu.


       Pls see: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[http://ubuntuforums.org/showthread.php?t=1397221](http://ubuntuforums.org/showthread.php?t=1397221)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Blindguardian on 2010-02-23
Ok here is the error that I am getting when I run the sudo update-grub:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Microsoft Windows XP Professional on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

I did edit the boot.ini for the win xp and now when I change to that drive it will boot straight into win xp and it still will not let me boot into win xp when I change drives and boot from the Ubuntu drive even though I do have that option.

---

### Post by darkod on 2010-02-23
If it complains about device.map first run:

sudo grub-mkdevicemap

then try

sudo update-grub

---

### Post by Blindguardian on 2010-02-23
> **darkod said:**
> If it complains about device.map first run:

sudo grub-mkdevicemap

then try

sudo update-grub

That did it! Now everything works great.

thanks darkod very much:D!! Problem solved.

---

