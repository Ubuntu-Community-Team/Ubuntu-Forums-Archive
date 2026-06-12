---
title: "Partitions not detected outside of Lucid"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by tjk on 2010-07-17
I have asked for help on other forums regarding my problem, with no results... hopefully someone here can help.

About a month ago I did a clean install of Kubuntu Lucid.  I believe it was after that point I was unable to run other LiveCDs without some problems -- I first noticed that swap partitions failed or weren't detected.  It appears that partition managers such as gparted, fdisk, etc cannot detect my partitions and interprets my hard drive as "unallocated" (this has been tested with multiple LiveCDs).  However, as far as I can determine, all the LiveCDs with applications for mounting drives and HD backup ARE able to detect the partitions.  Furthermore, when I am in Lucid, I am able to detect the partitions with gparted.

It's very odd... I've only found a few situations like this on the web.  Could it have something to do with the GPT? ([http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)) -- I really don't understand this stuff.

---

### Post by gordintoronto on 2010-07-17
Did you partition the disk with GPT fdisk? Sounds like a dangerous way to go.

---

### Post by tjk on 2010-07-17
> **gordintoronto said:**
> Did you partition the disk with GPT fdisk? Sounds like a dangerous way to go.

Not that I know of... I just used the partition manager that Kubuntu uses with the LiveCD install.  I know nothing about GPT, so I wouldn't know if that is used in the Kubuntu install.

---

### Post by bumanie on 2010-07-17
Don't believe that kubuntu uses GPT - Hmm...can you boot a live cd and post the output of > sudo fdisk -l interesting to see if the command line shows the partitions or not.
**That is a lower case L, not the digit one.

---

### Post by tjk on 2010-07-18
[INDENT][INDENT]> **bumanie said:**
> Don't believe that kubuntu uses GPT - Hmm...can you boot a live cd and post the output of  interesting to see if the command line shows the partitions or not.
**That is a lower case L, not the digit one.

Here's what I get:

Disk /dev/sda: 250.9 GB, 250999111168 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         184     1477948+  83  Linux
/dev/sda2           12986       29809   135138780   83  Linux
/dev/sda3           30258       30516     2077148   82  Linux swap / Solaris
/dev/sda4             185       12985   102819461+   5  Extended
/dev/sda5             185        3832    29296875   83  Linux
/dev/sda6            3832       12985    73522176   83  Linux
[/INDENT][/INDENT]

---

### Post by dino99 on 2010-07-18
its good to know what the errors are: boot on a live cd or usb stick and then check the partitions:

fsck -n /dev/sdax  (where x is 1, 2, 5, 6, no need to check swap)

to repair:

fsck -y /dev/sdax

---

### Post by tjk on 2010-07-18
> **dino99 said:**
> its good to know what the errors are: boot on a live cd or usb stick and then check the partitions:

fsck -n /dev/sdax  (where x is 1, 2, 5, 6, no need to check swap)

to repair:

fsck -y /dev/sdax
Thanks dino99 for responding.  

I have tried many different LiveCDs and am finding it hard to get to a command line (esp where a mounted partition is not needed) or get the fsck command recognized.  I finally got a GParted LiveCD to work, but it's output said something like: "superblock could not be read or does not describe a correct ext2...".

Do I need a very recent LiveCD to work with the ext4 format, or will all fsck commands work with this format (even though it refers to ext2)?  

And with the given error message (as above), should I try the fsck -y command?

---

### Post by tjk on 2010-07-20
Can anyone help out here, please?

I'm still wondering if I may have inadvertently changed to a GPT system?  Is there a way that I can determine this?  I'm even having trouble backing up the partition table... I don't have a clue what's going on.

---

