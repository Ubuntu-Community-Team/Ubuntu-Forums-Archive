---
title: "Installation on dual laptop xp/fedora"
date: 2006-04-11
forum: Installation &amp; Upgrades
---

### Post by pi6502 on 2006-04-11
Hi,
I'd like to install Ubuntu _removing_ at the same time the fedora installation I have on my laptop. I already boot xp/fedora from grub.
When the installation process reaches partitioning, I see the following partitions and mount points:

#1 primary 24.5 GB ntfs bolt blacksmiley /media/hda1 as mount point
#2 primary 9.7 GB ext 3 blacksmiley /media/hda3 as mount point
#5 logical 1.1 GB swap aliensmiley swap
#2 primary 4.7 GB blacksmiley fat32 /media/hda2 (this is the ibm restore partition for the laptop)

Now how do I proceed to remove fedora and safely install Ubuntu? Shall I just format #2? Do I need to (re)define mount points? Can I keep the swap as it is (I presume it does not need formatting)?

Thanks in advance!:rolleyes:

---

### Post by Sef on 2006-04-11
First **Back up**  your files.

The easiest way that I know of is to delete the Linux partitions, except for/home and then reinstinall them. I do this during the install.

---

### Post by pi6502 on 2006-04-11
[QUOTE=Sef]First **Back up**  your files.

The easiest way that I know of is to delete the Linux partitions, except for/home and then reinstinall them. I do this during the install.[/QUOTE]

And how do you do this during install? Besides, I don't mind deleting all of my old stuff I have in fedora, so I could just delete the ext3 partition?

---

