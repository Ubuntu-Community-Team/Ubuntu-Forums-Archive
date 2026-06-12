---
title: "Sony VAIO: /boot/grub is not readable by GRUB on boot"
date: 2013-09-12
forum: Installation &amp; Upgrades
---

### Post by fruitz on 2013-09-12
Hi All,
I'm the unluky owner of a sony vaio, I spent a lot of time to install ubuntu on my machine some months ago, but it eventually worked out fine thanks to [darkod's help]("http://ubuntuforums.org/showthread.php?t=2107483&page=2").
Lately i had a broblem with my system and decided to go for a full clean up, I was sure I could reference to the same thread for the installation.
I was wrong, I'm still stuck with my unusable machine. I'm using boot repair, but when i get to install GRUB, I tried on every single device listed but the error is always the same

```
Path `/boot/grub' is not readable by GRUB on boot. Installation is Impossible
```

[here]("http://paste.ubuntu.com/6096941/")'s the pastebin of boot repair.

I hope someone could help me again with this.

PS. Please let me know if i should continue in the old thread instead of opening a new one

---

### Post by oldfred on 2013-09-12
Issues may be different so best to have new thread.

But I do not know RAID. Boot-Repair seems to have issues as RAID is already mounted. Did you mount it before running Boot-Repair?

Darko mentioned separate /boot outside of RAID, I do not see that?

Why RAID? Most desktops do not use it.
       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

---

### Post by fruitz on 2013-09-12
I dont think i mounted (at least I wasn't explicitly willing to) anything.
I ran the installer, left the grub installation on sda, selected md0 for /boot, md1 for /, and md2 for /home.

Since previously I managed to install the system, and had it runnign for 9 months, I think in RAID, it was nice. I mean, I can't really tell if there's a performance difference, but if there is, well, it's nice to take advantage of the 2 disks. 
And I actually wonder, when i run the installation, if i decide not to setup the RAID, how to i manage the disks? It seems like I have 2 disks 128 GB each, how do I manage the partitioning? if how can i have /home to be on 2 different disks (with same mount point)?

---

### Post by Quackers on 2013-09-12
If it's anything like my Vaio (an AR51SU) raid0 is just not worth it. I disabled mine in the bios (in fact that was just about the only thing I could do in Sony's bios!) and then re-installed both Windows and Ubuntu.
Raid0 complicates everything massively and the performance gain is questionable at best - if there is any at all. I didn't notice any difference.

Disc management is easier without raid. Stop thinking about the drives being connected and just regard them as two completely seperate storage devices. Two computers even. You can have what you want, where you want it with one proviso.
On my Vaio I could not choose the second hard drive as a boot device so all bootloaders had to go on /dev/sda - the first drive. Not a major problem though.


EDIT if you go down this route you should first make the Vaio recovery discs! Just in case. They will work with or without raid (as does the recovery option on the hidden partition).

---

