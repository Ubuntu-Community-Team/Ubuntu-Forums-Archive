---
title: "Partition unusable - dual boot system"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by daviddesancho on 2007-07-29
Hi all:
I have a dual boot system, with Windows XP and Ubuntu 7.04. I had installed the 32 bit version but I want to upgrade now to the 64bit that corresponds to my intel core 2duo processor.
I have used the live cd and tried to erase existing linux partitions to create new ones. I've followed some instructions that I found about partition sizes in [http://tuxecutor.programasfull.com/instalar-ubuntu-704-para-principiantes.html](http://tuxecutor.programasfull.com/instalar-ubuntu-704-para-principiantes.html).
Following partitions are suggested:
· Root: Type: primary - 8.5GB - Mount point: / - Use as: ext3
· Home: Type: logical - 20000GB (or more) - Mount point: /home - Use as: ext3
· Swap: Type: logical - 2*RAM (8GB in my case) - Use as: swap
I tried to do this several times, but when the moment comes to create the last partition I always find that remaining space has been labelled "unusable".
Can anybody help me with this? I admit I am growingly worried.
Thanx so much,

d.

---

### Post by logos34 on 2007-07-29
you can only have 4 primary partitions on a disk--maybe there is a manufacturer utility partition or recovery partition in addition to windows?  If so, you can't create a fifth partition--make an extended partition and put /swap and maybe even /home inside as logicals.

Type in a terminal:
[B]
sudo fdisk -l[/B]

post it.  

1 GB swap is more than adequate.

---

### Post by daviddesancho on 2007-07-29
Yes, you are right about the fourth partition. It's some kind of utility thing that DELL puts in its computers (Optiplex 745, by the way).
The problem with creating an ext3 partition that would contain the logical and swap is that I think that the partition program of the live CD doesn't allow you to create the logical partitions inside the ext3 one.

Now, the output of typing "sudo fdisk -l /dev/sda/" is:
     Device   Boot       Start     End       Blocks      Id          System
/dev/sda1                     1         7         56196    de      Dell utility
/dev/sda2        *           8  10735    86172660     7    HPFS/NTFS
/dev/sda3             10736   18517   62508915    83            Linux
/dev/sda4             18518   19452   7510387+     5       Extended
/dev/sda5             19092   19452     2899701    82   Linux swap/Solaris  
/dev/sda6         *  18518   18783     2136852    83            Linux

Thanks again

---

### Post by daviddesancho on 2007-07-29
One more thing. There's another thing in the output of fdisk that I did not post:

Partition table entries are not in disk order.

Is it any bad?

---

### Post by logos34 on 2007-07-29
> I think that the partition program of the live CD doesn't allow you to create the logical partitions inside the ext3 one.

actually I think it does allow it, but I could be wrong (with the number of times I've run installs you'd think i'd remember but my memory just goes on the blink for some reason).  Try it again, create / (root) right after windows, then create the ext3 extended partition, then a swap and home as logical partitions.

---

### Post by daviddesancho on 2007-07-29
But where do I mount the ext3 partition? Just as media/sda4? And how can I create those two partitions (home and swap) inside that one?
Thanx

---

### Post by logos34 on 2007-07-29
just use gparted on the livecd to wipe out all your linux partitions.  Create /, then create the extended out of the remaining empty disk space, putting swap and home inside.  The extended will named sda4.

---

### Post by daviddesancho on 2007-07-29
I tell you what I've done.
1 - Delete all linux partitions
2 - Create root partition with 8.5 GB
3 - Create ext3 partition (primary, mount point: /media/sda4, automatically asigned /dev/sda5).
Then, all the room in my disc is occupied, and I cannot create the two logical partitions inside the new ext3. The only choice that you get is edit the partition and you can reassign it for swap, for example, or home, but not for both.
Maybe there's an option later in the installation process to set the two logical partition locations. Shall I just create ext3 and go ahead with it? I'm a little bit frightened.
Once more, thanx for your help

---

### Post by logos34 on 2007-07-29
you can do it if you use gparted (system>admin> gnome partition editor). Go back and do that then run throught the install steps.

---

### Post by daviddesancho on 2007-07-30
I'm using the Gparted Live CD to create all the partitions that I am going to need, both primary and virtual. In fact what I am doing is resize the partitions that I already had in my hard disk drive.
After that I will use Ubuntu LiveCD (64 bit) to reinstall the OS in those partitions: Is that right?

---

### Post by logos34 on 2007-07-30
sure, you can do it that way

---

