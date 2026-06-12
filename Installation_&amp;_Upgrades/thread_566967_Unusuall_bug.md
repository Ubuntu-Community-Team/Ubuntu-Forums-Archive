---
title: "Unusuall bug"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by ASPCartman on 2007-10-04
Hi all. So when i bought  new processor and memory (AMD Athlon 64 x2 and 1gb ~ 4800+mhz) i reinstalled my x86 (i had x64 processor last time but i was still using x86 v of ubuntu cos i dont like to search for special v of packages or compile them myself many times). So i install ubuntu 7.04 as usuall. After installing i update everything. Then i install video drivers (Ati x1800 gto2) using tutorial on wiki (always worked. best tutorial but im too lazy to search for link now) So i do alll as always. Then i reboot.... and i got a black screen. After hours of thinking i went to recovery mode and did
sudo rm /etc/X11/xorg.conf

U now what? It worked. Linux started with no issues.

First question:
How the hell it started without xorg.conf (it didnt remake it. there is no xorg.conf in x11)
Second:
How to make it back?
Third:
Wtf!? How to install drivers for my video card in other way? (fglrx +xgl). Any scripts ?:confused:

---

### Post by ASPCartman on 2007-10-04
Just installed gutsy. same thing.

Using this guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

### Post by PmDematagoda on 2007-10-04
You might be using Gutsy which has Bullet-proof X that can start X in failsafe mode when you remove the xorg.conf file. In Feisty, if you remove xorg.conf then you can't start X at all.

Anyway, your problem may be the video drivers being incompatible with your VGA card. Is it a newly released card? I do not think I can help you with ATI as I use Nvidia but I will do what I can.

---

### Post by ASPCartman on 2007-10-04
Emm i can start feisty AND gutsy without xorg.conf.
I have x1800 gto2 PCI-e

Everything was fine before i ugrade my pc with proccessor and ram

---

### Post by ASPCartman on 2007-10-05
Noone knows? Thats cant ba true. Can someone give me a link to some script for auto installing? Or guide or atleast say wtf this all is happening? How the hell i install this damn fglrx!?

---

### Post by PmDematagoda on 2007-10-05
If you changed the processor it could attribute to most of the problems. Any OS when installed is optimised to work with a particular setup. If that setup is changed, especially the processor then problems will arise, so the best I think you can do in this situation is to re-install Ubuntu.

---

### Post by ASPCartman on 2007-10-05
Man how did u read what i wrote?

1, I used ubuntu. All ok
2. Then upgrade
3. Then reinstalling Fiesty
4. Then got bug with video
5. Installing Gutsy
6 = 5

---

