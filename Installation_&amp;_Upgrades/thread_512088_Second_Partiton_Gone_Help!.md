---
title: "Second Partiton Gone?? Help!"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by amorac on 2007-07-28
Long time ago i partitioned my 80g HD (via XP) into 2 partitions (80% / 20%).
My second drive acted as my gaming drive and backup drive. So if windows would to crash (surprise) Iwould not have to keep doing upgrdades on my games and/or loose my back up.
 
I found Ubuntu. LOVE IT!! My escape to dump XP. Yeah!!!
after experimenting with  Ubuntu on a second partition (not my game drive - according to the install i used the "FREE SPACE guided") I found that it did everyting that I needed it to (and my window based game worked flawlessly). So I reinstalled Ubunto utilizing the whole drive (didnt need windows anymore).

Problem.. everything went well.

but....

I cannot find my Game drive. Which is bad because, my important documents were stored on that secondary partition.

my 80g drive shows 63g free space which is about right because my other partition was done at 20g.

Question: Where is my secondary drive? is it gone? if not how can i mount it. i REALLY need those documents!! (NOT to mention the game backed up there will take a ton of time to reload)

I followed some of the suggestions here 
fdisk -l revealed nothing but what I already know.

Thank you inadvance for any help on this winded problem.

---

### Post by Pumalite on 2007-07-28
Check /media/disk. Also post your /etc/fstab

---

### Post by amorac on 2007-07-28
> **Pumalite said:**
> Check /media/disk. Also post your /etc/fstab

hi
thanks for the fast reply...

fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=e3d862db-fa56-4201-b5fe-36a8d04636bd /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=72e48e1a-09d6-412a-a742-d5ba7f7a62a3 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

media/disk 

cdrom
cdrom0
floppy
floppy0

thats all..

---

### Post by amorac on 2007-07-28
> **Pumalite said:**
> Check /media/disk. Also post your /etc/fstab

o and here was the fdisk -l output:


   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9352    75119908+  83  Linux
/dev/hda2            9353        9729     3028252+   5  Extended
/dev/hda5            9353        9729     3028221   82  Linux swap / Solaris

this makes me nervous because there is no NTFS drive shown.

---

### Post by Pumalite on 2007-07-28
Try this: sudo mkdir /mnt/hda3
sudo mount -t ntfs /dev/hda3 /mnt/hda3
(replace ntfs for fat32 if that's what it is)
See what happens and report back.

---

### Post by merlinus on 2007-07-28
IIRC, logical partitions begin with 5 and go on up.

1 to 4 is reserved for primary partitions.

Since 2 is extended, then the logicals begin with 5.

And unfortunately it looks like /swap wiped out the ntfs partition, judging from the beginning and ending blocks listed in fdisk -l.

-merlin

---

### Post by amorac on 2007-07-28
> **Pumalite said:**
> Try this: sudo mkdir /mnt/hda3
sudo mount -t ntfs /dev/hda3 /mnt/hda3
(replace ntfs for fat32 if that's what it is)
See what happens and report back.

mount: special device /dev/hda3 does not exist

---

### Post by amorac on 2007-07-28
> **merlinus said:**
> IIRC, logical partitions begin with 5 and go on up.

1 to 4 is reserved for primary partitions.

Since 2 is extended, then the logicals begin with 5.

And unfortunately it looks like /swap wiped out the ntfs partition, judging from the beginning and ending blocks listed in fdisk -l.

-merlin


i actually think your correct. however i am puzzled
hda2 and hda5 take up over 60gig

where is my other 20gig? would that not be the missing partition (size is about right)

---

### Post by meierfra on 2007-07-28
> So I reinstalled Ubunto utilizing the whole drive (didnt need windows anymore).

Sorry to tell you, but  if  you tell Ubuntu to use the whole drive, it will reformat your whole hard drive.

Your mistakes was that your didn't not distinguish between "drive" and "partition".
When ubuntu talks about drives it means whole hard drives.  The separate parts of a hard drive are  called partitions. 

Your fstab also says, that your back-up partition is gone.

---

### Post by amorac on 2007-07-28
> **meierfra said:**
> Sorry to tell you, but  if  you tell Ubuntu to use the whole drive, it will reformat your whole hard drive.

Your mistakes was that your didn't not distinguish between "drive" and "partition".
When ubuntu talks about drives it means whole hard drives.  The separate parts of a hard drive are  called partitions. 

Your fstab also says, that your back-up partition is gone.

well im a noob with linux (sigh...)

ok kinda figured that..  according to fdisk, only 60+gig is used where is the other 20?

---

### Post by merlinus on 2007-07-28
```

df -h

```

will show usage.

-merlin

---

### Post by meierfra on 2007-07-28
> hda2 and hda5 take up over 60gig

???????

According to your fstab:

hda1:            75,119,908   bytes

 hda5 :              3,028,221   bytes

total  about:  78 G 

(hda 2 is an extended partition and does not contribute to the total)

---

### Post by amorac on 2007-07-28
> **meierfra said:**
> ???????

According to your fstab:

hda1:            75,119,908   bytes

 hda5 :              3,028,221   bytes

total  about:  78 G 

(hda 2 is an extended partition and does not contribute to the total)

ok... 
that prob explains it. 
small price to move out of windows... i have most backed up online..
thank you all for your help...

and those of you reading for installation.. use the advance so you can distinguish between partition and drive (i got mixed up because windows does not, if i format my c part. d part is not affected.)

---

