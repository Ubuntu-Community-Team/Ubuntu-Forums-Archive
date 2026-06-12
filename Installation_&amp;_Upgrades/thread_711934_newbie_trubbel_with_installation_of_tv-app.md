---
title: "newbie trubbel with installation of tv-app"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by the_glider_pilot on 2008-03-01
Hi all

I just started to use ubuntu (again, and so far i am very satisfied, i am using ubuntu 7.10)
sure there are a lot of things that are hard to figure out, but i got most of my stuff working. 
However there are one thing i just cant figure out.
I have a analog cabletv in my building, and only one decoder wich i have in my livingroom.
I have a tv-card in my computer, a happanuage tv-express, it's a Bt878 card. and i found a sw that would enable me to watch the cable shows on my computer aswell as in my livingroom. this sw is called cabletv 1.3.9. 
After much hussle with dependencies i manage to get the thing installed. but i can not get it to start.

when i try to start it this is what happends:

blackangel@Bad-Boy:~$ sudo cabletv


CableTV - CableCrypt Decoder for Linux - Version 1.3
by TWISTI & FUX (3/16/2002)

WARNING: Your X-Server has no DGA support.
WARNING: couldn't find framebuffer base address, try manual
         configuration ("v4l-conf -a <addr>")
can't open /dev/vbi for reading, No such file or directory
no video grabber device available
blackangel@Bad-Boy:~$ 

Any ideas of how i can get it to work?

Help is much appreciated.

---

### Post by the_glider_pilot on 2008-03-01
nobody got any ideas at all?

---

### Post by 1337 on 2008-04-04
Same here, it just ain't working on a modern Linux distro I guess.

Regards

---

### Post by LiMaO on 2008-04-09
**Here's the answer directly from CableTv's website:**

[I]Q3: I get a:

can't open /dev/vbi for reading, No such file or directory

A3: You need a device in your /dev directory. It's needed for sync problems on some systems. Maybe it will be disabled in a future version. To create this device change to the cabletv source directory:

$ cd bttv
$ ./MAKEDEV

or create it manually:

# mknod /dev/vbi0 char 81 224
# ln -s /dev/vbi0 /dev/vbi
[/I]

CableTV website: [http://sector17.tvand.net/cabletv/]("http://sector17.tvand.net/cabletv/")

Anyway, if you get it working, please let us all know! =)

Regards,

LiMaO

---

