---
title: "installing 7.04 issue"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by rotalever on 2007-04-30
Hi,
I want to install Ubuntu 7.04 on my i386 machine. I downloaded the CD burned it and so on...
Now I am configuring my installation at must define the partitiontable, so ubuntu knows where to install. My HDD ist divided into several partitions. A  sudo fdisk -l /dev/hda gives:
```

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9726    78124063+   7  HPFS/NTFS
/dev/hda2            9727        9732       48195   83  Linux
/dev/hda3            9733       24260   116696160   83  Linux
/dev/hda4           24261       24321      489982+   5  Extended
/dev/hda5           24261       24321      489951   82  Linux swap / Solaris

```
But if I select "manual partitioning" in the installation manager it shows an empty harddisk with no partitions. How can I fix this?

Thanks in advance!

---

### Post by bulldog on 2007-04-30
Did you check the install cd on errors?

It's strange it sees your hda as  a fat16 file system,but it is not,so I expect an error in the install cd.

---

### Post by Sef on 2007-04-30
> Did you check the install cd on errors?

On the Ubuntu boot up menu, there is an option to check the disk for errors.    I had problem installing, and my md5sum was good, and the burn was good; however, the install failed.  Turned out I had a bad disk.  (Two actually.)  Once I used a different disk to burn to,  the install went fine.

---

### Post by rotalever on 2007-04-30
I googled around and read that this is an error of gparted which others also have. I am currently downloading the "alternate" CD which may include another installer.

I havnt checked my CD yet, but I guess it's correct :mrgreen: (brand new Verbatim CD-R burned at 20x speed)

---

### Post by bulldog on 2007-04-30
> **rotalever said:**
> I googled around and read that this is an error of gparted which others also have. I am currently downloading the "alternate" CD which may include another installer.

I havnt checked my CD yet, but I guess it's correct :mrgreen: (brand new Verbatim CD-R burned at 20x speed)

Yes that speed worries me :) 
It's a known issue when you burn to fast,the chances on errors increase rapidly.
Burn it slow 4x or 8x should do.
Takes a little more time,but in the end it's worth :guitar:

---

### Post by rotalever on 2007-04-30
I tested the CD with
md5sum -c md5sum.txt | grep -v 'OK$'
and it returns no errors.

---

### Post by mikesignguy on 2007-04-30
i had issues on two installs using the gparted on the live CD.  When i used the live CD from Gparted it worked flawlessly..... who knows

---

### Post by rotalever on 2007-04-30
> **mikesignguy said:**
> i had issues on two installs using the gparted on the live CD.  When i used the live CD from Gparted it worked flawlessly..... who knows
But on gparted's live CD is no Ubuntu installer.

---

### Post by bulldog on 2007-04-30
> **rotalever said:**
> But on gparted's live CD is no Ubuntu installer.

Nope,you're right about that :) 
There seems to be something wrong with your live cd partitioner,maybe you better use the alternate cd,I know I did,and had no issues.

---

### Post by rotalever on 2007-04-30
Now, I've also tried to use the alternate CD -> same error, the partitioning programm does not detect my partitions.

What can I do?

And yes, I checked the CD^^

---

### Post by bulldog on 2007-04-30
You can use the GParted live cd [55MB] and reformat the partitions if they are empty of course.
Otherwise I shouldn't know how to fix this.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by rotalever on 2007-04-30
Hmm they are not empty, but... Who needs windows anyway?:lolflag:

---

### Post by rotalever on 2007-04-30
I used another trick:
with fdisk:
I deleted the whole table and created a new one. Then I added all the partitions as they were before. Now it works... Seems to me that the MBR was a bit messed up by GRUB and WINXP.

---

### Post by bulldog on 2007-04-30
Well done :)  and thank you for telling,it's always frustrating when topic's have no good ending.:guitar:

---

### Post by rotalever on 2007-04-30
> **bulldog said:**
> ,it's always frustrating when topic's have no good ending.:guitar:
Yeah, same here! It is never good if people give up (to fast).

[Installation is now at 70%]

---

