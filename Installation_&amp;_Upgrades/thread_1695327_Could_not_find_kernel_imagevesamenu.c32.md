---
title: "Could not find kernel image:vesamenu.c32"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by spr1813244 on 2011-02-25
I'm continually getting this message. I'm just following the steps straight out of ubuntu.com, and I'm about 3.5 hours down so far...

I'm trying to create a bootable usb installer for the server edition. I've tried 10.10, and 10.04 to no avail, same message. I'm using the pendrivelinux program 1.8.3.1 as recommended, on windows 7, 4 GB Imation flash drive . Ticking the format option, all looks good till I try to boot it.....

and as a side note, how come it takes best part of an hour to "burn" to the usb?

---

### Post by mörgæs on 2011-02-26
Hi, welcome to the fora.

Have you tried Unetbootin?
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by spr1813244 on 2011-02-26
Thanks. Well that made UNetbootin has got further. Took only ten minutes to create boot drive, but still doesn't work.

I get into the installer, but can't get past where it tries to detect and mount cd-rom. States "No common CD-ROM drive was detected", not surprising since I don't have one, hence the whole ordeal.

I'm astonished how hard this is.

---

### Post by spr1813244 on 2011-02-26
Alright, found workaround for cd-rom mount problem at [http://www.revouser.com/forum/viewtopic.php?f=7&t=794](http://www.revouser.com/forum/viewtopic.php?f=7&t=794)

New problem now. Hangs at 45% during "Starting up the partitioner". Now what? I get the feeling I'm going to be on this forum a long time....

---

### Post by Rubi1200 on 2011-02-26
Stop what you are doing.

Start again and choose the option to try Ubuntu rather than installing.

At the live desktop, go to Applications > Accessories > Terminal.

Run this command and post the output back here (you can copy/paste from the terminal):

```
sudo parted -l
```

(lowercase L not 1)

---

### Post by spr1813244 on 2011-02-26
Not sure I can do that, the iso I'm using is ubuntu-1 0.10-server-i386.iso , there's no where I can select to just boot into ubuntu 

(I think I know what you mean, cause I made a CD for another PC with that option, a liveCD?)

There's one option screen at startup, but I can't do anything anyway. Supposed to be able to hit tab key for options, but keyboard seems to be dead at this stage (it's a usb keyboard if that makes a difference). However the options are all related to install's, and it's a text based menu system. No boot into OS.

I tried that sudo command when I'm mounting the iso as a work around, but evidently it's not the right place to try.

---

### Post by Rubi1200 on 2011-02-26
Sorry; wasn't paying enough attention to your original post :-(

Okay, the USB keyboard might cause problems; can you try another keyboard instead?

Did you check the integrity of the downloaded image?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

What are the specifications for the target machine?

---

### Post by pietrod21 on 2011-12-26
i have the same problem, anyone have the solution?!

---

### Post by boyshawn on 2012-01-17
Hi

I have also encounter this problem, and went to Google for a solution. 

It appears that there is a 'official' solution posted on pendrive linux at this [link]("http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/"). However, it does not explain the 3rd steps well. What does it mean by, "make sure that the paths to your kernel and initrd files are correct?" ? What is the correct paths to the kernel and initrd files anyway? 

An update (18 Jan): I try Unetbootin, and it work when the first menu appear, but after that. The Ubuntu loads for a while before my monitor went blackout with the CPU still running. It ends up the same when I select to try Ubuntu. 

Anyway, I will be back with a solution if I have solved the problem myself. :)

---

### Post by boyshawn on 2012-01-17
> **Rubi1200 said:**
> Sorry; wasn't paying enough attention to your original post :-(

Okay, the USB keyboard might cause problems; can you try another keyboard instead?

Did you check the integrity of the downloaded image?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

What are the specifications for the target machine?

Hi Are you continue to give guidance to us?

---

### Post by blake ryder on 2012-03-06
could not find kernel image : vesamenu.c32

Anybody out there....to solve this problem.......nothings work...!! { ](*,) }

thanks for help

---

### Post by mörgæs on 2012-03-07
We have no foundation for helping you based on this post. You need to take your time to write a thorough description of hard- and software including all the steps you have tried in order to diagnose the problem.

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by jjareds on 2012-03-09
I've got the same issue. I tried installing with a USB. After following directions given by Ubuntu, I plugged in my USB drive and booted my Thinkcenter. After going through the motherboards boot, and moving onto the OS, I got an error saying 
" boot:
Could not find kernel image:vesamenu.c32"
This error just repeats its self in the command line.

---

