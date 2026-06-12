---
title: "[SOLVED] Help me install please."
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by the badger on 2008-11-27
Hi! I am trying to install xubuntu to my older desktop (franken-puter). It was running hardy heron until I decided to embark on dual-booting. After a corrupted boot.ini file occurrence and the realisation that i really don't have time to deal with this right now, i figured i'd settle for reinstalling ubuntu - trying xubuntu this time around. i've been ubuntuing since dapper, but am still a n00b in many, many regards.

i've had it before (installing 7.10, i think) and i've got it now again: grub error (18 now, last time 22) because of my old computer. what i need is a nicely placed /boot partition, but it just doesn't seem to be happening for me. i've tried installing a number of times, and hopefully i'm not making everything even worse with my repeated attempts to overwrite the hd. here's what i did with the partition editor this last time 'round:

```

(drive)        (mount to)  (format?) (size)
\dev\sda1 ext3  \           +          50gb
\dev\sda6 ext3  \boot       +          100mb
free space                             28.xgb
\dev\sda5 swap                         1.5gb

```

i have also tried using the super grub disk...ineptly... but ran some diagnostic/'fix' tool successfully, however it didn't fix my grub error.

so as it stands, i can't boot into the os. i just get stuck at the black screen of 'Grub Error 18...'. i could not find a 'community doc'/'help file' that really laid it out for me in a way i was able to piece together. help is much appreciated - especially help with steps :)

---

### Post by mikewhatever on 2008-11-27
Can you boot from a live cd, doesn't matter which and post the output of the following command: 
**sudo fdisk -l**

---

### Post by the badger on 2008-11-27
sudo fdisk -l

[IMG]http://farm4.static.flickr.com/3067/3064199333_dc86dfd034_b.jpg[/IMG]

(is this okay/visible?)

---

### Post by the badger on 2008-11-27
fixed! phew! it's been days of tinkering with this. sometimes it just take posting up for things to fall in to place. sorry for taking up the forum space and then solving my own problem, but here's what i did that finally worked:

1. used the [GParted live cd]("http://gparted.sourceforge.net/") to erase all my partitions

2. booted up the xubuntu cd and reformatted the partitions.
[INDENT]   a) added a new 98mb ext3 partition mounted to '/boot' as a primary partition
   b) added a new 50gb ext3 partition mounted to '/' as a logical partition
   c) added a new 1.5gb swap partition (also logical)[/INDENT]
..and left the rest as 'free space'

so xubuntu is up and running... now to iron out the kinks ;P

---

