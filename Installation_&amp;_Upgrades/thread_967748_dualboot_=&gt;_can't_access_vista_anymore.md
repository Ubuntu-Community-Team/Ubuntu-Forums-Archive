---
title: "dualboot =&gt; can't access vista anymore"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by Chielus on 2008-11-02
let me explain the history:

at first i had vista delivered. later on i made a dualboot with ubuntu 8.0 desktop x64

that went fine, i had a 10 GB ext3 for linux, and a 8 GB ext3 for my /home, and a swap area of 2 gig

so i had still a 340 GB partition of vista

a year later my vista crashed, so i had to reinstall.. because i reinstalled it, i lost the dualboot.. today (a few months later) i decided to get back my dualboot so i downloaded the live cd (8.10 ubuntu-desktop x64).. at my installation i couldn't see the 2 ext3 partitions of the past anymore.. but ok, i made 2 new partitions with the same settings as in the past

now i want my dualboot back, but i can't find the location of vista anymore.. it isn't in /media and if i use fdsik -l, this is the answer:

```
chielus@chielus-ubuntu:~$ sudo fdisk -l
[sudo] password for chielus: 

Disk /dev/sda: 360.0 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc37cb588

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        2797    12699382+   5  Extended
/dev/sda5            1217        2432     9767488+  83  Linux
/dev/sda6            2433        2797     2931831   82  Linux swap / Solaris
```

i tried all sort of things in my menu.lst, currently this is added at the end of the file:

```
title         Windows Vista
root         (hd0,1)
chainloader      +1
savedefault
makeactive
```

what's the problem?

i hope i didn't lost my vista partition

when i try to to use boot recovery with the vista cd, it doesn't see any partitions.. :s

EDIT: i think i know the problem.. i forgot to make a new partition in vista, and with that partition i had to install linux.. right? forgotten.. so now the 340 gig isn't used.. any way to solve this without reinstalling vista and losing everything? and if no.. i miss some important files in my backups, but i think they aren't deleted, they still are somewhere in that 340 gig unused filespace.. how can i get them back?

---

### Post by taurus on 2008-11-02
You don't happen to wipe out your vista when you reinstalled Ubuntu?  What's the output of this command from a terminal?

```
df -h
```

---

### Post by Chielus on 2008-11-02
chielus@chielus-ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9,2G  2,3G  6,5G  26% /
tmpfs                 942M     0  942M   0% /lib/init/rw
varrun                942M  100K  942M   1% /var/run
varlock               942M     0  942M   0% /var/lock
udev                  942M  3,0M  939M   1% /dev
tmpfs                 942M  108K  942M   1% /dev/shm
lrm                   942M  2,4M  940M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda5             9,2G  218M  8,5G   3% /home

so the c: disk from vista is gone i see.. but normally, it isn't formatted, right? how can i get back my files? do i have to use file recovery tools (which i don't like that much) or is there a simple way?

---

### Post by Chielus on 2008-11-04
can anybody help me with this last question

---

### Post by taurus on 2008-11-04
Is it the whole output from "sudo fdisk -l" because you are missing a bunch of space on /dev/sda?

```

Disk /dev/sda: 360.0 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc37cb588

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        2797    12699382+   5  Extended
/dev/sda5            1217        2432     9767488+  83  Linux
/dev/sda6            2433        2797     2931831   82  Linux swap / Solaris

```
And by the way, once you format the partition that windows is on, you probably need a professional to recover the data on that partition.

---

### Post by dbryant32 on 2008-11-04
Seems to me Vista got nuked.
There should be something similar to this in fdisk output
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26127   209864103+   7  HPFS/NTFS

---

### Post by Chielus on 2008-11-04
indeed, there's much of non-used space

that's because when i installed ubuntu i choose to use sda, and i made 2 partitions, each of 10 gig.. so that i have 340 gig left (which i thought that was for vista, but i'm wrong, that's simply unused space and i've lost c: of vista)

so is there any solutions to just find these files back, because it isn't formatted (i think), only set to "unuse"

if there's no simple solution to this, i'll try installing vista and recover the files with GetDataBank (i hope this program will find the files i need)

what do you think?

---

### Post by Chielus on 2008-11-06
bump (sry if this isn't allowed)

---

### Post by Mark Phelps on 2008-11-06
You appeared to have overwritten your Vista installation entirely because there are no NTFS partitions shown in the drive list.

GetDataBack, like other data recovery products, find files by recognizing what file headers look like; it doesn't actually use the file system information.  Thus, you might actually be able to use it to recover some of your overwritten data.  But your success will vary depending on how much got overwritten.

You will have to completely reinstall Vista (if you want it back).  Hope you have a Vista DVD or a recovery disk to do that from, because if all you had was a recovery partition on your hard drive, that's no longer there.

---

### Post by Chielus on 2008-11-07
yes, i have a vista DVD.. i will install it and try GetDataBank

i've heard this is the best recovery program, is this true?

i hope i'll find these files, or else i have 2 days of work lost..

---