### Post by matt_symes on 2012-03-09
Hi

Take a look at this thread and post #11 in particular.

[https://answers.launchpad.net/ubuntu/+source/linux/+question/153014](https://answers.launchpad.net/ubuntu/+source/linux/+question/153014)

Have you tried unetbootin ?

Kind regards

---

### Post by jjareds on 2012-03-10
I think I've solved the problem. I re-downloaded Ubuntu, using the USB method provided by Ubuntu. This time though I used the 64bit where as the first time I used the 32bit. I shoud've checked before but the BIOS for the Thinkpad I have doesn't give all the information some other ones I used have. So just using the 64bit was the solution for me.

---

### Post by Buurman on 2012-03-17
I've used Universal-USB-Installer-1.8.8.8.exe to install Ubuntu (desktop) to an USB pendrive (4GB). This gave me the 'Could not find kernel image:vesamenu.c32'-error for images from ubu 10.04.4, 11.04, 11.10 and 12.04 (precise).

However, I noticed that there are both an 'isolinux' and 'syslinux'-directory on the USB pendrive, with varying contents.
Copying all files from one to the other (don't overwrite existing files) until both directories have the same content made the vesamenu-error go away on all occasions :).

(However 10.04 didn't use my hdmi-connected monitor, and 12.04 kernelpanicked, but that's another story).

---

### Post by mörgæs on 2012-03-18
Thanks for the tip.

As Matt suggested above, have you tried Unetbootin?

---

### Post by silverhairedJudy on 2012-03-23
OOps...starting to respond to wrong post...hmmm

---

### Post by silverhairedJudy on 2012-03-23
> **Buurman said:**
> I've used Universal-USB-Installer-1.8.8.8.exe to install Ubuntu (desktop) to an USB pendrive (4GB). This gave me the 'Could not find kernel image:vesamenu.c32'-error for images from ubu 10.04.4, 11.04, 11.10 and 12.04 (precise).

However, I noticed that there are both an 'isolinux' and 'syslinux'-directory on the USB pendrive, with varying contents.
Copying all files from one to the other (don't overwrite existing files) until both directories have the same content made the vesamenu-error go away on all occasions :).

(However 10.04 didn't use my hdmi-connected monitor, and 12.04 kernelpanicked, but that's another story).
THANK YOU for finding this!  I thought I was going to be another 3 hours just getting the USB to boot up before moving on to my original goal of using partimage!  Again, THANKS!

---

### Post by justawave on 2012-12-13
Some older BIOS's seem to have a problem reading FAT32 formatted USB sticks.

I  first formatted my USB stick using FAT16 and then installed the iso  without reformatting the stick. Gratefully I finally had success.

I got a lead from:

[http://www.blogphotovideo.com/software/could-not-find-kernel-image-boot-error-when-installing-linux-from-usb](http://www.blogphotovideo.com/software/could-not-find-kernel-image-boot-error-when-installing-linux-from-usb)

Hope this helps.

---

### Post by sbbaker on 2013-01-29
This solution worked for me too  ;)

> **Buurman said:**
> I've used Universal-USB-Installer-1.8.8.8.exe to install Ubuntu (desktop) to an USB pendrive (4GB). This gave me the 'Could not find kernel image:vesamenu.c32'-error for images from ubu 10.04.4, 11.04, 11.10 and 12.04 (precise).

However, I noticed that there are both an 'isolinux' and 'syslinux'-directory on the USB pendrive, with varying contents.
Copying all files from one to the other (don't overwrite existing files) until both directories have the same content made the vesamenu-error go away on all occasions :).

(However 10.04 didn't use my hdmi-connected monitor, and 12.04 kernelpanicked, but that's another story).

---

### Post by GlenH on 2013-05-11
The problem (and solution) turn out to be quite trivial, and are probably best fixed within the tools that create the bootable pen drives.  It appears that at some point, the system files moved from /syslinux to /isolinux, but pendrivelinux (at least) hasn't caught up to that fact.  The solution for pendrivelinux is to open /syslinux/syslinux.cfg and make the following changes:

Old:
include menu.cfg
default vesamenu.c32

New:
include /isolinux/menu.cfg
default /isolinux/vesamenu.c32

That's all there is to it.  You just have to specify the directory holding the files.

This was for a ubuntu-12.04.2-desktop-i386 USB installation created with Universal-USB-Installer-1.9.3.3.exe from pendrivelinux.com.  The filenames may vary for other distributions, but the process is similar.  Find the correct directory for the files referred to in syslinux.cfg and add full pathnames.

---

