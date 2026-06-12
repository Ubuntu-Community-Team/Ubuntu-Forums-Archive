---
title: "[SOLVED] HELP!  Ubuntu partition is missing?!"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by LuckyDevil on 2007-08-14
I booted my machine up today and it went straight to windows (the 1st time it's been there in months as I don't have time to game).  I never see the grub menu, which was previously there..

It's a single serial hard drive...sda...partitioned as
    sda1 - windows
    sda2 - ubuntu /root
    sda3 - swap
   
All of a sudden, when I boot in I don't get grub access.  In windows it now shows the drive in computer management as all one partition (though it shows the size as the the partition size (17gig instead of 250 gig, the full drive).

I booted the live cd and went to a terminal to try

grub
root (hd0,1)

I get the error "Selected disk does not exist"

There's only one disk...it should be hd0, yes?  I've of course tried hd1, hd2, but same result

What's messed up here, why can i not see those partitions?

Any help?

Thanks a lot

---

### Post by merlinus on 2007-08-14
From a terminal using the live cd, what does this return:

```

sudo fdisk -l

```

-merlin

---

### Post by logos34 on 2007-08-14
> **LuckyDevil said:**
> 
I booted the live cd and went to a terminal to try

grub
root (hd0,1)

I get the error "Selected disk does not exist"

There's only one disk...it should be hd0, yes?  I've of course tried hd1, hd2, but same result

What's messed up here, why can i not see those partitions?


no, use 

**sudo grub**

otherwise you'll get the errors

Post your fdisk like Merlinus suggested and your menu.lst while you're at it.  If you're lucky a reinstall of grub will fix it.

---

### Post by LuckyDevil on 2007-08-15
Sorry, I forgot to post that...

fdisk -l

   Device   Boot    Start         End                       Blocks                    ID               System
/dev/sda1 *           1               30401                244196001              6               FAT16

Looks like partition table is all gone somehow... my ext3 and swap are gone?

EDIT - obviously, it's not all gone...what I meant was all incorrect, I guess. :-)

---

### Post by LuckyDevil on 2007-08-15
I can't post menu.lst as I can't get to it.  My partition table is wrong for that drive...it shows the whole drive as being fat16?  

Is there any way to recover?  I've tried the rescue command of parted, but it thinks it's all one partition.

---

### Post by LuckyDevil on 2007-08-15
Well, some encouraging news...the partitions are still there, I just can't restore them.

sudo parted /dev/sda

Guessed primary partition table
Primary Partition(1)
   type: 007(0X07)(OS/2 HPFS, NTFS, QNX, or Advanced Unix)
   size: 18002mb #s(3689104) s(63-3689166)

Primary Partition(2)
   type: 131(0x83)(Linux ext2 filesystem)
   size: 29996mb #s(61432560) s(3689175-98301734)



Try to recover those partitions using

sudo parted /dev/sda
(parted) unit s
(parted) rescue
start 63
end 3689166
(parted) rescue
start 3689175
end 9801734

There are no errors to these commands, but it doesn't restore the partitions, I still see one partition
(parted) print
Number       Start         End        Size       Type          File system          Flags
1                   32.3kB       250GB    250Gb   primary   ntfs                         boot


Any ideas how to restore this?

Thanks


EDIT - Allright, sorry for continously going on my own post here...I decided to just delete that incorrect partition
# sudo parted /dev/sda
# (parted) rm 1

Then make the correct partitions in it's place using the sectors from the gpart command...since restore didn't seem to be working
#(parted) mkpart primary
Used the start and end sectors...now all my primary partitions are restored.  I restored grub (sudo grub, root (hd0,1), setup (hd0) ) so I can boot back in.  Now I just need to get my extended partitions back, but I won't bother the forum with that as it's not important data, if I can't grab it it's no big deal.

Maybe someone else can learn from my silly post.  Maybe I'll learn to troubleshoot on my own a little more before posting :-)

---

