---
title: "Dual Boot Question - Ubuntu 12.04 &amp; Windows XP"
date: 2013-01-31
forum: Installation &amp; Upgrades
---

### Post by arvindx on 2013-01-31
Hello Group,

I'm a long time follower of Ubuntu and FOSS :D. After trying out Ubuntu (WUBI included), I'm finally ready to dual boot (need to keep windows for work related programs).

My hard drive has 2 partitions - C: (user files) & D: with Windows installed on D: (free space about 50 GB). 

Questions --> 

[LIST=1]
[*] Can I resize the D: drive to allocate 30GB for Ubuntu (during Ubuntu installation itself) by changing/editing the disk space?
[*]Or should I use gparted or disk-keeper (in windows) to resize D: first before I begin installing?
[*] Would there be any risk to dual boot here due to the Windows being installed in D: drive as against the usual C: drive?
[*] Also, should I leave Windows bootloader in control of the boot instead of letting GRUB takeover?
[/LIST]
 On the other hand - am also open to wiping out hard drive and just do Ubuntu only install and then setup Windows XP in a virtual box.

Sadly, there are still windows dependencies :( which require my XP in some form - dual or virtual.

Waiting for your opinions. 

Thanks, Arv.

---

### Post by coldraven on 2013-01-31
If your computer CPU supports virtualization and if you have a reasonable amount of memory and if you have an XP install disc I would go for XP in a VM.
Installing XP with all it's updates is always a long boring process so if you do make a VM then make a backup copy of it straight away.

If you go for dual boot it might be worth considering buying a bigger hard drive. If you have a desktop PC just use it for ubuntu and leave your XP disc alone. 
If you have a laptop you could clone your XP setup to it and have plenty of space for ubuntu.

---

### Post by Mark Phelps on 2013-01-31
While a VM is certainly an option, if you already have XP in place, why go through all the trouble of reinstalling it, and all your apps, and doing HUNDREDS of Windows Updates only to end up with what you have already?  Your choice.

As to dual booting:
1) Resizing -- while using GParted or the Ubuntu installer has resulted in some filesystem corruptions with Vista, Win7, and Win8 setups, they haven't been reported for XP.  Still, to be safe, I would download and burn the Minitool Partition Wizard Boot CD, boot from that, and use that to resize the XP partition.
2) Ubuntu install is going to install GRUB -- unless you prevent it.  Windows being in D: instead of C: won't matter to GRUB. AFter the install, when you boot into Ubuntu, open at terminal and enter "sudo update-grub" -- to regenerate the GRUB config file to add an entry for XP.

Good Luck

---

### Post by arvindx on 2013-01-31
> **coldraven said:**
> If your computer CPU supports virtualization and if you have a reasonable amount of memory and if you have an XP install disc I would go for XP in a VM.
Installing XP with all it's updates is always a long boring process so if you do make a VM then make a backup copy of it straight away.

If you go for dual boot it might be worth considering buying a bigger hard drive. If you have a desktop PC just use it for ubuntu and leave your XP disc alone. 
If you have a laptop you could clone your XP setup to it and have plenty of space for ubuntu.
Hi Coldraven,

Thanks for your help. I will check up on the VM requirements again (had run the W7 demo on VB earlier). PC runs on a core 2 duo 1.8, 3gb ram & 250gb HDD.

---

### Post by arvindx on 2013-01-31
> **Mark Phelps said:**
> While a VM is certainly an option, if you already have XP in place, why go through all the trouble of reinstalling it, and all your apps, and doing HUNDREDS of Windows Updates only to end up with what you have already?  Your choice.

As to dual booting:
1) Resizing -- while using GParted or the Ubuntu installer has resulted in some filesystem corruptions with Vista, Win7, and Win8 setups, they haven't been reported for XP.  Still, to be safe, I would download and burn the Minitool Partition Wizard Boot CD, boot from that, and use that to resize the XP partition.
2) Ubuntu install is going to install GRUB -- unless you prevent it.  Windows being in D: instead of C: won't matter to GRUB. AFter the install, when you boot into Ubuntu, open at terminal and enter "sudo update-grub" -- to regenerate the GRUB config file to add an entry for XP.

Good Luck
Hi Mark,
Thank you for your answers. I will give it a try tomorrow or over the weekend (its too late in the night here to try this now) and update this thread :)

Glad to be hopping on to the Ubuntu bandwagon :)

---

### Post by arvindx on 2013-02-01
Thanks Coldraven & Mark,

I have partitioned my windows drive, have successfully installed Ubuntu 12.04 LTS with a dual boot and updated it too :)

Minitool Partition wizard worked well; had installed it inside windows and ran it - it resized the drive during reboot (didnt use the boot cd option).

When my activex dependencies (work wise) are removed, I can move my games to Ubuntu and make it the single OS :)

Thanks for the help guys :)

---

