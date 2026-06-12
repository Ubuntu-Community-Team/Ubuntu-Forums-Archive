---
title: "messing up with partitions..."
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by cespinal on 2008-05-13
So... I wanted to expand my 533 MB swap partition up to 6Gb
1) I got into Gparted, and it would not let me do it since the four existing partitions fill up the entire disc. 
2) I loaded into Vista and ran the partitioner, and tried to shrink the vista partition, which actually did, leaving out a 17Gb partition called "Unallocated" which is totally dead and I dont know to to fix/revert it. My intention was to use that space to expand the swap partition without actually knowing if that was possible anyway. 
3) Now I dont know go to make Gparted make that unallocated thing usefull and be able to expand my swap partition. 

Can you help me out on this? :confused::confused::confused:

---

### Post by Rallg on 2008-05-13
Unless you did something exotic, the problem is not hard to fix.

In GParted, simply choose to resize/move the linux-swap partition. You will still have some extra unallocated space left. If you wish, make a new partition there.

Some possible problems:

(1) When you resize or move a patition, its UUID may be automatically changed. GParted does not tell you the value. From Terminal, use

ls -l /dev/disk/by-uuid

to get a list of UUID values. You may have to manually edit your /boot/grub/menu.lst file if any UUID changes.

(2) GParted allows you to "label" a partition. Don't do it! That function does something different from what you may think it does.

(3) A hard drive can only have a maximum number of bootable "primary" partitions (four?). But in GParted you can create an "extended" partition and subdivide it into "logical" partitions.

(4) It is a bad idea to move the start point of your Vista partition. Moving the end point is OK. The start point may be one of the factors that Windows uses to decide if your software is a legal copy.

(5) Within Vista, you could take the 17Gb unallocated space and create a new partition there. But I doubt if that has an advantage over using GParted. Vista (home basic, at least) does not allow you to expand a partition.

---

### Post by cespinal on 2008-05-13
Thank you very much por your input... I will give it a try again when I get home... now:
 
*Unless you did something exotic, the problem is not hard to fix.*
 
I REALLY HOPE SO!..
 
*In GParted, simply choose to resize/move the linux-swap partition. You will still have some extra unallocated space left. If you wish, make a new partition there.* 
 
no go here... when I try to do that. it already tells my maximum space is 533Mb. 
 
*A hard drive can only have a maximum number of bootable "primary" partitions (four?). But in GParted you can create an "extended" partition and subdivide it into "logical" partitions*
 
Indeed, it has four partitions, let me see if I can do this.
 
*It is a bad idea to move the start point of your Vista partition. Moving the end point is OK. The start point may be one of the factors that Windows uses to decide if your software is a legal copy.*
 
Have not done that yet, many thanks for the advice
 
*Within Vista, you could take the 17Gb unallocated space and create a new partition there. But I doubt if that has an advantage over using GParted. Vista (home basic, at least) does not allow you to expand a partition.*
 
I didnt have any sucess trying to fix that from Vista, but i'll try over!!!.. now.. If a achieve this, how could I tell ubuntu I want this 17 Gb partition to be a swap partition? 
 
Thanks!!! :guitar:

---

### Post by ironwolfe on 2008-05-13
I guess the obvious question is why do you want such a large swap file?  This will actually slow down your machine.

I am curious - maybe you know something I don't.

---

### Post by Pumalite on 2008-05-13
What do you need a 17 GB /swap partition for?. 2 GB is more than sufficient.

---

### Post by cespinal on 2008-05-14
> **ironwolfe said:**
> I guess the obvious question is why do you want such a large swap file?  This will actually slow down your machine.

I am curious - maybe you know something I don't.


dont worry.. I am totally ignorant about that :P 

I managed to make a right partition but now I installed uswsusp at it not being detected :(

---

### Post by housam on 2008-05-14
Boot from the live cd and post a screen shot of Gparted partition table please.

---

### Post by cespinal on 2008-05-14
> **housam said:**
> Boot from the live cd and post a screen shot of Gparted partition table please.

I installed Gparted so I guees I dont need the live cd, do I?

I'll do that as soon as I can.. I just arrived to the office :S

---

### Post by housam on 2008-05-14
> **cespinal said:**
> I installed Gparted so I guees I dont need the live cd, do I?


you need it to save the screen shot on ubuntu desktop and to be able to post it .

---

### Post by cespinal on 2008-05-14
I just got home from work :) 

here are my partitions.. I guess they are okay now..

---

### Post by cespinal on 2008-05-14
bump....

btw.. have u tried tuxonice??

---

### Post by Partyboi2 on 2008-05-15
If for some bizarre reason you still want to go ahead with 17gig swap use gparted to make another /swap and delete your old one and resize either sda1 or sda5 to use the unallocated space from the old swap.

