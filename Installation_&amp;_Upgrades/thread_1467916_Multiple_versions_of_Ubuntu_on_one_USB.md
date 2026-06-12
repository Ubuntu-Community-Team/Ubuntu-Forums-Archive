---
title: "Multiple versions of Ubuntu on one USB"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by God Of Atheism on 2010-05-01
Hi,

I want to make a live-USB containing among others both Ubuntu desktop i386 and Ubuntu desktop AMD64. How do I go about this?

I tried using unetbootin, first adding i386 and then amd64, but that failed. My computer with an athlon II did manage to boot, and showed it had booted into the 64-bit version (ram shown was 3.9 GB, i386 goes to about 2.7 I think), my wife's computer with a pentium 4 did not manage to boot, got to a black screen. I think this is because casper has issues, being overwritten (I'd seen something to that effect somewhere), and thus only the latest version added being booted (in this case amd 64).

I'm under the impression that the startup disc creator included won't help, nor won't the multicd.sh script, so how do I circumvent the issues?

---

### Post by oldfred on 2010-05-01
I did what you want with ISOs. You cannot save settings but can boot multiple systems:

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntuforums.org/showthread.php?t=1451184](http://ubuntuforums.org/showthread.php?t=1451184)

I did a combination of panticz and ky forums info and have 4 ubuntus, gparted, system rescue, and parted magic.

If you have a large USB key you can just do a regular install and make it dual boot.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
Somewhere recently herman also posted comments on a full install to USB. It is just like any other install but you msut install grub2 to the USB.

---

### Post by RubenK on 2010-05-02
That looks very promising. I came across both these sites before, but it's only this time that I actually get what's going on (which is not that much really...). I'm going to try make a USB drive that can boot:
Ubuntu
Ubuntu Netbook Remix
Kubuntu
Xubuntu
Mythbuntu
Ubuntu Studio
LinuxMint
CrunchBang

Maybe later I'll add other useful ones like DSL, GParted, Fedore, etc. I have 16GB so I can put a lot of em on there... =D

I'll keep you posted!

---

### Post by xanfantasy on 2010-05-02
This was a feature on Hak5 with not just Ubuntu but almost any Linux live cd out there. If you would like a ton of information on doing this with many OS then check out their forums.
[Hak5 USB Multipass forums]("http://www.hak5.org/forums/index.php?showforum=52")

---

### Post by RubenK on 2010-05-02
CrunchBang and Ubuntu Studio are not working yet. I'll look into it tomorrow. Messing with these kind of things always keeps me way too busy...

hak5 has some useful stuff (gparted i.e.) but no info on Ubuntu Studio or ChrunhBang...

---

