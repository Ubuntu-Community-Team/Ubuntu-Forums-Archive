---
title: "second hard drive install &amp; boot loader"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by sonicrazy on 2007-09-19
I have a second hard drive that I use for Linux distributions. My first one has Vista x64, if it matters. After trying Fedora for a while, I wanted to go back to Ubuntu. However, the Grub boot loader conflicted and I had to go into the Windows Recovery Console to restore the original Windows boot loader. This time, I'm wondering if there is a way to have both Ubuntu and the Grub boot loader on the second drive without ever bothering the first drive and Vista. I experimented before in both Ubuntu and Fedora and had the Grub loader apparently installed on the second hard drive, but it still proved to end up actually being on the first, as I had to change the bios boot order to the first for the Grub loader to appear.

Documentation I originally read stated that if I changed the boot order in the bios to the second drive and installed Linux and a boot loader to it, I could at any time change the order to the first and it would act like Linux never existed. This wasn't the case in the experiment.

My other idea is entirely disconnecting the first hard drive during the install, but then I would have to go into the bios to change the boot order every time I decide to use a different OS. Maybe I could then edit the Grub file in Ubuntu, but then it's getting too complicated...

Thoughts?

---

### Post by Pumalite on 2007-09-19
All you have to do, if you are using the Live CD is: in step 7 click 'Advance' tab and change default (hd0) to (hd1) if you want grub in the second drive.

---

### Post by sonicrazy on 2007-09-19
It didn't work. I get the following errors when using Grub:

For Ubuntu: Error 17: Cannot mount selected partition

For Vista: Error 13: Invalid or unsupported executable format

The good news is that when switching the bios boot order back to the first hard drive, Grub didn't show up. So at least something worked out... any ideas on what's going on? I've been searching around Google but haven't turned up much yet.

---

### Post by confused57 on 2007-09-20
> **sonicrazy said:**
> It didn't work. I get the following errors when using Grub:

For Ubuntu: Error 17: Cannot mount selected partition

For Vista: Error 13: Invalid or unsupported executable format

The good news is that when switching the bios boot order back to the first hard drive, Grub didn't show up. So at least something worked out... any ideas on what's going on? I've been searching around Google but haven't turned up much yet.
Until Pumalite gets back, you can try highlighting your Ubuntu entry in your grub boot menu, press "e", highlight your line with root, press "e" again, then change root from (hd1,x) to (hd0,x), press "enter", then press "b" to boot...x means leave this value "as is"...this is temporary, but you can make it permanent.

Vista's entry would need to be root (hd0,x) and you'll need map commands to boot Vista on (hd1).

---

### Post by guzman87 on 2008-06-25
I did that just like you said but everytime i boot Ubuntu i have to change the order.  Do you know how to make it permanent so that the (hd0,x) stays the same everytime i boot linux

---

### Post by confused57 on 2008-06-26
> **guzman87 said:**
> I did that just like you said but everytime i boot Ubuntu i have to change the order.  Do you know how to make it permanent so that the (hd0,x) stays the same everytime i boot linux
To make it permanent, open a terminal(Applications---Accessories---Terminal), enter:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
copy & paste one line at a time, press "enter" after each line...you probably already know this, but won't hurt to mention.

Change the root values to what works for you and change the line with #groot to the same as root...quit & save.

---

