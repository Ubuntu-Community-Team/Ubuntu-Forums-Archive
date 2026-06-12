---
title: "Making Ubuntu use lilo instead of grub"
date: 2004-11-24
forum: Installation &amp; Upgrades
---

### Post by FeliceMente on 2004-11-24
Can I, someway, make Ubuntu installer use lilo instead of grub, when installing the bootloader, at the end of the installation process?

I need this, because grubs seems to cause a lot of problems to my NTFS Windows XP partitions.
I already had problems in the pas, with grub installed by Fedora Core 2 on a laptop, and installed by Fedora Core 1 on a desk PC. I also had a Windows XP bootable partition, at the begining of the this, and, in both cases, grub set it as hidden, so I manualy had (using parted) to set that flag off for making the work again.

With ubuntu instead, on a desktop PC, everythng seemed to have gone ok after the installation, but, after 4-5 days of use of both the Linux and Windows XP partition, this one stopped woking, and this time, I got actually corrupt (I could recover the data using one of those programs for recovering data from llost NTFS partitions), so.. I can't be 100% it's grub's fault, but...
1) I want to use Ubuntu
2) I unfortunately still need Windows XP

so... If I can make Ubuntu installer (maybe from the boot prompt?) use lilo instead of grub, that great.

Anyway... am I the only one who experienced problems with grub?

---

### Post by jdong on 2004-11-24
Yeah, you're one of the only ones to have these issues!


LiLO is in the repository.

---

### Post by FeliceMente on 2004-11-25
[QUOTE=jdong]Yeah, you're one of the only ones to have these issues![/QUOTE]
Ok, I'm not the one, so... considering there's a little percentace (also if very very small) of users who got problems with grub, why do some distributions, like Ubuntu, uses it as deault bootloader?

> LiLO is in the repository.
Well, but is there a way for telling Ubuntu, during the installation process "use lilo, don't use grub"?
For example, passing some parameter just after I've inserted the installation CD, etc...?

The first time I tried to install Ubuntu, I had a corrupted disk, so the installation stopped, and I could see a menu. In this menu, I saw the possibility of installing lilo instead of grub. Can I make this menu appear, someway?

Or... what happens if, at the end of the installation process, when I'm asket wheter to install grub or not,, I choose not to install it?

---

### Post by wallijonn on 2004-11-25
I've heard just the opposite - that it is LILO which has more problems with NTFS5.

Do you have any anti-virus software which touches the mbr? (Like Norton?). It could be the problem.

---

### Post by FeliceMente on 2004-11-26
[QUOTE=wallijonn]I've heard just the opposite - that it is LILO which has more problems with NTFS5.[/QUOTE]
Well, I've used lilo for yers without any problem, and also with Windows XP (I especially used it with Slackware 9.1 and 10), I never had problems with NTFS partitions (both primary and logical) using lilo, but always had with grub.
On Fedora Forums, there have been a lot of topic about partition problems caused by grub...

> Do you have any anti-virus software which touches the mbr? (Like Norton?). It could be the problem.
I don't use Norton. I use avast 4.5 home edition under Windows XP ([www.avast.com](www.avast.com)), and I don't think it touches the MBR.
Above all, I've used it for a lot of time, and never had problems with lilo.

Anyway, once more, is there any way of telling Ubuntu installer, during the installation proces: "use lilo, don't use grub"?

---

### Post by poptones on 2004-11-26
I also want to use lilo and it has nothing to do with problems caused by grub - I just need to use lilo for a security package. Every time I try to install it I get errors telling me I have to edit lilo.conf manually. I do so, run lilo -v, and it says everything is ok. Reboot, still using grub.

A FAQ or some kind of support on this would be nice. I have no clue why this isn't working, never had to fix a bootloader before.

---

### Post by FeliceMente on 2004-11-26
[QUOTE=poptones]I also want to use lilo and it has nothing to do with problems caused by grub - I just need to use lilo for a security package. Every time I try to install it I get errors telling me I have to edit lilo.conf manually. I do so, run lilo -v, and it says everything is ok. Reboot, still using grub.

A FAQ or some kind of support on this would be nice. I have no clue why this isn't working, never had to fix a bootloader before.[/QUOTE]
Infact.... in my case, I had a lot of problems when trying to remove when recovering the HD, grub from my MBR.
Event rewriting the MBR using Ranish Partition Manager o 'fixmbr' command from Windows XP installation CD weren't able to remove grub!!!

---

### Post by wallijonn on 2004-11-26
FeliceMente,

I believe to remove GRUB you issue a [COLOR=Red]fdisk/mbr[/COLOR] command. You would then issue a[COLOR=Red] fixboot[/COLOR] command to have WXP scan the disk for bootable partitions & create a new MBR.

SPM has a lilo package that can be installed. Obviously it is not something which I am prepared to experiment with as I find that GRUB has been working fine for me. So I don't know if it would create a [COLOR=Red]/etc/lilo.conf [/COLOR]after running [COLOR=Red]/lilo[/COLOR] from a root terminal. [COLOR=Green]/boot[/COLOR] already has most images in it so it should be an easy matter to[COLOR=Red] sudo gedit /etc/lilo.conf[/COLOR] and edit it accordingly.


.

---

### Post by sect2k on 2004-11-26
Try runing an expert install (type expert at the boot prompt). It will let you choose which Boot loader you want to install.

Make sure you have the final release ISO images, because preview release has some issues and will install GRUB even in expert mode.

---

### Post by FeliceMente on 2004-11-26
[QUOTE=sect2k]Try runing an expert install (type expert at the boot prompt). It will let you choose which Boot loader you want to install.

Make sure you have the final release ISO images, because preview release has some issues and will install GRUB even in expert mode.[/QUOTE]
I finally got the answer I asked for!
Thanx, that's just what I asked! :-)

---

### Post by snipes420 on 2004-12-02
What if you have already installed ubuntu? do you have to do a complete reinstall just to replace the bootloader?

---

### Post by FeliceMente on 2004-12-14
First, someone is some other post explained his difficulties doing this. Second, I couldn't easily manually remove grub. Thir, I was anyway asking for a way to choose lilo during the installation process, not just for a way to resolve this "problem" only in this case.

Anywa, I can't still understand why the Ubuntu team decided to use grub instead of lilo, that I think it's still great...

---

