---
title: "Installing Ubuntu - Partitioning Problem"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by Xylograph on 2007-12-01
Hello. 

I just tried installing Ubuntu 7.10 Gutsy Gibbon on my Compaq V5000 laptop (the LiveCD works perfectly - if a little slow).

However coming to install, I do not appear to have the options other people have in the partitioner.

As I would like to dual boot with XP, I was going to resize the XP partition, and create some for Ubuntu as instructed.

However, I do not have the option to Guided - Resize on the partition menu, only to Guided - Use entire disk , Guided - Use Free Space and Manual. Clicking Guided - Use Free Space creates an error saying I have only 8mb free space. However, I have about 30GB free space.

Any ideas about what I should do? or what the problem is?

---

### Post by bingoUV on 2007-12-01
Did you try manual? I think that is the one that allows us to edit partitions.

---

### Post by Pumalite on 2007-12-01
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2)

---

### Post by Xylograph on 2007-12-01
I was advised against manual.

Ive tried again, and its thrown up a load of other options, like Repartition with free space (which Im trying now) and Resize IDE1MASTER (which I tried but got a root error).

EDIT: I get the error NO ROOT FILESYSTEM DEFINED

QUOTE: [http://www.howtoforge.com/dual_boot_...untu_feisty_p2](http://www.howtoforge.com/dual_boot_...untu_feisty_p2)

I already have a pre existing XP partition, Im using 7.10 and I apparently only have 8MB of free space (I have 30GB in fact). Ive tried every option on the installer, and all give me that root error.

---

### Post by tinycamp on 2007-12-01
try this, boot with the livecd and:

```
sudo fdisk /dev/hda or sda or whatever is your hard drive
```

list your partition table, and post it here!

i think you resized but there is a logical partition defined.

---

### Post by Xylograph on 2007-12-01
I have not resized already. I have a 40GB harddisk with a 40GB Unknown Partition and 8mb free space, and do not seem to have the options everyone else has.

Even in manual, I get the root filesystem error.

---

### Post by tinycamp on 2007-12-01
the root filesystem error is because you are installing without saying where to....
and thats because there is no partition that can be "taken" and mounted as /  "root"

do this:

1) BACKUP ALL YOUR DATA FIRST

2) DO ANOTHER BACKUP

3) resize your windows partition

4) boot with the livecd, now you should be able to install just fine

5) remember BACKUP YOUR DATA, partition resizing is dangerous, always.

---

### Post by Xylograph on 2007-12-01
Ok, thanks. ill shut it down, resize in xp, and then boot the LiveCD and try again.

Ill post my results soon.

---

### Post by Xylograph on 2007-12-01
Hmm Still no luck. 

Trying Partition Logic as I type...

---

### Post by Pumalite on 2007-12-01
Better use Gparted Live CD.

---

### Post by Xylograph on 2007-12-01
I have a download limit, and this is only a few MB (Gparted is 51) , and as Gparted on the Ubuntu installation didnt work, Ill use this. Im currently burning its disc...

---

### Post by Xylograph on 2007-12-01
Aha!

It seems to be working.

I did a Chkdsk /f in Windows, rebooted with my Knoppix LiveCD I often use, and used Gnome Partitioning Tool on that too resize the windows partition to 18GB. 

Its currently still resizing. If that works, Ill try Ubuntu again tomorrow. If that doesnt work, I will have to try OpenSUSE (I got a disc free in LXF, with Ubuntu 7.10 as well), or maybe Fiesty Fawn.

---

