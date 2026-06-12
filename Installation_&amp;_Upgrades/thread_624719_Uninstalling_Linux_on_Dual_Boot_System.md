---
title: "Uninstalling Linux on Dual Boot System"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by weasel7711 on 2007-11-27
Ive read a few threads on this I just want to make sure my particular situation will work.
Here's my situation.
2 Hard disks
Windows XP is loaded onto the master C drive
Linux is loaded into the back 20gig partition of my D drive
I just bought a new Hard drive and I would like to copy both of my windows formatted data from both hard drives onto the new hard drive. However, the manufacturer of my CD case only included 2 sets of the plastic hard drive mounting rails for the 3 hard drive spaces and after contacting them and numerous computer supply companies I cannot get a hold of a 3rd set. So I can only have 2 hard drives in at a time. I was thinking of keeping the master C drive and putting in the new drive and cloning the C drive into the new drive. Then I was going to swap the C for the D drive and clone the data there (with all my music, pictures, etc) onto the new drive. THEN format the D drive and completely dedicate it to Linux with a fresh install.
The problem was when I had the C drive and the new drive in it wouldnt load anything because it couldnt find the GRUB loader because that is on the D drive. So will it matter if I load up the win XP cd recovery console and type in fixmbr with both the C and D drives in there? And what drive would i type in, the C or D drive?
Or is there something else I am missing?

---

### Post by cpmpal on 2007-11-27
wow that's a mouthfull.

But apparently it seems as though you have 2 hardrives
both of these have one partion on them with operating systems.
Then the one with linux shares all your files in conjunction.
your system currently only supports two hard drives
Now you want to pull all your windows onto the new drive.
Then dedicated the empty windows drive to linux a new install

Okay with that out of the way,
 are the files on the linux/other drive (D) mixed linux files and windows?
 i think this is what your saying and then say that is a geat idea to switch it over

the issue with fixmbr:
fixmbr can be specified to a drive in particular. **If** it isn't then it will write a master boot record to the windows os drive

what this can do is it would let windows run perfectly on its hard disk. here would be a great time to defrag only the windows drive
then run a chkdsk /P on it
get a copy of partion magic (might need to be paid for or not)
then use this to partion both drives ina loader so it will shw the linux os that is on the D drive witht the GRUB loader all in one nice linux os package.
then windows will be on the other drive as it was before with the inbetween files untouched and from here clone and swap and organize to your hearts content! :KS

---

### Post by weasel7711 on 2007-11-28
100 gigs of the D drive is partitioned for use with windows, the next 20 gigs is partitioned for linux with it installed on that 20 gig space

---

### Post by weasel7711 on 2007-11-29
I tried the fixmbr and it worked ok. Now I transferred everything over to the new drive and I will be reformatting the old D drive. What format is does Ubuntu use? FAT32?

---

### Post by Pumalite on 2007-11-29
Ext3

---

