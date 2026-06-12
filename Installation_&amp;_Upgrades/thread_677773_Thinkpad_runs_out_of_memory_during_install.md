---
title: "Thinkpad runs out of memory during install"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by nlz on 2008-01-25
I'm trying to install Gutsy with a live CD on a IBM thinkpad r31 (intel celeron, pentium 3, 1.13 GHZ, 120 MB of RAM), but the install freezes all the time. If i install it in safe graphical mode, it end with:

[ 121.908000 ] out of memory: kill proces 4139 (gconftool-2) score 407 or a child
[ 121.908000 ] killed proces 4139 (gconftool-2)

if i start/install it normally from the live CD, the above text is shown + a lot of ununderstandable messages;
[..]
[..]
[ 226.6080000 ] call trace:
[...]
[...]
[ 226.6080000 ] EIP: [ <c81a39f> ] unionfs_rename+0x9f0 [unionfs] SS:ESP 0068:c1c55e24

It would be really nice if someone could help me out.

---

### Post by Partyboi2 on 2008-01-25
try the alternate cd from [here]("http://releases.ubuntu.com/releases/7.10/")
its a text base installer and is best for older hardware

---

### Post by nlz on 2008-01-29
The text based installer actually did function, thanks a lot. 

I'm now starting up in Ubuntu (which goes really slow, but i guess i'll have to adjust gnome a bit. 

I had to download the ISO of the alternate CD three times by the way before the md5sum was OK, how come?

Thanks a lot,

nlz

---

### Post by Partyboi2 on 2008-01-29
From what I have read if you use a bit torrent program to download the ubuntu iso if the md5sum does not match you can click on the iso and get bit torrent to download the missing pieces. Never tried it myself. You could try a lighter desktop like xfce desktop
```
sudo apt-get install xubuntu-desktop
```

---

### Post by nlz on 2008-02-01
xubuntu does the trick much better, thanks
although i got the feeling that a fresh xubuntu install is faster then if you upgrade (downgrade?) from Ubuntu..

---

### Post by Whiffle on 2008-02-01
Not necessarily.  Its the same thing, just a different desktop shell, everything underneath is the same.  Theres probably alot of stuff you can clean up though that will speed things up.  Search google for ubuntu speed tweaks, there are some that will help out.

---

