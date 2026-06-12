---
title: "Ubuntu installation with a different GRUB location."
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by Hgetis on 2009-12-12
Greetings to all!
I am kind of new in Ubuntu linux.. I have been using another linux distro several years ago for a limited time, so I am not as familiar as I wanted to be with linux.

_The story:_
In my PC there are 2 hard disk drives.
The first has a Windows XP installation with its boot loader (NT loader).
The second one is empty and I want to install Ubuntu.

Now what's the catch... I really do NOT want a dual boot system. I mean I do NOT want to install GRUB in one of the hard drives which will boot my system to Ubuntu or to Windows.

What I want is to have 2 different operating system installations in 2 different hard drives like the one hard drive does not know the existence of the other one.

This is easy to be done. I can just connect firstly the one drive, install Windows, and then disconnect this hard drive from the mobo and connect the second one. Then I shall install Ubuntu to the other hard drive.

Everything it's ok up to here.

But,
unfortunatelly my mobo does NOT support Boot Selection Option during POST (usually with F11 or F12 key) cause it's kind old...

_My question:_
Years ago I had the same hardware and software configuration (2 HDDs, 2 different OSes), but then I used a simple diskette, which probably had a boot loader (LILO) inside, and via this diskette my Linux distro booted up from the 2nd HDD. When there was no diskette into the floppy drive the 1st HDD was booting normally into Windows...

So, I just want to do the same thing but I don't know how to do it and I really need some help..

In synopsis,** how do I install Ubuntu in a hard drive but its GRUB loader is installed somewhere else (floppy or USB flash)???**

Thanks in advance!
Hgetis
Greece

PS.
Sorry for the very analytical post, but I need to explain excactly what I want, so u can help me on this!

---

### Post by darkod on 2009-12-12
During the install process, in the last screen, step 7, before clicking the Install button, click on Advanced button and it will show advanced options among which where to install the bootloader (grub).

---

### Post by Hgetis on 2009-12-13
Many thanks! :)
I'll try that!

---

### Post by slakkie on 2009-12-13
You can do it, just make sure the Windows bootloader knows about Ubuntu and then chainload to grub on the Ubuntu disk. But I guess grub2 will see you windows partition and create an entry for it.

You could also have a look here:
[http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/](http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/)

And specific:
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html)

This will tell you how to create a (legacy) grub floppy, which you can use to create a similar floppy as your previous Lilo boot floppy.

---

