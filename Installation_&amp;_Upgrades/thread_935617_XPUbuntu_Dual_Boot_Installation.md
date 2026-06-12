---
title: "XP/Ubuntu Dual Boot Installation"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by kimberkarrier on 2008-10-01
Hello All, and thanks in advance for your help here. 

I'm currently running XP on my HP Pavilion dv5020us laptop equipped with AMD Turion 1.8 Gb 64 bit processor, 1 Gb Ram, ATI Radeon Xpress 200m video (128 mg system shared memory I think), Broadcom wireless, and an 80 Gb HDD. 

I've got entirely too much useless crap on this machine now, so I was going to wipe the drive and reinstall XP, but a friend of mine is trying (nearly to the point of irritation) to get me into this Linux OS. Figured I'd give it a shot, but there is appearantly a bit of difference in opinion on how to set this up for dual boot, so I figured I'd go straight to the "horses mouth". I have to keep XP as my repair hobby is 100% windows based, and nearly all of my of my related software is Windows based as well... :(

To make a long story short, would someone be so kind as to offer me (as detailed as possible) a step by step installation process so's that i can do this without pulling my hair out. :) As I said, I'm going to wipe and reinstall XP first, then install Ubuntu, but how exactly this is done, and all this et3/home/root stuff has got me lost to tell the truth...

Also, I've heard horror stories about Linux on laptops not being capable of supporting hardware due to incompatability issues, etc... Any help on preventing that would be great too if anyone has a comparable machine with this already done! 

Thanks again in advance

---

### Post by virtuallinux on 2008-10-01
Creating a dual boot system can actually be pretty straight forward.

1) Install XP
2) Boot the Ubuntu live cd.  Choose the first guided option (resize) for partitioning your hard drive.
3) complete install

Ubuntu will install the GRUB bootloader automatically, and it should recognize your XP install.

There are hardware incompatibilities sometimes, but there are lots of people here who are more than willing to help you resolve them.

---

### Post by WWSmith36 on 2008-10-01
Drive partitioning is kinda of a touchy subject.  There is no right or wrong answer so it causes a lot of debate.  My recommendation is that you follow this partitioning scheme before your installation

20 Gig primary partition for windows ntfs
20 Gig primary partition for ubuntu ext3

the rest of the drive can contain and extended partition with
1.5 x memory for linux/swap
remainder for data partition as ntfs

This configuration allows you to use a common data partition which both window and linux can read.  This is where you can store videos, music, picture, etc.  To do that you can just create links from ¨My Documents¨ or ¨Home¨ folders.

Hope this helps

---

### Post by Forbees on 2008-10-01
i like to partition my hard drive right down the middle . . . half and half


but i'm now started to use linux WAAAAAAAYYYY more than xp...

like xp is for running counter strike scorce . . . and CIV4 . . . that it lol

those games didn't seem to work in wine OR crossfire >,<

my xp system is on the verge of crash lol . . . i've been blue screens once or twice (yes it does still exist)

i'm actually looking for a nicer modded XP to install . . . i've run windows custom (mod'd with vista themes and security checks + cool programs) and windows Crystal (many cool themes, security and programs)

i loved both of them but after about 6 months they start to die . . . than again all XP starts to die in like six months( i heavily torrent, and game game on xp)

any recomendations to a good XP to try?

normal XP sucks . . . XP Vista Black+Blue Ultimate sucks

---

### Post by kimberkarrier on 2008-10-02
Um...wow! Thanks all for your response. I'm familiar with most of the inner workings of XP, but not so much with linux so i'll likely post back with any additional issues that may arrise. I had the feeling that it was that simple, but to here everyone talk, i figured it was best to ask first, so thanks again!

Forbes, I gotta say that i love gaming too, but unfortunatly i have little time for it. :(  You're right though, the more i work ON (not so much with) XP, the more dissatisfied i become. As far as the other mods and os's...dont get me to lyin :)  I only work on the XP Home/Pro, and try my damndest to aviod Vista, but that doesnt work so well...hehe

As a matter of fact, i've found far more Linux based software lately to correct Windows issues...and for that very reason, i'm gonna dual boot my machine with Ubuntu...

Thanks again all...and i'll get back to you to let you know of any issues i run into, or to report success... :)

Later,

---

