---
title: "How to shrink an ntfs partition"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by AllBuntu on 2007-02-25
I have not seend a start-to-finish description of shrinking ntfs, so here is one

a. you need an Ubuntu desktop cd that you can boot from
b. a too big ntfs partition
c. an idea how much data is on that partition, and what size it should become
it could be good to backup using dd, partimage or ntfsclone before you start

[LIST=1]
[*]Boot from Ubuntu desktop CD
[*]Gnome > Applications > Accessories > Terminal
[*]sudo bash # get the # as the end of your prompt indicating root powers
[*]ntfsresize /dev/hda1 -s 26G # pick a value less than your final parition size, but large enough to hold your Windows data, size is bytes or suffixed by k, M, G, /dev/hda1 is the partition your are resizing. Don't live on the edge, have a GiB or so of margin
[*]Gnome > System > Quit > Restart
[*]Boot Windows for automatic chkdsk # this verified disk integrity
[*]Windows restarts by itself, launch Windows then immediately restart to Ubuntu # this enables the journal
[*]Boot from Ubuntu desktop CD
[*]Gnome > Applications > Accessories > Terminal
[*]sudo bash # get the # as the end of your prompt indicating root powers
[*]fdisk -u /dev/hda # -u indicates block sizes, /dev/hda is the device where your partition resides
[LIST=1]
[*]p # note your partition's boot (* for yes or no), start (large number, typically 63), and id (small hex number, typically 7)
[*]d, 1 # delete your partition (this is the number corresponding to your partition 1 for hda1)
[*]n, p, <same start>, desired last sector # re-create partition starting at same block but slightly smaller
[*]t, 1, <same id, 7> # put back your partition identifier
[*]w # write parition table to disk and quit
[/LIST]
[*]# now the hard disk has a different partition table than what kernel is using, so we want to reboot right away, if you stick around here, it will get weird
[*]Boot from Ubuntu desktop CD
[*]Gnome > Applications > Accessories > Terminal
[*]sudo bash # get the # as the end of your prompt indicating root powers
[*]fdisk -ul # list and verify that your patition data looks ok
[*]ntfsresize /dev/hda1 # adjust to the size of the partition
[*]Boot Windows for automatic chkdsk # this verified disk integrity
[*]Windows restarts by itself, launch Windows # this enables the journal
[/LIST]

Very easy,

Harald Rudell

---

### Post by Kateikyoushi on 2007-02-25
I would ask a mod to move it [here]("http://ubuntuforums.org/forumdisplay.php?f=100") or post a copy over there as well.

---

### Post by Azakus on 2007-02-25
For a GUI of this process, try GPartEd with ntfs-3g. It automates this process, and runs multiple simulations to check for possible errors before actually resizing the partition.

---

