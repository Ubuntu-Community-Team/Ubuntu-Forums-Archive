---
title: "upgraded to Gutsy, broke USB camera"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by fishtoprecords on 2007-10-20
Used to work great with fiesty. With Gutsy, connecting my Nikon camera via USB gets
"cannot mount voiume"
unable to mount the vouume.
Mount:L wrong fs type, bad option, bad superblock on /dev/sdb1 missing code page or helper program or other error. In some cases useful infor is found in syslog"

But I see nothing useful in the syslog.
Same camera with same USB cable works perfectly with Windoze and Mandriva (and used to work with Feisty on the same hardware)

---

### Post by fishtoprecords on 2007-10-27
I've now tried a USB nine-in-one card reader on my Gutsy upgraded Thinkpad T60p.
No joy.same error.

"Cannot mount  volume
details:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1, 
missing codepage or helper program,
or other error. In some cases useful info is found in syslog - try dmesg | tail or so"

Also tried another CF card, this one a 512MB Viking card. Same general error.

Pointers greatly appreciated.

---

### Post by herorev on 2007-10-28
I am also experiencing this.

My Logitech webcam worked well in Kubuntu Feisty, but after upgrading to Gutsy, it's no longer recognized. All the programs I tried say there aren't any video inputs. The audio input of the webcam is still recognized and works just fine.

The worst part is that I have no idea how to obtain more information. Searching for "cam" in KDE Help Center only lead me to caminfo, which just told me "Detected 0 Video4Linux devices."

---

### Post by Civean on 2007-10-28
Same here, webcam stopped being recognized after upgrading to Gutsy Gibbon. Worked perfectly with camorama, ekiga etc in Feisty. 

Webcam model: Kinstone KS-1668

Of what i've seen around the forums when searching for this, lots of other people are having problems with webcams breaking in Gutsy. Would be nice is someone could look this up, since I have no clue where to start...

/C

Update: 
A clean reinstall solved all my problems. I've just been updating since Tribe5 when I installed gutsy originally, I suspect a lot of strange cruft must have been hanging around. For you who have this problem when coming from feisty, maybe a clean reinstall would work for you too? (Windows-think, I know I know...)

---

### Post by CarlAdam on 2007-10-28
Same problem here. My USB-stick (inmation 1Gb) doesnt work anymore, works perfect in feisty and in win...

---

### Post by CarlAdam on 2007-10-28
Btw, i did a clean install of gutsy, so that cant be the problem:(

---

### Post by ossi on 2007-10-29
I also got a similiar problem. There seems to be a fix for Gnome. But where's the KDE one? You lucky gnomers luck here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025]("https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025")

---

