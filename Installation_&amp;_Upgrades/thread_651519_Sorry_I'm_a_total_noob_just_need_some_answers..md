---
title: "Sorry I'm a total noob just need some answers."
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by Bandolin on 2007-12-27
I d/l the .iso and burned it to CD

I ran the live session and I love the distro (woohoo, I'm already using the lingo).

I want to install but I'm a little gun shy and I can't seem to pull the trigger on this.

I have XP installed and I've read I can dual boot, but during the installation process it is asking me to partition the drive that XP is already installed on and I'm afraid to lose my XP installation.

My system:
3.0 GHz P4
1.5 Gb Ram
C: = 80 Gb w/24.5 Gb of free space
D: = 14 Gb partition of C:
E: = 200 Gb

I'd like to be able to put ubuntu on the already partioned D but I can't see to find a way to do it.

Just need a little hand holding and someone to tell me everything will be alright.

---

### Post by Pumalite on 2007-12-27
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it, choose the 14 GB partition and format it ext3 so you will not get lost later. Install Ubuntu, go Manual, choose that partition and do the following:
7 GB for '/'
1 GB for /swap
The rest for /home

---

### Post by Bandolin on 2007-12-27
Thanks for the quick reply. I'll try that and let you know how successful (or how badly I screwed up your simple instruction) I was.

---

### Post by Pumalite on 2007-12-27
You'll do fine. Good luck.

---

### Post by Bandolin on 2007-12-27
OK, here we go. Baby steps, so apologies again.

Problem: I get the following once booted in Gported

/dev/hda/   ntfs   WinXP   74.52 GiB
unallocated                       7.84 MiB

Doesn't seem to be able to find this D partition I've got. I've uploaded a pic so you can see I'm not crazy. Now, I believe this partition was created using Acronis True Image. I've tried deleting but Windows won't let me. Eventhough I've gotten rid of everything on it, it won't let me format it using Norton Partition Magic.

Anyone with any clues?

Now the E drive you see there is my 200 Gb HD. I looked in Gparted if by chance the D was a partition of the E but nothing there either.

Hmmm, but the more I think about it, the more I believe that this D partition is part of the 200 Mb drive and not the 80 Gb drive. So, will repartioning the C destroy any data? And no I don't have place to backup 50 some odd Gigs of data.

---

### Post by Pumalite on 2007-12-27
Boot from Gparted Live CD, right click on the XP partition, choose 'resize' from the menu. In the new partition, a good scheme is:
10 GB for '/'
1 GB for /swap
The rest for /home
(adjust according to your possibilities)
Then install Ubuntu, go Manual and use the partitions already created.

---

