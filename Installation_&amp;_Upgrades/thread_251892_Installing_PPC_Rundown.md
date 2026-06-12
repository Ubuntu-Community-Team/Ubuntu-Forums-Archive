---
title: "Installing PPC Rundown"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by QwertyDitto on 2006-09-06
Well, i need a rundows on installign (and partitioning) an iBook G4 to run Mac OS and Ubuntu using YaBoot. ](*,)  I know DOS, like that would help... ;) anyway i need to find out more about the partitions... thanks.


I have everything ready... the cd's... the lot MY BRIAN DOEN"T NOW KNOW WHAT TO DO!!!:confused: :-k :-k :-k

---

### Post by linear on 2006-09-06
You may need to use the alternate installer. The Desktop CD installer fails on some G4 systems.

For starters, read these:

_[https://help.ubuntu.com/community/Installation/PowerPC](https://help.ubuntu.com/community/Installation/PowerPC) _(for Breezy, but still helpful)
[http://www.askdavetaylor.com/how_do_..._mac_os_x.html]("http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html")

This worked for me:

0. Read up in the PPC forums on any model specific quirks.
1. If you need to save the OS X partition, back it up. ([Carbon Copy Cloner]("http://www.bombich.com/software/ccc.html") works well.)
2. Repartition disk. Make two partitions, leave first as free space and second for OS X. Disk Utility is destructive (another reason for the back up), or there is a howto [here]("http://ubuntuforums.org/showthread.php?t=89960") on using **parted** to resize non-destructively.
3. Boot from the Ubuntu install disk. When you get to the partitioning step, tell the installer to use the largest free space. It will take care of the rest.

---

### Post by QwertyDitto on 2006-09-07
Thanks, so then it will to yaBoot and things automaticly? YAY INFO AT LAST :D :D 

Now to actually do this.. to verify... (i am a little nervious)

1. Backup data externally
2. Partition
3. Install MacOSX on the largest  (in this case 2nd one)
4. Install linux

THANKS \\:D/ \\:D/ \\:D/ \\:D/ \\:D/

---

### Post by linear on 2006-09-07
Yes, those are the steps.

---

### Post by QwertyDitto on 2006-09-07
Great \\:D/ 
So it installs YaBoot as part of it?

---

### Post by linear on 2006-09-07
Yes, yaboot gets installed.

---

### Post by QwertyDitto on 2006-09-08
Hey that rocks..... will do

---

