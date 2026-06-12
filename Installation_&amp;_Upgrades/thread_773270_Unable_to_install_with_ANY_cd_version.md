---
title: "Unable to install with ANY cd version"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by jimmyd850 on 2008-04-28
I've read as many forums as I can regarding the installation of Ubuntu but I have had no luck yet.

My pc is a scratch built AMD 64 Athlon 3000+
1GB RAM
2 ATA HDDs
1 SATA
Nvidia 6600 AGP

The graphical installs crashed around just before the point of when you can see the cursor (I saw it once) and the text based install crashes when it starts the partitioner. I have already created a partition where I want to install ubuntu but I can't get any further with it.

I'm sorry for the lack of information but any help would be much appreciated. I would love to try a new OS but I'm struggling already!

Thanks in advance!

---

### Post by Invader Amoto on 2008-04-28
I had seemingly random problems with installing ubuntu a while back. It turned out that burning the iso at too high speeds can corrupt the data. It happened to me 3 times in a row. Then I tried burning at 4X as someone recommended and it worked perfectly. Try reburning it at a low speed.

---

### Post by jimmyd850 on 2008-04-28
Thanks for the quick reply. I'll give it a go tomorrow morning and let you know what happens.

---

### Post by jimmyd850 on 2008-04-29
I'm afraid I've had no luck. I made the new CD at X4, the minimum my drive would do, and still it froze about 1.5 blocks from the end on the loading screen during the installation and live cd.

When I was fiddling about with the text based version it stalled at the point of finding a volume to install on, something about no volumes found?

Any help would be much appreciated!

---

### Post by Invader Amoto on 2008-05-02
hmmm... The text based installer saying theres no disk doesnt explain why the live cd didnt work. It doesnt need a hard drive to run. (or does it? somebody wanna correct me?)
Do you have windows your computer? If the hard drive works and windows can run, then it must be a problem with the installer, not your computer.

---

### Post by rholt on 2008-05-02
You have, as do I, a mix of SATA & IDE hard disks. 

It is not a good combination I have learned. Burning with DAO/SAO and as slow as possible is a good policy, but that is not my problem. 

I have had success installing by unplugging my IDE hard disk and only install 1 (one) Linux at a time on the SATA hard disk. 

Looking at getting a second SATA disk to get back to normal. Life was much easier with my old box with 2 IDE hard drives. Could put all kinds of linuxes. 

There are some references in this forum. Supposedly, after installing, I can reconnect the IDE drives and add the stanzas from their menu.lst, but I have not proved that as yet. 

It is a thorny problem. Apparently brought on by breakage in "legacy grub". Which apparently caught many by surprize. I have read that LILO is not affected and will work with a combination of IDE/SATA drives but I have not tried it. 

Best of luck. I'm still working on mine to see what happens when reconnecting the IDE drive.

---

