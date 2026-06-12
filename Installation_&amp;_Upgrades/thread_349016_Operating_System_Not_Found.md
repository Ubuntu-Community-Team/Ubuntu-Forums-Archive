---
title: "Operating System Not Found"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by pignati on 2007-01-29
Greetings,

I am attempting to put ubuntu 6.10 on a fresh 20gb SeaGate hdd.

I can run ubuntu fine when running the live version off CD.  Everything goes without a hitch as I click the Install icon that brings up the 6 screen pre-install diagnosis (How nice it is to not run amuck looking for cd-key).

On the 6th screen, I am asked where to install GRUB - It originally selects hd0, and I said sure.  I then proceeded to install, noticing that the progress percentage numbers were all garbled up, but it finished without a hitch.

Rebooted, was told to take CD out of drive, did so, clicked enter when CD drive was closed, and bam - Operating System Not Found.

Why or the better question:  What am I doing wrong?

I appreciate your patience and time, here are my specs:
- 733Mhz Celeron
- 512DDR PC2700
- Onboard Video/Audio (Both work fine)
- 20GB SeaGate IDE hdd
- 40x Generic CD drive.

[edit] Perhaps I should also add the format type of the hdd:
- ubuntu root:  "/" partition 1 as ext3 (hd1)
- swap "swap" partition 5
[/edit]

Thanks,
- Sean

---

### Post by scrooge_74 on 2007-01-29
I see you have hd0 an later say hd1

I think you should try to install again since it seems Grub is pointing to the wrong place

your hardrive shoud be something like hda1 or hdb1 depending on how many drives you have or how many partitions

---

### Post by pignati on 2007-02-01
I apologize for the unneeded bump, however the problem has been resolved.

I tried hd0 and hd1 both on seperate installs with no luck.  So I swapped out the drive.  Turns out that did the trick - But now I need to trash the 20gb.

Many thanks for taking your time.

---

