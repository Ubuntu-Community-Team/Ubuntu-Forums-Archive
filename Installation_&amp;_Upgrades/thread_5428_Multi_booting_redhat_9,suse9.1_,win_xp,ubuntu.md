---
title: "Multi booting redhat 9,suse9.1 ,win xp,ubuntu"
date: 2004-11-18
forum: Installation &amp; Upgrades
---

### Post by eldrich_rebello on 2004-11-18
Hi all,
my pc currently has no cd drive but i'll have a combo drive soon,.I have on cd REdhat 9 .suse 9.1 and soon ubuntu.i'm currently running windows xp pro and have 25.4 GB of unpartitioned space.in which order should i install the linux os's?also will i have problems with the kernels as all of them have different versions?will ubuntu detect the rest if i install it last?and what happens to the bootloader/?

Awating an answer
Eldrich

Intel P4 2.5 ghz
50 GB HDD
Intel extreme graphics 1

Also please tell me if my graphics card is detected by ubuntu...!

---

### Post by Karnaugh on 2004-11-18
I see allot of threads like this.

I cant understand the point of running multiple Linux distributions like that honestly. It's a bit crazy from a management (and partitioning point of view, although you might get away with sharing swap space), and I don't think you'd really learn anything worth while out of what I can guarantee will be a painful experience.

---

### Post by gfg on 2004-11-18
I dont know about your graphic card. But I belive ubuntu detects all other OS's under instalation and ask if you want to have them in your grub (bootloader) menu. You won't have any problems with the kernels as each OS will use it's own kernel if set up propely.

---

### Post by FLeiXiuS on 2004-11-18
In respose to your question things should be just fine.  Grub will install over the current MBR and it will detect all other Linux/Win OS's on your drives.  Give it a go for go.  

Multi-booting multiple distro's is great.

---

### Post by dataw0lf on 2004-11-18
Sure, dual booting distros is fun, but, damn, why are you going to dual boot these specific distros? I used to dual boot Gentoo with my primary distros, but I'm sure you can see the reasoning behind that. Plus, I'd push for you to boot Fedora Core 2+ (Fedora Core 1 has already been switched to legacy).
dataw0lf

---

### Post by jdong on 2004-11-18
well, for me, I boot 4-5 distros regularly, to package .rpms and .debs.

---

### Post by dataw0lf on 2004-11-18
> well, for me, I boot 4-5 distros regularly, to package .rpms and .debs. 
That's what I have separate machines for.
dataw0lf

---

### Post by eldrich_rebello on 2004-11-19
hi, 
nice replies,.I'm mainly interested in trying out some linux distros before settling down with 1 or 2..right now i'm stuck with windows xp and i'm hating every moment of it.i'm still waiting for ubuntu to arrive in the mail.the thing that scares me most about installing linux is the installation itself..i learn by trial and error..also limited disk space is another concern..do you pepl think that installing redhat 9 is worth the time and space?should i ditch windows and migrate completely to linux?suse 9.1 and ubuntu to be specific?

---

### Post by dataw0lf on 2004-11-19
[QUOTE=eldrich_rebello]
i learn by trial and error..also limited disk space is another concern..do you pepl think that installing redhat 9 is worth the time and space?should i ditch windows and migrate completely to linux?suse 9.1 and ubuntu to be specific?[/QUOTE]
Honestly, it depends on you.  If you really see no valid reason to keep Windows, then don't.  I used to keep an XP partition on my main box primarily for Visual Studio and some gaming.  But, if you don't see a reason to justify XP, then don't keep it.  It used to be that Windows was the 'failsafe', but with the expansion of better desktop versions in Linux, especially with the advent of Ubuntu, that really isn't the case anymore.
dataw0lf

---

### Post by FLeiXiuS on 2004-11-19
[QUOTE=dataw0lf]That's what I have separate machines for.
dataw0lf[/QUOTE]

No need for seperate machines when you have a superior hard drive which can do it all.  Unless you like working on all of the ditro's at once.

---

### Post by wazoo42 on 2004-11-21
I have xp on a sata drive, and then suse 9.2 and ubuntu on an ide drive.  I have installed all of the os's multiple times, and I haven't found the order to matter.

---

### Post by eldrich_rebello on 2004-11-21
thanks wazoo42 ,but unfortunately my pc was put together without my consent and so i had no say as to what went into in.I'm stuck with 1 physical HDD.will the multiple installs still work?i'm thinking of ditching either suse 9.1 or redhat 9 and sticking with ubuntu and win xp.i use xp mainly for IM purposes.If there are similar packages in ubuntu,i'll ditch xp too.would it be a good idea to tell the ubuntu installer to format the entire hdd and gp for a clean install?and will RH9/suse9.1 install after that?
Thanks
Eldrich

---

### Post by wazoo42 on 2004-11-21
Actually I think having them all on the same hd makes life easier.  So you already have xp and suse on there and grub lets you choose between them, no?  In that case, when you are in the ubuntu install, tell it not to put grub on the mbr and to put it on your /boot partition.  Then you need to edit grub on suse to something like:

title ubuntu
root (hd0,X)/grub  ***X is the /boot partition for ubuntu***
chainloader +1

---

### Post by wallijonn on 2004-11-21
RH9 is no longer supported. 

If you are happy with either distro why bother changing? 

I find that GRUB and LILO do not play nice, so I messed up my Ubuntu when playing around with Slackware 10. When I had Gentoo's VidaLinux installed in its own root I still had problems. I believe that Ubuntu likes complete control over menu.lst so if you make changes to older distros (like updating kernels) it may blow away Ubuntu's Grub.

I did the Linux shuffle (SUSE, RH, Fedora, Slackware, Gentoo, VidaLinux, FreeBSD, Immunix, IPCop, Debian, Prodigy, Mandrake, Bit-Defender, Ubuntu) and have settled on Ubuntu because of what it offers, GNOME 2.8, Evolution 2 & Firefox. I no longer feel any need to try other distros. I'm home.

---

