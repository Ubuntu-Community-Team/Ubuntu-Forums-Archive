---
title: "Edgy to feisty upgrade: can't boot (URGENT), mdadmin installed though no RAID"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by pilpi on 2007-05-01
Hi,

I started edgy to feisty upgrade through update-manager button yesterday. At some point after downloading the packages it asked me a question about RAID related to mdadm configuration, something about which disks to load before the rest of the system. (I have not had RAID on this pc and do not know if such a package was on my PC, at least I don't know that I would have installed it.) I think I left it at the default value, 'all', supposing that it wouldn't hurt. I read the 'help' of the choice too but it only confused me more.

Anyway, after the installation ubuntu now refuses to boot, saying that it's waiting for the root partition (on the RAID) to wake up or something like that, though no actual RAID disks are even configured.

I managed to get DSL linux access to the partitions so I've removed all configuration files related to mdadm from /etc/ (though those are on the root partition which it doesn't even access I guess), but that didn't help. I don't know how to access package management to remove mdadm that way. Can I remove mdadm just by editing files?

Thanks for any help,
Olli Savolainen

P.S. The installation process was really infuriating, taking all in all over a day since there were dialogs (about replacing config files most of which I actually haven't even changed!) in the middle of the process and someone would have had to babysit the installer to make sure it goes on. Ask questions before or after doing everything that takes time, please. Windows installers learned this lesson years ago.

P.P.S. The reason I'm upgrading in the first place was that in edgy everything was slowing down in edgy periodically and a process that would be busy doing something could easily make the whole system unresponsive (mouse wouldn't move at all or very slowly) for 15 minutes, unlike in dapper. Running ubuntu on AMD 1600+ with 512 MB RAM.

---

### Post by pilpi on 2007-05-06
Got the RAID problem finally fixed by burning the DSL-N CD, which has a 2.6 kernel (the regular DSL with 2.4 kernel didn't work since chroot wasn't compatible). 

So this should do it: 
[LIST]
[*] mount /dev/hdXX /mount/ubuntu_root
[*] cd /mount/ubuntu_root/
[*] chroot . apt-get --purge remove mdadm (actually I did chroot . dpkg -P mdadm or something but apt seems simpler)
[*] chroot . apt-get install mdadm (to reconfigure mdadm, removing RAID from boot by giving it the parameter 'none' when it asks -- because I couldn't run dpkg-reconfigure)
[*] and then again: chroot . apt-get --purge remove mdadm (it warned me about being screwed if there actually is a MD that needs to be run before booting the system and I went YAY since that kinda showed that I solved the issue)
[/LIST]

However, after booting a couple of times, at a certain point of the boot process ubuntu stopped taking anything from the keyboard (PS2). Detaching the keyboard and putting it back in made numlock work, but nothing else. 

I then proceeded to install a fresh ubuntu feisty. Now everything just rocks.  :)

---

### Post by mjgumbley on 2007-05-07
Started trying the DSL-N you suggest here - but how do I get it to unmount its own /cdrom so i can insert the Feisty CD?

(I'm trying chroot /dev/hda7, then apt-get remove --purge mdadm)

Any help would be most appreciated!

Thanks,
Matt

---

### Post by pilpi on 2007-05-08
I'm not sure that's possible, since I suppose DSL-N is running off that CD. You could try putting DSL-N on a usb memory stick, then boot from that, freeing your cd drive.

---

### Post by mjgumbley on 2007-05-08
My old system won't boot off a USB stick - but many thanks for the suggestion.

I spent last night trying to get it to boot in single user mode, using an old kernel but to no avail - I had low-level hangs at various stages in the boot. I tried removing those parts of the boot, but it would just hang elsewhere.

By adding rw init=/bin/bash to the grub entry, I could get a shell, insert the CD, but apt-get remove --purge mdadm would complain that dpkg-preconfigure couldn't re-open stdin and fail. 

I ran that command through strace, but it didn't yield anything obvious that might be wrong.

I ran several of the /etc/rcS.d scripts manually to get the usual pseudo-filesystems mounted; I remounted / read-write with mount / -o rw,remount - all to no avail. Perhaps the upgrade is too badly botched.

So, I'm giving up, and will re-install Feisty from scratch. I've been using Linux since TAMU - and I've NEVER been so badly burned by an upgrade. Very disappointed.

---

### Post by pilpi on 2007-05-09
Yeah. I was very disappointed, too. Gladly it worked so much better than any of the old versions after I got it reinstalled though.

---

