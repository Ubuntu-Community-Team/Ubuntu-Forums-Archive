---
title: "Gutsy RC install - Kernel Panic: Not syncing"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by Mobiesque on 2007-10-15
Hi all. Here's the basics - 

Fresh install of Gutsy RC. Install went fine, enabled restricted video driver (old nvidia card) and then downloaded the updates available. Restarted and received the following msg -

Starting up..
[26.193181] Kernel panic - Not syncing: No init found. Try passing init= option to kernel.

Any help would be much appreciated. Thanks.
Nick.

---

### Post by Vengeance_AU on 2007-10-15
I worked around this by hitting Esc on the grub boot options, and then selecting;

> Ubuntu gutsy (development branch), kernel 2.6.20-16-generic (recovery mode)

Bypass the root login, then when the machine comes up, shut your machine down and restart it normally. Worked for me - let me know if it doesn't work for you.

---

### Post by Mobiesque on 2007-10-16
Sadly this just returns the same msg. I'm gonna try a full format and reinstall.

---

### Post by MessiahAngel on 2007-10-16
Hi there :)

I might have found a solution :)
I edited the menu.lst from grub and saw that the line "initrd..." was missing for kernel 2.6.22-14 so i added it manually and it worked...

Hope it will be usefull :)

---

### Post by ecrissman on 2007-10-16
> **MessiahAngel said:**
> Hi there :)

I might have found a solution :)
I edited the menu.lst from grub and saw that the line "initrd..." was missing for kernel 2.6.22-14 so i added it manually and it worked...

Hope it will be usefull :)

I am having the same problem on a fresh install.  How exactly did you edit the menu.lst and what is the line you added?

Thanks

---

### Post by fusionisthefuture on 2008-01-27
ive got a small form factor shuttle with an amd athlon processor, its running OC'ed at 3200 speed, dont remember what it actually is.  anyways, i woke up this morning with a new cd of gutsy, and i checked the md5, it was good.  i ran the alt install cd, and got to "installing base system"  then it said it couldnt find something so i rebooted, and now it wont even start the install.  ive tried two different optical drives and two different hard drives and 3 different install cds, all of them never get past the black screens, and the errors vary.  live cds will say fixing recursive fault but reboot is required, others say that the kernel panic, cant sync, unable to mount root fs on unknown-block.  i also get a crc error.   i have tried these install cds on other computers and they boot right up and start the install, and ive even had ubuntu on this computer before, on the same hard drive, but i wanted to upgrade from feisty.  anyone got any ideas?
thanks,
-arne

---

### Post by fusionisthefuture on 2008-01-27
for people with the same problem as me, where you cant even install ubuntu, i think i solved my problem.  turn off overclocking.  seemed to work for me.

---

