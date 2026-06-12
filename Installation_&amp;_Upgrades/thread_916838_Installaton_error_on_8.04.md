---
title: "Installaton error on 8.04"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by Whiteeagle on 2008-09-11
My PC has XP SP2 on it. I have a hard drive (60Gigs) free for my 8.04. I installed here and on another PC I have. It works on the other PC after I corrected my user name for it. So........

When I click to go into ubuntu I get this:
Busybox v1.1.3 (debian 1:1.1.3-5ubuntu12) built-in shell (ash)

Enter 'help' for a list of built in commands  ( I enter 'help' after (initramfs) ) and I get this:

(initramfs) help
,: alias break cd chdir command continue echo eval exec exit export false getopts hash help let local pwd read readonly return set shift times trap true type unlimit umask unallas unset wait
[ [[ ash awk basename busybox cat chmod chroot chvt clear cmp cp cut deallocut dumpkmap echo egrep env expr false fbset fdflush fgrep grep hostname ifconfig ip kill in loadfont loadkimap is mkdir mkfifo mknod mkswap mktemp more mount mvopenvt pidof printf ps pwd readlink reset rm rmdir sed setkeycodes sh sleep sort stat sync tail tee test touch tr true tty umount uname uniq wget yes
(initramfs).

(Of course I have no idea where to go from here ) so I used:
Control alt delete and it  reboots

I had the password problem on the other PC I have so I think the installation was successful with the exception of this error and I just don't know what to do now. The other PC had this same problem but corrected itself the next day after I installed it.

Thanking you guys in advance. The purpose y'all do for this system is so fantastic. Thanks.
Jimmy

---

### Post by overdrank on 2008-09-11
Hi and if I understand you are having issue installing on one of your systems. You may try and use the F6 option from the install window on the live cd. this will allow you to edit the kernel line and remove quiet splash and add noapic before the --
Could you give us some system specs?

---

### Post by Whiteeagle on 2008-09-11
> **overdrank said:**
> Hi and if I understand you are having issue installing on one of your systems. You may try and use the F6 option from the install window on the live cd. this will allow you to edit the kernel line and remove quiet splash and add noapic before the --
Could you give us some system specs?

Win XP Home Edition V 2002 SP2
Celeron(R) CPU 2.66GHz
Go easy on me, I'm almost a virgin with Ubuntu.
What gets me is I put Ubuntu on my 2 PCs. They both had this same identical problem but the other PC corrected itself after 1 day. I keep hoping this one will too but no such luck.:lolflag:

---

### Post by Whiteeagle on 2008-09-11
> **Whiteeagle said:**
> Win XP Home Edition V 2002 SP2
Celeron(R) CPU 2.66GHz
Go easy on me, I'm almost a virgin with Ubuntu.
What gets me is I put Ubuntu on my 2 PCs. They both had this same identical problem but the other PC corrected itself after 1 day. I keep hoping this one will too but no such luck.:lolflag:

something I just thought of that might be the problem is, quite some time ago the program "Seagate Technologies Dynamic Drive Overlay v9.85" was put on my PC to partition part of it. I cannot find a way to remove it and I remember when I tried to install 7.10 it wouldn't install and there was some talk around the house here that seagate was the problem.

---

