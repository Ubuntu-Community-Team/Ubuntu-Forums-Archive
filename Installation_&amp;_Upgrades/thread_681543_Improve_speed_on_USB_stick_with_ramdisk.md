---
title: "Improve speed on USB stick with ramdisk"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by tisse on 2008-01-29
I managed to install Ubunut on a diskless PC using a 4GB USB stick, but it is very slow. It boots quite fast put when I try to do anything it is really slow. I guess it has something to do with that writing to an USB stick is really slow but reading from it is quite fast.

So my idea is to create a ramdisk during boot and copy almost everything (will keep at least /home on the stick though). This would speed up the performance I quess.. The computer I'm using has 1.5GB of RAM at the moment but if this is a possible solution I will upgrade the memory (its quite cheap nowadays). 

Does anyone have any experiences with this? Do anyone have any good links how to accomplish this? What parts of ubuntu should I put on the ramdisk?? /usr only or? Which parts should I keep on the USB stick except /home?

---

### Post by Jad on 2008-01-29
Personally never tried it but you can read about it here

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install/](http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install/)

---

### Post by tisse on 2008-01-29
Thanks for the links but I'm not sure that making a sort of live-cd on the USB stick solves my problem. As I said, I was able to install the complete ubuntu on an USB-stick and I don't know if it's going to get faster if I do it the way you recomend, or have I missed something???

After doing a bit more search I found "puppy linux" that I will try as well. What I found with puppy linux is that it loads everything into ram then all changes are written back to the usb-drive.

---

### Post by allenb on 2008-01-30
I am currently investigating the topic as well, and I have been using Puppy Linux as a guide.  It loads everything into ramdisk such that once the system loads, you can remove the USB drive.

From what I've been able to gather, it does this by modifying the initrd image used in the Linux boot process.  During a normal Linux boot, this image is loaded into a ramdrive where it is able to mount the system drives, do some basic setup, and then chain execution to the initialization code on the system drive.  Puppy Linux modifies the init scripts in the initrd image so that before they look for a system drive to boot to, they create a ramdisk, copy a filesystem image into it (they have it compressed with squashfs), and mount this image as the root drive.

I haven't been able to dig up any particulars as to just exactly how they go about doing all that, but that's the general overview I get from what I've read.  I have also read accounts of people using a ramdisk in addition to their normal system, and they store things like Firefox's cache on it in order to improve performance.  For things like browser caches that get read from and written to frequently, storing them in a ramdisk was reported to be noticeably faster than storing them normally on disk.

In case they're of any use, here are a couple of links I've found:
[http://www.puppylinux.com/flash-puppy.htm]("http://www.puppylinux.com/flash-puppy.htm")
[http://puppylinux.org/wikka/FlashPuppyDetails]("http://puppylinux.org/wikka/FlashPuppyDetails")
[http://www-128.ibm.com/developerworks/linux/library/l-initrd.html]("http://www-128.ibm.com/developerworks/linux/library/l-initrd.html")
[http://www.vanemery.com/Linux/Ramdisk/ramdisk.html]("http://www.vanemery.com/Linux/Ramdisk/ramdisk.html")

---

### Post by tisse on 2008-01-31
Thank you for the information and the links! That is exactly what I want for ubuntu. I run Ubuntu on all my other machines so I would like to have ubuntu on my diskless mediacenter as well. Will try to create something this weekend and see how hit goes.

I have read that puppy-linux stores changes to /etc and /home back to the usb-disk as well. Would be a nice feature.

---

### Post by allenb on 2008-01-31
> **tisse said:**
> I have read that puppy-linux stores changes to /etc and /home back to the usb-disk as well. Would be a nice feature.

IIRC it does this as an option on shutdown, not by default.  It prompts you for a flash drive, hard drive, or some writable medium to store the info on and creates an additional image file containing these directories (squashfs filesystems are read-only, I think Puppy uses gzip).

Duplicating this shouldn't be too hard (in theory).  On startup, create a second ramdisk (that's not read-only) and move into it the /etc and /home directories (and whatever else) from the main ramdisk.  Then, mount these folders onto their "old" locations on the main ramdisk.  When you shut down the system, you can dd / gzip this second ramdisk into an image file on whatever writable medium you have before you unmount it (or, just unmount it without saving it and you'll get a fresh clean system next boot).

Then, when the system starts up next time, it will check to see if a user-space disk image exists.  If so, it de-compresses the image and copies it into the second ramdisk.  If it doesn't exist, it moves the default versions of the folders into the second ramdisk as normal.  Then, it continues with mounting them as before, etc etc. (it might also be a good idea to prompt the user to use the saved session or start a new one).

That's what Puppy does from what I understand.  I have yet to find information from the people behind Puppy Linux about "here's how we did it" in a straightforward way.  I'm having to piece this together from various pages on the Puppy website and forums, so if someone knows of a better description of how they do it please let us know.

---

