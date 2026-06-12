---
title: "[SOLVED] upgrading &amp;amp; partition problems"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by ZeroHimself on 2008-03-23
ok, here's my deal
I am currently running a dual boot  XP/Gutsy.......

xp is /dev/sda1
gutsy is /dev/sda2

I boot with grub....
i know that it is a bad idea to just move my gutsy to sda1

i hardly use my xp drive, and i would like to reduce the size to about 20 gigs(AFTER A FRESH INSTALL)

so my plan is to get the BETA of Hardy, and install that on sda1
get every thing from my gutsy install working....
repartition sda1 to a larger size
wipe gutsy, and then reinstall XP....

I have a hunch, that when i wipe my sd1, i will lose grub.... which would make my system difficult to boot....

further more, after i get everything working, and install XP, it will remove grub again....

any ideas/suggestions?

---

### Post by bigredradio on 2008-03-24
May not be what you want but.... Start over with Hardy. Then install XP inside VMware or other virtualization solution. Since you do not use it often, keep it in a VM. 

BTW, when you install Hardy, use LVM and create multiple filesystems ( / /usr /var /home, etc). /boot will have to be partition based. Then create the filesystems on Logical Volumes only as large as you need. Then if you need more space, just use the LVM/filesystem tools to grow the filesystem. Then you can use the disk space most efficiently. I keep reading about users with everything in one big / partition and I begin to wonder if this is a windows or linux forum. :)

---

### Post by jken146 on 2008-03-24
Back up your valuable files, then start from scratch.  That will be easiest.  Windows on first is the easiest way, but you can always reinstall GRUB from a live CD.

---

### Post by ZeroHimself on 2008-03-25
ok... but my problem, is that i have a (wonderfully) working copy of gutsy on sda2...., i would like to keep it running until i verify that Hardy works(and i get all of my stuff to work...)

hmm, if i just look at my grub settings, and note them, i could remove windows, install hardy and still boot gutsy from a cd right?

---

### Post by zvacet on 2008-03-26
>  but my problem, is that i have a (wonderfully) working copy of gutsy on sda2

Don´t touch it then.And if you install Hardy on windows partition you will be able to boot in Gutsy by choosing that from grub screen.In other words,Hardy will not remove your Gutsy entries.

---

### Post by ZeroHimself on 2008-03-26
but, when i remove windows(to install hardy...) it will remove grub??? oh, well, i looked at my grub settings, and they look straight foward enough, i am going to write them down, and install hardy this week.... then, i will rewrite my grub file(so i can still boot gutsy).....

then i will get hardy working right....(hopefully), and running all of my actually used stuff....

but then comes the part i'm worried about.... installing vista(!! try #30....), and i know that if it even lets me install over hda2, it will try to take my bootsector hostage...., and i will have to reinstall grub...(this is the part that worries me

---

### Post by ZeroHimself on 2008-03-31
Well, i did it and it's over.... I wrote down my grub settings and installed hardy(amd64)....

First 64-bit OS!!!:guitar:

Any how, it made the whole procedure almost painless

biggest setback:
had to delete 1st partition(ntfs) and recreate it as ext3 before i could use it as "/"

next, i made a new swap part, and i had to remove it from /etc/fstab

BTW 64-bit works great..(a few issues, but no more than gutsy-32 had)
and hardy w/ 64  is about 2x faster....

next week, i think i will disable(or remove) my hard drives, and plug in a usb for the windows-gaming partition ;-)

---

