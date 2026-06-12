---
title: "USB install problems"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by Flyer on 2008-06-09
Hi,
I have just done a full Ubuntu install to a 4 G USB stick from the Ubuntu iso. My problems are:
1. Ubuntu loads from the stick but refuses to accept my username or password " using incorrect case". I am sure I am not making a mistake (but you never know!) so I cant get in to Ubuntu.
2. I was not expecting Grub to be installed. I expected to boot to the USB stick via the bios. So now to boot into Windows XP I have to select it from Grub. This means I cannot boot into Windows without the USB stick being attached. Otherwise I get an "error 21"
 So my questions are:
1. How can I get around the password problem?
2. How can I remove Grub and boot into windows via the bios without the stick?
I am new to Linux so I am slightly panicking!
Thanks for any help.

---

### Post by issih on 2008-06-09
Ok, you are probably right, Ubuntu by default tends to install grub into the master boot record (mbr) of the internal drive.

You need to do 3 things to get what you want:

1) Replace the mbr of the internal hard drive with the original windows bootloader. To do this you can use either the windows xp install cd..(boot from it, go into recovery console and then type fixmbr) or download a supergrub disk, and use that instead.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

This will get you back to where you started, with a working windows install.

2) Install grub onto the mbr of the flash drive.. There are various ways to achieve this, I believe the supergrub disk can do it, or you can do it from within ubuntu booted from the live cd.

The simplest method however, is simply to reinstall ubuntu, just start again, this time however, on the last screen of configuration, before the install starts, hit the advanced button and configure it so that grub is installed to the flash drive rather than the internal hard disk.

3) set bios to try and boot from usb device first.

Having done that, you should boot into windows as normal, unless you insert the usb drive.

Most of all, don't panic yet, all should be fine :)

---

### Post by Flyer on 2008-06-09
Thanks Issih,
Panic subsiding a little. Will try your suggestions and let you know how I get on.

---

### Post by Flyer on 2008-06-09
Wheww!!! Dont have a Windows install cd so downloaded the supergrub disc. It worked. You have just made my day. Need a  drink now and will try a reinstall later. 
Many many thanks for your help.

---

### Post by issih on 2008-06-09
Excellent, I'm glad stage one went well, As long as you don't install ubuntu into the windows partition, most things can be recovered from with a bit of fiddling.

I hope the reinstall goes better, just remember to go into the advanced dialog at the last step :), let us know how it goes

---

