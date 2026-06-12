---
title: "100GB disk image???"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by vcarbon on 2007-08-29
I just installed 7.04 (for the 5-6 time) by now I have figured out most of the tricks for my Dell latitude D820. I still haven't got the sound recording working but I haven't really tried yet. 

here is my question

I got Ubuntu configured the way I want it, including vmware running widows XP. and I want to make an image of my hard disk (100GB) and make new images about every week. in case i screw something up!

My configuration is that I installed Ubuntu on the full drive, only leaving the small partition at the beginning of the disk. I didn't know if I should erase it or not. I'm referring to the small boot partition.

It was 3am when I installed so I gave 10Gb to swap and the rest to the / mount point.

standard install.

i then installed vmware and made a 50Gb virtual machine.

Like I said I want to make an image of the full disk. I have a USB 500GB backup drive to store the images on but for now this is my only computer. I do have access to mac, windows and a 386 running Ubuntu at work and it may be possible to do the backup there.

Any suggestion will be helpful, I am new to linux, but I know my way around a computer pretty well.

---

### Post by kscott121 on 2007-08-30
Boot with a Livecd (System Rescue. maybe Trinity Rescue, or Puppy) and use the partimage utility to push across a image of your large partition.  It will take a good while but you can tell it to do no compression (since your backup drive is so big) and that'll make it faster.

Good Luckage!

---

### Post by wolfen69 on 2007-08-30
acronis true image (not free) is a great program for such a task. if you only have 8gb of data on a 100gb drive, it will only save 8gb of data that can be restored to any drive. and you can make incremental backups too.

---

### Post by vcarbon on 2007-08-30
Thanks for the tip, I am going to try systemrescue

If I make an image of the 90GB / partition, then resize my 10GB swap to say 500MB then restore the image to 99GB partition...will that work? is 500MB a good size for swap?

I have heard that you only need to backup you home directory...but it seems that you would have to reinstall all software for that to work, also I transferring most files (post installation) for install to /usr/local/src

---

### Post by kscott121 on 2007-08-31
partimage doesn't actually deal with partitions (as I understand it). It actually low level copies the filesystem inside the partition.   It's also not important how much is actually used at the time except the "backup" image will of course be smaller.  Thus if you backup a 20GB partition (10 GB in use) and then restore that to a  40GB partition (which you would have had to previously create) , the resultant filesystem will still only be 20GB - That is , the last 20 of the 40 total will be at first wasted.  If the the filesystem involved is ext2, ext3, or NTFS (I believe), not FAT then you can use the utility resize2fs to the resize(stretch)  the file system up to the full size of the partition.

As for swap the standard linux ROT (Rule of Thumb) is the swap partition should be 2x the RAM on the machine.   I guess you can use much more but I'm not sure of the pros/cons of that.

partimage moves the contents of partitions.  If your /home directory is part of the / "root" partition it will automatically be picked up with that partition.  If it is a separate partition you need to partimage that one separately.

Hope that helps.
Ken

---

