---
title: "Dual Boot Windows 7 &amp; Upgrading Ubuntu"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Trilby on 2010-05-03
I've heard people have been finding that when they upgrade from 9.10 to 10.04 on a machine that dual boots 9.10 and windows 7, they can't boot windows 7 afterwards. There is a fix to this problem but I would rather prevention to a cure.

Is there a way of ensuring I won't have this problem and how common is the problem?

Thanks,
Trilby

---

### Post by Ad@m on 2010-05-03
Just browse this forum, upgrading = asking for issues.

It is best to do a clean install, which automatically created my Windows 7 disk entry.

---

### Post by frantid on 2010-05-03
Most of the problems have been where grub has been installed.  Just install it to the MBR or /dev/sdx  where x is the disk from which your computer boots.

---

### Post by oldfred on 2010-05-03
Someone posted the incorrect instructions that has checkboxes for every drive and partition:

[COLOR=Red]If you're unsure which drive is designated as boot drive by your BIOS, it is often a good idea to install GRUB to all of them. 
           
Note: It is possible to install GRUB to partition boot records as well. However, this forces GRUB to use the blocklist mechanism, which makes it less reliable, and therefore is not recommended.
[/COLOR]
What is not clear is the first part only mean MBR or sda, sdb etc as the boot drive. Many do not know difference between MBR - boot drive and PBR boot partition, so they check everything.
 Second part refers to sda1, sda2 etc or boot partition. Windows has essential boot info in its partitions so if grub is installed to a windows partition in sda1 then windows will not boot.

---

### Post by Trilby on 2010-05-05
> **oldfred said:**
> Windows has essential boot info in its partitions so if grub is installed to a windows partition in sda1 then windows will not boot.

Do I get the option of where to install grub if I simply upgrade, or is that an clean install option only? If so how do I do a clean install? Can I do so with losing programs and settings?

---

### Post by oldfred on 2010-05-05
It seems on upgrades that they present a check box of every drive & partition on where to install grub. I have not upgraded but someone posted what it looked like.

On clean installs it presents a combo box if you use the advanced button on where to install. I am not sure what logic it uses on where to install as a default. My first install of the first beta I missed the advanced button and it installed to sda even though the install was on sdc7 (I boot from sdc to karmic so I was ok).

---

### Post by Trilby on 2010-05-05
> **oldfred said:**
> On clean installs...

Do I just boot Ubuntu and stick a 10.04 disk in, or I do have to do something else first?

---

### Post by wilee-nilee on 2010-05-05
> **Trilby said:**
> Do I just boot Ubuntu and stick a 10.04 disk in, or I do have to do something else first?

A fresh install would be booting a live or alternate cd then installing. Now this will overwrite wherever you install, so if you have stuff to save back it up. You are going to want to try out the live CD first to make sure it's runs okay, if you use a thumb to test the ISO it will run a bit faster.

---

### Post by Trilby on 2010-05-11
I have finally got round to installing 10.04. I upgraded and experienced no problems other than a late night. Some things work better than before, such as media support (That said, I'm not convinced I like Lucid yet for a few reasons). Windows 7 boots with out any problems too so it would seem that my concerns were for nothing.

Thanks for all your help and advice,
Trilby.

---

