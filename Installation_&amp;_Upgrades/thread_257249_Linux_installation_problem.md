---
title: "Linux installation problem"
date: 2006-09-14
forum: Installation &amp; Upgrades
---

### Post by tmcahow on 2006-09-14
I am trying to install a version of linux onto my desktop specs:

AMD 64 3400 @ 240mHz
1.5Gb memory
1st hdd 160Mb
2nd hdd 300 Mb
Nvidia GeForce 5200
On board sound card is AC97
Windows XP running on first partition (100Mb) works like a champ (as much as i hate to say that).

History: Installed Suse 10.1 (Gnome desktop) and everything was working except router (D-link WBR-3210) to DSL modem. Could not get Suse to talk to modem through router.  And Suse kept randomly freeezing.  Then tried Kubuntu and everything installed and worked fine.  Then installed package for Amarok 1.4.3 and the Kubuntu no longer worked.  Moved on to Ubunutu.  First attempt Live-CD installed and worked.  Selected install script and started installation.  Install freezes at partioner.  Rebooted PC and used system tools to create partion before selecting install script.  Again intall freezes at partioner.  So I tried Suse 10.1 again.  Everything installed and hot reboot everything is fine.  However, after shutting down for cold reboot system.  When system returns the system freezes about 30 seconds after windows manager loads.  Loading in "safe" only takes me as far as the login and then freezes.  
So I know sounds like a hardware issue.  I have removed everything one by one and re-attempted this little game with the same results.  Additionally, I have disabled APIC in bios, and the sound card in bios, no luck.  So what I would really like is to ubuntu or kubuntu on my pc.  From what i have seen and been able to do, i like the interfaces.  

Anyone with suggestions...i tried to cover everything i have done, but honestly i have worn out the reset button on my pc and can not remember everything i have done.

---

### Post by tmcahow on 2006-09-14
So is this an example of not enough information?

---

### Post by kazuya on 2006-09-14
I would recommend you trying out Kubuntu again then as it worked fine before. I say this because you can install Kubuntu and then through Kubuntu install choose to install ubuntu-desktop, xubuntu-desktop, etc.

(1) Are you using dapper livecds or the older livecds?
(2) The dapper partitioning tool may be having difficulty with the fact that you already have four partitions., You may need some of those partitions to be extended. As normally max primary partitions is supposed to be 4.

You may need to take the linux ext3 partition and convert that to an extended partition first, from there you can create Swap> 512 MB, hdaX> for root 30 GB or higher, and hdaY> home partition the rest.

Sometimes when installing a pacage like amarok or so breaks something, you can go to synaptic and do "fix broken packages." It works sometimes. It is not typical or easy to break installation especially to just install amarok. Now for the bleeding edge amarok, there are special ways of installing from other repos, you also must ensure that you disable these repos from your sources.list or synaptic repo preferences after getting the package you want. 

Hope this helped somewhat. 

Kubuntu or Ubuntu 64 bit version may be optimal for drawing out your system potential, but the regular dapper would work as well without compatibility issues with 32 bit windows media components. This is why I am holding off on the 64 bit for now, and using i-686 images or kernel as this is fast and compatible with most new systems.

---

### Post by tmcahow on 2006-09-14
Kazuya,

Thank you for the reply.  I am using a dapper live cd.  This is my partion setup.  1st hdd primary partion 100Mb (windows) 2nd partion extended using 51Mb this is split into 7mb for swap and the rest for /.  This partion is reiserfs.  ANd unfortunatley after the amarok incident i could not even get into "safe" mode.  so i could not edit anything.  And currently I am not able to install Kubunut...so I am stuck...but i am going to try the 32 bit version...

would still like suggestions for getting the 64 bit version back on...

Tad

---

### Post by tmcahow on 2006-09-14
Ok...so the 32bit version does not boot at all...my frustration continues to mount.....

---

### Post by tmcahow on 2006-09-14
Apparently I reached the Dell help center...oh wait at least they say they can not help...and just like the operating systems I have tried to install this forum apparently also does not work...

---

### Post by tmcahow on 2006-09-15
Good to see this forum works as well as the software...i really dont want to seem bitter...but i just dont get all the hype for a product that windows beats...

---

### Post by tmcahow on 2006-09-16
Thanks to no one on this site...but i have solved my own problem...the problem is the 64 bit version of ubuntu...it, ubuntu does not work with the amd 64 bit processor...installing ubuntu after disabling APIC in the bios using the i386 version works....well wait a minute, it only works if you dont use any 64 bit programs...NOT A NOVICE...but thanks, wait never mind linux forums....

---