Or use the current 17 gig unallocated space to create a seperate /home partition and move your /home folder to its own partition. [[COLOR=Blue]Here[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome") is a how-to if interested. Then resize your current 6 gig swap down to 2 gig and move the remaining 4 gig of unallocated space to sda1 or sda5.
Also when working on partitions they need to be unmounted so best to use something like the ubuntu live cd or[[COLOR=Blue] gparted live cd[/COLOR]]("http://gparted.sourceforge.net/download.php")

---

### Post by housam on 2008-05-15
Your partition table is ok except some points :
1 - you have a very big swap partition that is not needed ( 2 GB swap is more than enough ) 
2 - your ubuntu partition is nearly full which will affect the system performance . try to give it some space by shrinking the swap partition to only 2 GB and also adding the unallocated space to it. 
3 - the swap partition is acting as a vertual memory , so you can not install anything on it.
You can read about swap [[COLOR="Red"]_here._[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by cespinal on 2008-05-15
Thank you very much for your advise on this. 

I just read that the swap partition had to be the double of the systems' RAM memory. My laptop has 3 GB RAM so I made the swap partition like that. 

But anywayz, I will follow your advise on this. 

BTW, do you think all this will help USWSUSP detect my swap partitions and hence, install properly? 

Cheers!!!

---

### Post by housam on 2008-05-15
Uswsusp is already exist at synaptic and you can download it from there ( it will be downloaded to the root partition ). you don't have to declare the swap for it. but To use this package you need a Linux kernel version 2.6.17-rc1 or newer configured to use an initramfs.
You can read more about it at synaptic.

---

### Post by cespinal on 2008-05-15
I know it is there, it is just that when I install it, it automatically says I could not find de swap partition so hibernate wont work...

---

### Post by housam on 2008-05-15
To make the swap detectable , I suggest the following :
- delete the swap partition completely and add its GB to Ubuntu partition.
- create a new swap file as described below with the size of 2 GB count=2048  
> How do I add more swap?

      Usually, people associate swap with a swap partition, maybe because they've been proposed to create a swap partition on install. In fact any file can be used as a swapping device, be it a partition or a conventional file. If you're considering responsiveness, my advice: add more RAM. Swapping to a partition or a file won't change anything.

      We will add more swap by adding a swap file.

      Adding more swap is a four-step process :
         

            a- Creating a file the size you want.
          

            b- Formatting that file to create a swapping device.
          

            c- Adding the swap to the running system.
          

            d- Making the change permanent.
    

      We will consider (as an example) a 2GB swap need.
    

      a- Creating a file the size you want :
          

            We will create a /mnt/2GB.swap swap file.
```
sudo dd if=/dev/zero of=/mnt/2048Mb.swap bs=1M count=2048
```

                  What is important here is count=2048, which means we want our file to contain 2048 blocks of bs=1M, which means block size = 1 MegaBytes.
    

      b- Formatting that file to create a swapping device :
```
sudo mkswap /mnt/2048Mb.swap
```
 

      c- Adding the swap to the running system :
```
sudo swapon /mnt/2048Mb.swap
```

     
            You can see with "cat /proc/meminfo" that your additionnal swap is now available.
    

      d- Making the change permanent :
          

            edit your /etc/fstab:
```
sudo gedit /etc/fstab
```

           
            and add this line at the end of the file:


            ```
/mnt/2048Mb.swap  none  swap  sw  0 0
```

          

            save and reboot


---

### Post by cespinal on 2008-05-16
okay! 
so.. I fixed the partitions and uswsusp wont detect the swap one...I'll follow your howto once I get home :) 

Thanks!!!!

---

### Post by cespinal on 2008-05-16
so I made everything just as you said... now it seems that I have a swap file: 

yeto@yeto:~$ cat /proc/meminfo
MemTotal:      2967584 kB
MemFree:       2035848 kB
Buffers:         20124 kB
Cached:         476700 kB
SwapCached:          0 kB
Active:         531100 kB
Inactive:       296244 kB
SwapTotal:     2097144 kB
SwapFree:      2097144 kB
Dirty:              88 kB
Writeback:           0 kB
AnonPages:      329708 kB
Mapped:          91156 kB
Slab:            37316 kB
SReclaimable:    21072 kB
SUnreclaim:      16244 kB
PageTables:      16108 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   3580936 kB
Committed_AS:   912104 kB
VmallocTotal: 34359738367 kB
VmallocUsed:     57276 kB
VmallocChunk: 34359679479 kB

but uswsusp is not dectecting this as far as I that every time i reinstall that program... maybe it just does not work :S.. dunno...

I just encounterd another problem. now I get a boot log in CLI before the splash screen every time i boot into Ubuntu. I know a way to solve this and it inclues changing de UUID of tha swap partition... but now that I have no swap.. what am I supposed to do???  here is the output from terminal: 

yeto@yeto:~$ sudo blkid
/dev/sda1: UUID="342D7D7923AC4107" TYPE="ntfs" 
/dev/sda5: UUID="94d566ce-f91b-4273-80ca-cbb29b370078" TYPE="ext3" 
/dev/sda4: UUID="2C88743C8874071C" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/mmcblk0p1: SEC_TYPE="msdos" UUID="3137-3766" TYPE="vfat" 


thanks...

---

### Post by housam on 2008-05-17
> **cespinal said:**
>  but now that I have no swap.. what am I supposed to do???  here is the output from terminal: 

yeto@yeto:~$ sudo blkid
/dev/sda1: UUID="342D7D7923AC4107" TYPE="ntfs" 
/dev/sda5: UUID="94d566ce-f91b-4273-80ca-cbb29b370078" TYPE="ext3" 
/dev/sda4: UUID="2C88743C8874071C" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/mmcblk0p1: SEC_TYPE="msdos" UUID="3137-3766" TYPE="vfat" 
thanks...

Your partition table have no swap partition , but you already have a swap file which will work the same way as if you have it as a partition . so don't worry about that . the important part is why it is not detectable by this program ? I really don't get it.
Did you tried to hibernate without using this program ?

---

