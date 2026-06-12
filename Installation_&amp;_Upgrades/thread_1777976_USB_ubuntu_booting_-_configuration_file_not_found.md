---
title: "USB ubuntu booting - configuration file not found"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by Nalfeind on 2011-06-08
Hi,
I'm having a problem booting ubuntu 10.04/11.04/11.10 (32&64) on my computer.

When I boot I get an error like :
>SYSLINUX   ...   H. Peter Anvin
>Configuration file not found
>boot: 

Then anything I try on the boot: line give me the error :
>Could not fin the kernel image ...
>boot:

I tryed remaking my USB several times with different versions of ubuntu between 10.04 and 11.10 and in 32 and 64 bit. I followed the instructions here [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I also followed the instruction here [http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/](http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/), but it didn't help.

The weird thing is that my usb boots perfectly from my comp at work and my roommate's computer, but it doesn't care for my computer.

I don't remember the complete specs, but it's an AMD with a P5N architecture mother board.

Anyone has an idea of what I can try to fix this!

Thanks
Nalfeind

---

### Post by Rubi1200 on 2011-06-08
Hi and welcome to the forums :-)

First check the integrity of the image:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If it is good, then try UNetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Nalfeind on 2011-06-08
Hi Rubi1200,

I checked the iso file with md5sum and it is good.
I also used Unetbootin to create my "bootable" USB.

My USB key does boot on other computers, its only on my computer that it poses problems. 

any idea?

Thanks 
Nalfeind

---

### Post by Rubi1200 on 2011-06-08
Okay,

First a question; is the USB stick formatted as FAT32 or something else?

Next, check this link:
[http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/](http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/)

make sure the files are where they should be.

---

### Post by Nalfeind on 2011-06-08
Yes it is formated as FAT32.

The files are in place.
I tryed moving and copying in different folders boot - boot/syslinux - (root) and other, but it didn't work either.

Nalfeind

---

### Post by Rubi1200 on 2011-06-08
It's odd that it works on other computers but not yours.

I did some searching but the only solutions suggest either formatting to FAT32 or FAT16 or checking the file as in the link I posted.

So, where does that leave us?

3 suggestions:

1. check the settings in BIOS; maybe something was changed inadvertently

2. try another USB stick

3. format the stick to FAT16

Other than that, not sure what to tell you.

---

### Post by Nalfeind on 2011-06-08
Hi,

I will try and keep you posted.

Thanks

---

### Post by Nalfeind on 2011-06-10
Hi,

1) My BIOS was fine, I had to make changes from default so it would boot on USB first instead of ... (I don't remember).

2) I tryed with an other USB (Kingston:FAT32) and it still didn't work but error message was different.

3) Then I tryed with my own USB formatted in FAT16 and ...... it worked!! Hurray!

So the problem was that my machine could not read correctly my FAT32 Pendrive USB key. 

Thanks to Rubi1200 for the help

Nalfeind

---

### Post by Rubi1200 on 2011-06-10
Hi,
that is great news and I am pleased you managed to get this sorted out :-)

Please mark this Solved using the Thread Tools near the top of the page.

Thanks.

---

