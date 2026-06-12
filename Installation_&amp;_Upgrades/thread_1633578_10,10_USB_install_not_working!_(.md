---
title: "10,10 USB install not working! :("
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by xadz on 2010-11-29
Really really would love Ubuntu on my netbook, it looks so swish!  Anyway, I've burnt a CD, slapped it on my desktop and created a USB key using the USB creator that came with it, on a 2GB memory stick (I've tried two different ones).

Everything says its done ok, I shove it in my Samsung N150 Netbook, go to boot from the USB and it just idles at a black screen that says "SYSLINUX then some numbers and copyright info", I've left it for atleast half an hour there and nothing, help, please!  So irritating, Wubi installer just seems to always crash half way through too, ugh!

I'm currently running W7 on both, on the netbook which I'm trying to install ubuntu on, it's 32-bit and I'm running windows on a 40gb partition, and have a 70gb one ready for ubuntu.

The main computer is 64-bit windows 7.

So, either a fix for the USB, or a way to install it without using the wubi installer on a netbook with no disk drive would be amazing!

Thanks Ubuntu'ers!

---

### Post by dino99 on 2010-11-29
wubi is not for working :(, make a real install

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

lot of usb issues fixed with the 2.6.37-7 kernel:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

---

### Post by xadz on 2010-11-29
They all seem to be if you're already running linux, unfortunately I'm not just yet.  Also, it may be worth noting that I've never really used linux before, which kind of punches a hole in any plans of using any complicated terminal commands.

---

### Post by xadz on 2010-11-29
I've just tried the USB stick in my desktop, to be given the same issue.  Also, I tried the disk in my desktop and worked a charm, so.. hm.  Would it be worth trying it on an external hardrive, seeing as though this has failed on two memory sticks so far??

---

### Post by xadz on 2010-11-29
No joy on the external hard drive either!  Been trying now for 48 hours, so irritating!

---

### Post by Phil92804 on 2010-11-29
I downloaded the netbook version to my laptop then created a usb boot drive using [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) - just followed the directions and it worked very well on a netbook.  Make sure the bios on your netbook have booting from a usb drive as the first option.  I didn't know how to at the time, but found that I was able to get to the bios menu by pressing F2 key as soon as the starting sound and screen began to appear.

The instructions on the Ubuntu site are great and I was able to walk myself through the entire process.  

I am nowhere near a techie, but it all worked and am enjoying using Ubuntu 10.10 on my laptop 98%+ of the time - faster and more efficient.  I even prefer it over Apple - and I loved Apple at one time.  Use it on the netbook, as well.  In fact, I am moving a very small company from the Windows world to Ubuntu - it's that great. 

Don't give up - it works well.

---

### Post by xadz on 2010-11-29
I've just tried that pendrive linux site, and now it shows a purple ubuntu landing screen, then starts loading a ton of stuff and shows messages like.

Kernal Panic - Not syncing VFS: Unable to mount root FS on unknown-block(8,1)

No file system could mount root, tried: ext3, ext2, ext4, fuseblk

It then freezes at kernel_thread_helper +0x6/0x10 

Ugh!  Just when I thought I had it.

---

### Post by Phil92804 on 2010-11-29
At this point, I'd start with a clean usb drive, download the netbook distribution from the Ubuntu site to your computer, create a new bootable usb drive, and use it to install on your netbook.

I don't claim to know very much about anything techie, but it would seem that a file might be corrupt, or not working correctly - so start completely fresh!

Good luck and please let us know.

---

### Post by xadz on 2010-11-29
I done exactly that, swiped another stick, re-done the whole process using the pendrive-linux and it worked a charm!  Using it right now, and loving it!  Guess I was so worked up at the complicated stuff I completely overlooked something that simple, thanks a lot! :D

---

### Post by Phil92804 on 2010-11-29
I am so pleased it all worked out - now enjoy Ubuntu - it's great.

---

