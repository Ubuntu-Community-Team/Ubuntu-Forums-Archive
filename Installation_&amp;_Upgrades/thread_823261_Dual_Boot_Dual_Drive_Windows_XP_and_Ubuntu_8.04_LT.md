---
title: "Dual Boot Dual Drive Windows XP and Ubuntu 8.04 LTS"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by Driver on 2008-06-09
[CENTER]I have a very similar problem as to morning_napalm's,

hd0 = Windows xp (Master)
hd1 = Ubuntu (Slave)

I have added an extra "drive" purely for "Linux" based programs e.g ubuntu, XP on the other. 

After installation of Ubuntu from Cd to hd1, "Grub" was also installed.

During "Boot" Grub displays the 2 systems BUT choosing to boot to XP shows an error 13 message (Wrong.... Format) booting to Ubuntu OK.

I have since Formated HD1 in preparation for new installation of Ubuntu. (FIXMBR & FIXBOOT to recover xp).

I am a noobee that has always wanted to try "Linux" & a friend suggested a new one "Ubuntu" - I have also Explored:

SUSE 9.1,9.2
Mandrake 9.0
Lindows 4.5.212
Fedora 3,5
Konopix 4.0,3.6
Linspire 5.4
Winlinux 2003
Libranet 2.8.1
Mepis 3.3
Linare
Lycoris Desktop/LX
and now 
UBUNTU 8.04LTS

I have used EasyBCD 1.7.1 in the past with XP & Vista - dose it work with XP & Ubuntu if "Grub" is not installed?

any consrtuctive replies would be much appreciated

[IMG]http://i288.photobucket.com/albums/ll181/emmaroy/glitterwords15.gif[/IMG][/CENTER]

---

### Post by logos34 on 2008-06-09
> **Driver said:**
> [CENTER]
I have used EasyBCD 1.7.1 in the past with XP & Vista - dose it work with XP & Ubuntu if "Grub" is not installed?

yes, but you need to write grub to bootsector of linux root partition, *not* the MBR:
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by Driver on 2008-06-11
Thankyou so much for your quick reply.

Driver

---

