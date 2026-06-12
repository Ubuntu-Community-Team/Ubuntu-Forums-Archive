---
title: "Installation ISO or USB images"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by SnappyU on 2008-04-28
Hi all,

Just wondering out loud here, the venerable ISO images that had been with us since time immemorable in pc history, giving us a simple and efficient means to grabbing installation images for linux distros.

With wide spread availability of cheap thumbdrives of greater capacity than 1gb, is it time for linux distros, in particular Ubuntu, to consider releasing one-click installations for USB thumbdrives?

Distros like puppy linux and DSL have such images, but ideally, such an "image" should actually be an app that you can simply use to install the distro onto a USB and use it to boot up as a Live-Thumb and/or install.  It should not require the user to grab files from multiple sources and have to do the thumbdrive preparation using thirdparty tools.

Step #1: Download USB install app
Step #2: Thumbdrive Preparation
Step #3: Installation

**#1 Download USB install app**
1.1 Download image (app)

**#2 Thumbdrive Preparation**
2.1 Format thumbdrive (TB)
2.2 Prepare TB with bootup files
2.3 Copy Ubuntu installation image/files over

**#3 Live-Thumb and/or Installation to machine**
3.1 Insert TB into pc (desktop or notebook)
3.2 Power up pc
3.3 Select boot from USB option
3.4 Select Live-Thumb or Direct Install

Note:
Wubi is as close to what I described as possible, but it requires that the ubuntu install is an upgrade onto an existing Windows machine.  If you have a blank machine and requires a fresh install of ubuntu with USB thumbdrive, then wubi would not work. :)

So guys, any thoughts or comments?

EDIT:

[http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install/](http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install/)
The above link demonstrates "how to install, boot and run Ubuntu 7.04 from a USB flash thumb drive using Windows, the Ubuntu Linux CD and a new custom FIXED initrd.gz to correct the persistent feature that was previously broken with the original 7.04 release."

[http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/](http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/)
Ubuntu 8.04 USB Live installation from Windows: This simple tutorial covers how to install, boot and then run Ubuntu 8.04 (Hardy Heron) from a USB flash drive.  

Again, an additional file is required.

EDIT:
On second thought, the above method seem to be a good enough compromise so that a standardized ISO is used instead of maintaining multiple images.  This is probably good for consistency and means that lesser resources is diverted to other areas.  Thoughts?

---

### Post by Payteer on 2008-05-01
Hello all,

I agree with above.  I have wiped all mention of an OS on my machine and would like to install from a USB very easily as I don't have a CD/DVD drive on the computer.  Can anyone help?

---

### Post by phr0ze on 2008-05-02
This link (mentioned above) is super easy but needs windows.

[http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/](http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/)

It is what I recommend to you since you have no CD drive.

---

### Post by SnappyU on 2009-04-11
Thanks for the replies.  Starting from Intrepid, a usb installation writer is available.

I'm using Jaunty beta right now and it is at System >> Admin >> USB Startup Disk Creator

---

### Post by sandy8925 on 2009-04-12
yeah there is a Ubuntu USB startup disk creator as snappyu mentioned. Easy to use too. I've used it and it works well. It requires an iso file to copy the image from (or you can also use the CD i think).

I would recommend using USB for booting the livecd and installing since it will be way faster than using the LiveCD. And easy to use. All I do is stick in the USB port of my laptop and start it up. And that's it.

---

### Post by SnappyU on 2009-12-12
*grin* ... I now swear by unetbootin. :D

---

