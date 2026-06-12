---
title: "Manual partition help"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by cupps on 2008-04-09
Long-time lurker, and several-time Ubuntu user here. I recently built a new desktop for myself, and began with Windows XP, but with 8.04 on the horizon, I'm making the move back to Ubuntu. However, most times I've installed Ubuntu, I've only had one hard drive, and I've typically let the installer automatically divvy up the free space (be it the whole thing or the pieces not used by XP).

This time around, however, I'm reaplcing XP entirely and doing so with two hard drives. When I began the installer, the two automatic options were either installing completely on one hard drive (not both) or installing in the unused space from Windows XP. I want to use all the space from both hard drives, however, for Ubuntu.

Anyways, long story-short, I wanted to know what the basic setup for partitions for a Linux installation is. I know I typical make the partitions in ext3, and I know I need one swap partition. But I'm using two 250GB hard drives, and I wanted to know how I should split up that space for the Ubuntu installation.

Thanks in advance for any help.

---

### Post by mikewhatever on 2008-04-09
Check this out [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning).

---

### Post by tamoneya on 2008-04-09
what i would do is select the use remaining space on windows drive option during the install.  Then after it is all installed I would format and mount the second drive to /home.  This is because most of my files (video, music, pictures) will reside in /home and this is where I need the most space.  This drive should be added to /etc/fstab so that it mounts when the system boots.

---

### Post by cupps on 2008-04-09
Thanks, that helps out quite a bit actually. I was having horrendous luck with Google, heh.

Although, it mentions that two hard drives are essentially two pre-defined partitions. In that case, if I partition the first hard drive with SWAP, EXT3 (/) and EXT3 (/home), what do I do with the second? I mean... what should I partition that as... since I want to use all may space for Ubuntu?

Sorry for seeming thick about this.

---

### Post by manosagn on 2008-04-09
You can use a lot of space for your system: /root, /usr as well as swap, resulting in less than than 200GB for /home. (maybe you become really greedy for your system and manage somehow to get a /home less than 100GB).

Then mount the second drive as (say) /media/local_home or /media/stuff and use it for larger files and/or less important data.

I have a /home where I keep files like essays, code and important libraries for development, interesting pdfs and e-books on home. At the same time, I keep my music, avis, and every possible "useless" information on such a "/media/stuff" directory. In that way you don't mix important stuff with your music and/or torrent data files or similar files.

On the other hand, have you considered a raid?

---

### Post by mikewhatever on 2008-04-09
> **cupps said:**
> Thanks, that helps out quite a bit actually. I was having horrendous luck with Google, heh.

Although, it mentions that two hard drives are essentially two pre-defined partitions. In that case, if I partition the first hard drive with SWAP, EXT3 (/) and EXT3 (/home), what do I do with the second? I mean... what should I partition that as... since I want to use all may space for Ubuntu?

Sorry for seeming thick about this.

Use it for backup and storage, Ubuntu itself does not need so much space. You can turn it into one big ext3 partition or several ones, it does not matter.

---

### Post by LeoSolaris on 2008-04-09
My two cents worth...

Since you're committed to Ubuntu, I would suggest setting a 20g partition for your / and filling the rest of the hard drive it's on with /home (plus the customary couple of g's for swap)

The second hard drive would be just like it would show up in windows, a second large partition with basically nothing in it.

You may want to leave a small slice of Windows on there, since you already paid for it. Besides, if something catastrophic goes wrong with your Ubuntu, it's nice to not have to go hunting for a Live CD to get to the forums for help. (Or you could install a second Linux distro for that purpose.)

Leo

---

