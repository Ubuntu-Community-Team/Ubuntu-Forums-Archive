---
title: "Installing Ubuntu on a netbook with a corrupted small Linux OS"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by epiclysteve on 2009-12-21
My netbook has had a mapping error and displays the message: 

fsck failed.  Please repair manually and reboot.  Please not that the root file system is currently mount read-only.  To remount it read-write:
#mount -n -o remount,rw /
CONTROL-D will exit this shell and REBOOT the system.
Give root password for maintenance (or type Control-D to continue):

I have no idea what the root password is, and i can't type anything in after the colon anyway.

So my friend suggested I try Ubuntu.  Since the netbook doesn't have a CD tray, I unpacked the iso download file onto a flash drive.  I tried changing the boot command sequence to run the flash drive first, but obviously Ubuntu OS isn't set up on that flash drive and I get and error message along the lines of "missing operating system." I understand why I would get that message, but I don't know how to fix it.

How can I essentially reboot the netbook with Ubuntu.  Is there some kind of reboot cd iso I can download and extract to a flash drive?

Thank you for your help.

---

### Post by snowpine on 2009-12-21
You can't just copy the .iso file to the thumb drive. Use Ubuntu's "USB Startup Creator" (maybe running the Ubuntu Live CD on another computer?) or [Unetbootin]("http://unetbootin.sourceforge.net").

A word of warning though: if your hard drive is toast, Ubuntu's not going to magically fix it. :)

I am not familiar with "small linux OS" otherwise maybe I could suggest how to fix the problem without reinstalling.

---

### Post by epiclysteve on 2009-12-21
I actually used winRAR to extract the iso file to the flashdrive.  But because I can't login to the SUSE Linux Enterprise Desktop system on the netbook, I can't run the application to install Ubuntu.

---

### Post by snowpine on 2009-12-21
> **epiclysteve said:**
> I actually used winRAR to extract the iso file to the flashdrive.  But because I can't login to the SUSE Linux Enterprise Desktop system on the netbook, I can't run the application to install Ubuntu.

I have no idea what winRAR is and don't see it mentioned anywhere in the Ubuntu installation instructions:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Follow the instructions in that link (or click the Unetbootin link in post #2) and you should be fine. :)

---

### Post by YosefKaro on 2009-12-21
Here you will find detailed instructions for making your USB ubuntu flashdrive from within Windows: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

-Yos

---

### Post by sanderj on 2009-12-21
This is how I installed Ubuntu on my netbook:

1) get a Ubuntu CD and boot it in a computer with a cd-drive (duh!)
2) put in a USB stick with at least 1GB free space.
3) choose System -> Administration -> USB Startup Disk Creator, and create a live-Ubuntu on the USB stick
4) after finishing that, put the USB stick in your netbook, and boot from it
5) after booting from the USB stick, choose "Install" on the desktop to install Ubuntu to your netbook

HTH

---

### Post by epiclysteve on 2009-12-21
I appreciate all the help guys. I've got everything figured out.

---

