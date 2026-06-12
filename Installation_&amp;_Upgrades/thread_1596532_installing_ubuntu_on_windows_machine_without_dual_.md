---
title: "installing ubuntu on windows machine without dual booting"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by bgclevenger on 2010-10-14
greetings all. here's my situation:

i currently am running windos 7 (64 bit) and would also like to install ubuntu on a second hard drive. i understand a dual boot is easy enough to do, but i'd like to install ubuntu so that it and windows are completely isolated. rather than be prompted with a boot screen to choose os, i would do so by changing hd boot priority in bios. i'd like the end result to be 2 separte computers in one box. can it be set up this way, and if so, how?

many thanks,
bgclevenger

---

### Post by dino99 on 2010-10-14
to much useless noob hesitations :confused:

grub only find and list distro installed somewhere, nothing else.

---

### Post by lechien73 on 2010-10-14
Welcome to the forums, first of all :)

Yes, you can do what you propose. You need to set the installation so that Grub - the Linux boot loader - is installed to the Master Boot Record of your second hard drive, rather than the first.

If you want to be certain of absolute separation, then perhaps disconnect your Windows hard drive before beginning installation.

---

### Post by pricetech on 2010-10-14
Yes this will work.  Just make sure your BIOS is capable of letting you select a discreet device for booting.

and welcome to forums.

---

### Post by ak07 on 2010-10-14
I've done this and it has been working well until now - i've got another post on the problem i'm having if anyone can help.

Just install ubuntu on to your separate hard drive might be best to disconnect your windows drive while doing this.

Once you have completed the install and your ubuntu system is booting create a grub boot disk on floppy - goggle it loads of hits.

Then reattach your windows drive and set the boot order in your BIOS to point to floppy first then your windows hard drive second.

If the floppy disk is inserted ubuntu loads if not windows you can also replace a floppy with usb if you prefer.

It works for me but maybe better ways of achieving this

---

### Post by bgclevenger on 2010-10-14
thanks all for the wlcome, and for the responses that were helpful. remember, we were all noobs once. i also like the idea using a floppy/usb memory drive to boot into ubuntu without entering bios.

---

