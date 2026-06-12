---
title: "Installation Problems"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by Anunnaki on 2008-01-09
A while back, I reformatted my Vista installation to set up a dual-boot with Ubuntu x64. I tried running the Live CD, and it would get to the initial screen ok, but after I pressed "Start Ubuntu", I would just have a blank screen. I know it was loading the OS because I could hear the disc drive spinning, but there was no video. I did some researching and some people suggested just using the 32-bit. So I decided ok and just installed that, with no problems.

However, now I have 4 GB of RAM and every time I boot up Ubuntu, it freezes at the desktop. I have a suspicion it's because of my having 4 GB of RAM in a 32-bit OS, so I'd like to install the 64-bit. The only problem is: I know from doing it in my Computer Maintenance & Repair class that if you just delete a Linux partition, the GRUB loader will fail and you won't even be able to boot up Windows. So I figured I could just run the Live CD, delete the Linux partition within that, and do a fresh install of Ubuntu x64. But now, even with a freshly downloaded/burned Live CD, I'm still having the same problem with getting no video after the initial screen. I thought maybe I could try the Alternate Install disc, but I don't know if I'll be able to mess around with the partitions in text mode.

If the text mode is similar to XP's text mode for messing with partitions, then I'll probably do okay, but I don't know if it's like that or like a terminal, in which case I wouldn't be able to do it. Would this method of just deleting x32 within a x64 Live CD and installing over it even work? Will GRUB work if I do that? And what can I do about the video problems?

My specs are:
Intel Core 2 Duo E6400
nVIDIA 8800 GTS
4 GB DDR2 800 RAM

---

### Post by Sef on 2008-01-09
> I thought maybe I could try the Alternate Install disc, but I don't know if I'll be able to mess around with the partitions in text mode.

Check out the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").

---

### Post by Anunnaki on 2008-01-10
I installed Ubuntu 7.10 with the Alternate Installation CD, but now I'm still getting no video. I've tried going into Recovery Mode and using the "dpkg-reconfigure xserver-xorg" command and going through that, and I've tried both the "nv" and even "vesa" drivers, and I still don't get any video when I try to boot up.

---

