---
title: "Installing on Thinkpad 240 without CDROM boot?"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by maagnh on 2007-01-10
I would like to try and install Ubuntu on my IBM Thinkpad 240. It's a Celeron 400 with 192meg of ram. It's an old machine that originally had Windows 98 on it. The hard drive died and I bought a used replacement for it. The HD has nothing on it. I have a floppy disk drive and an external USB cdrom drive. No wifi.

Here's the problem:

The system will not boot from a CD. The BIOS does not support booting from anything except the HD or the floppy. Is there a way I can install Ubuntu on this system? 

Keep in mind that although I'm an experienced Windows power user I am a complete linux newbie.

I have a Windows 98 boot disk with drivers for the cdrom drive ifthat helps.

I appreciate any help you can give as I take my first tentative steps toward linux. I need to learn because I've made up my mind I'm not going to be upgrading heading down the path of Vista. I've had enough MS BS. Thanks.

---

### Post by K.Mandla on 2007-01-10
Hi maagnh. Take a look at [https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto) ... I've had good luck with that, installing to machines that had no CD boot option in the BIOS. It's going to depend on your hardware, of course. :roll:

---

### Post by maagnh on 2007-01-11
Thanks for the info. I checked the link and there is a comment regarding the utility not supporting external USB cdrom drives. I will give it a try though.

---

### Post by rodneybarrett on 2007-01-18
I am wanting to do the same thing and came across your post.   Any progress on this?   Since a thinkpad 240 doesn't even have a ethernet port built it,  you can't even do the bootp load.

---

### Post by cloakable on 2007-03-08
I managed to get Ubuntu installed on it using a 2.5 to 3.5 addapter to install the target hdd into my desktop, but I found that Ubuntu isn't really well suited to this hardware - even with a minimal install, it's a bit too heavy.

---

### Post by hencke on 2008-02-24
I had a very positive experience installing Xubuntu 7.10 on my ThinkPad 240 and I would like to share it with anyone interested. Hardware needed:

-ethernet card (and internet connection)
-ThinkPad 240 (or any other PC) with:
 -preferrably 128 MB RAM (64 MB might be enough) or more
 -Windows 98 or newer (should work up to Vista) (any linux distribution should also do, but I'm not going to go into that, please refer to the second link)
 -no cd-rom or floppy drive needed

I made a small HowTo here:

[http://ubuntuforums.org/showthread.php?p=4395086#post4395086](http://ubuntuforums.org/showthread.php?p=4395086#post4395086)

More information available also here:

[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

