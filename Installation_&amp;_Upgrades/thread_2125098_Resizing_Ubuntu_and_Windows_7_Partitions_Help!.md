---
title: "Resizing Ubuntu and Windows 7 Partitions Help!"
date: 2013-03-13
forum: Installation &amp; Upgrades
---

### Post by Psil0cybin on 2013-03-13
Hey guys, so I just recently installed Ubuntu 12.04 along side with my old Windows 7.
Needless to say I feel in love with Ubuntu, and Linux!! 
I currently have my partitions set to 145 gbs on Windows 7, 60 something Gbs on Ubuntu.
My problem now is that I want to add more memory to the Ubuntu partition...

I wanted to just make sure that I was doing this properly in theory

1. back up important files on both partitions
2. Run disk checks on windows 7 partitions
3. Turn off laptop and boot up with bootable USB Ubuntu
4. Use gparted and reconfigure partitions.
5. Restart to get intended results?

Am I on the right track, or are there other things that i should keep in mind (Sorry if i posted this in the wrong forum)
Thanks in advance!

---

### Post by Psil0cybin on 2013-03-13
Hey guys, so I just recently installed Ubuntu 12.04 along side with my old Windows 7.
Needless to say I feel in love with Ubuntu, and Linux!! 
I currently have my partitions set to 145 gbs on Windows 7, 60 something Gbs on Ubuntu.
My problem now is that I want to add more memory to the Ubuntu partition...

I wanted to just make sure that I was doing this properly in theory

1. back up important files on both partitions
2. Run disk checks on windows 7 partitions
3. Turn off laptop and boot up with bootable USB Ubuntu
4. Use gparted and reconfigure partitions.
5. Restart to get intended results?

Am I on the right track, or are there other things that i should keep in mind (Sorry if i posted this in the wrong forum)
Thanks in advance!

---

### Post by varunendra on 2013-03-13
Duplicate threads merged.
----------------------

Welcome to the forums Psil0cybin!

Please do not create multiple threads for the same question. It dilutes community efforts to help.

---

### Post by Psil0cybin on 2013-03-13
Sorry about that wasn't sure exactly where it should go, was a tad confused..but thanks for cleaning it up for me.
Just a little excited!! Hopefully soon Ill have no need for windows 7 or anything windows related for that matter :)

---

### Post by varunendra on 2013-03-13
No problem with that, but...> **Psil0cybin said:**
> 
4. **Use [COLOR="#FF0000"]gparted[/COLOR] and reconfigure partitions**.
5. Restart to get intended results?
Don't do that!

Use windows tools to resize windows partitions. Use gparted only on the empty space left after resizing, or on the Linux partitions.
Windows can sometimes get messed up if external tools are used (outside windows) to manipulate its partitions.

Rest of the plan seems okay.


**PS:**
Oh, and do not forget to create backup + (at least) System Repair CD/DVDs from control panel > Backup and Recovery option in windows.
Just in case things don't workout as you expect and you wish to return to the more familiar windows..

---

### Post by Psil0cybin on 2013-03-13
> **varunendra said:**
> No problem with that, but...
Don't do that!

Use windows tools to resize windows partitions. Use gparted only on the empty space left after resizing, or on the Linux partitions.
Windows can sometimes get messed up if external tools are used (outside windows) to manipulate its partitions.

Rest of the plan seems okay.


**PS:**
Oh, and do not forget to create backup + (at least) System Repair CD/DVDs from control panel > Backup and Recovery option in windows.
Just in case things don't workout as you expect and you wish to return to the more familiar windows..

Sorry im just super new, I just want to make sure we are on the same page before I attempt anything..
I have 3 partitions the two default partitions that are created with Ubuntu and the Windows Partition.
So i would use the windows tools to resize the windows partition (take away Gbs) - Make it smaller.
Than i would use Gparted (Via Bootable USB) to add more gbs to the Ubuntu Partition?
Sorry if it seems a little big confusing..
And thanks for the tip im going to defiantly create a system repair cd/dvd (in my case- USB) Just in case..

Darn if I knew id fall in love with Ubuntu this much, I would have just allocated more space to begin with, Just I never had a good experience with Wubi and wanted a taste of the real thing! Now I hardly even use my Windows Partition, Just need it there for school work once in a while at the moment
Thanks again in advance
and Thanks varunendra, for your quick reply!

---

### Post by varunendra on 2013-03-13
> **Psil0cybin said:**
> im going to defiantly create a system repair cd/dvd (in my case- USB) Just in case..

-- good idea, backups are always a good idea :)

Just something more about partitioning you should know..

Be it gparted or any other partitioning tool, resizing is always a bit tricky job.
If you re-size a partition from its right side (end of partition), it will be done quickly.
But if you even slightly disturbed its Left boundary (start of a partition), it will almost certainly take eternity to finish the job. I think you don't want to go into details why.

If your windows partition is BEFORE the Ubuntu partition, then shrinking it will create the space in the Left side of the Ubuntu partition. In that case, it would be much much better and a lot more quicker to just delete the Ubuntu partition > re-create it and re-install Ubuntu.

It shouldn't be a problem if you have just installed Ubuntu and there is not much to save there. But if there is, you can use tools like clonezilla or if possible, remastersys to create a backup of your Ubuntu installation which you may later restore on the newly created larger partition.

If unsure, post back the output of -
```
sudo fdisk -l
```
from ubuntu.

---

### Post by Psil0cybin on 2013-03-13
Thank you for the wisdom! That is something I need to think about, I really am not sure which side each is on..
All i know is that the Windows 7 Was the first O.S, and then Ubuntu got installed after.
Do you think for my case since I have sort of a new install of Ubuntu (only differences is i customized appearances , it might be best to just format both partitions and do a clean install of each?

I ran the command
Here is the output

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2b9b4523


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   497674651   248733902    7  HPFS/NTFS/exFAT
/dev/sda3       497676286   625141759    63732737    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       497676288   623069183    62696448   83  Linux
/dev/sda6       623071232   625141759     1035264   82  Linux swap / Solaris


Disk /dev/mapper/cryptswap1: 1060 MB, 1060110336 bytes
255 heads, 63 sectors/track, 128 cylinders, total 2070528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x80b8b593


Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

```

Does [COLOR=#000000]clonezilla keep the changes that i made to the Ubuntu? So all my preferences would be installed as well?[/COLOR]
Resizing might be a tricky job, but I might be up for it!
Also when you mean Windows Tools (You mean an application that comes with Windows? I thought if your using a partition, you cannot resize it? Or Windows tools as in a bootable CD that might have came with my laptop - I never got anything)
Sorry for the silly questions
Thanks again in advance!

---

### Post by varunendra on 2013-03-13
These are quite sensible and important questions, nobody considers them silly here.

> **Psil0cybin said:**
> Do you think for my case since I have sort of a new install of Ubuntu (only differences is i customized appearances , it might be best to just format both partitions and do a clean install of each?
If you can, and all that is important is backed up, that's the best option.
Also, if you have the full installation DVD of windows, there is no need to create repair cd, as it includes that function. Boot and go to repair mode to make sure.

As per the output of fdisk, your Ubuntu partition is within an extended partition AFTER windows - that's a typical win/lin dual boot layout that I was concerned about.

> Does clonezilla keep the changes that i made to the Ubuntu? So all my preferences would be installed as well?
Clonezilla takes an exact image of the partition (normally compressed, but can be bit-by-bit if you wish), then restores it the same way, including boot sector and MBR if required. The only limitation of clonezilla is that it can not restore an image on a partition that is smaller than the original one which it cloned. But in your case it is going to be restored on a larger partition, so that point is moot.

So yes, it preserves everything, regardless of what is on the partition/drive.

> Also when you mean Windows Tools (You mean an application that comes with Windows?
By windows tools I meant windows' own disk manager that is part of windows installation. Although third [arty tools installed and running on the same windows installation can also do the job, but the native disk manager is a preferred way.

 > I thought if your using a partition, you cannot resize it?
You are correct, a partition 'in use' can not be manipulated. That's why such tools run with Admin privileges and get 'exclusive access' to the partition they are dealing with. Means, you can not actually use it while these tools are in action on it. If it is the windows partition itself, then those few things that give you the interactive environment in that duration are all run from within memory, and no read/write on the partition is permitted (well, the tool and the OS do have to do necessary reading/writing required to do the job).

Hope it helps clearing your doubts.

---

### Post by Mark Phelps on 2013-03-13
Just so you know ... we advise Against using GParted (or other Linux partitioning tools) to resize Win7 OS partitions because doing that can sometimes result in filesystem corruption -- rendering win7 unbootable, and therefore, very difficult to repair.

While the Win7 Disk Management utility is quite primitive, nonetheless, it does NOT corrupt Win7 -- so it is the preferred tool to use.

---

### Post by Psil0cybin on 2013-03-13
Thank you so much for your tips guys! So what im concluding is that it is better and easier to format both partitions and install from scratch than to repartition both windows and Ubuntu, gathering from my **fdisk** output?
Or do you guys still think its possible to take all the gathered precautions, and than attempt a modification of the windows 7 partition with windows tools and enlarge ubuntu using gparted? 

I have looked at **clonezilla**, and it seems a little bit complicated following the instructions confused me a bit, Would i use the USB bootable option, in order to create an ISO of my settings? Maybe I cannot find a detailed enough guide, ill take another look.

I might just stick with my current partitions till the summer time and after exams to play around and reconfigure everything.
Im guessing I might as well take this to my advantage and take time to learn alot about how Ubuntu and Linux function and in the future when I reformat ill just create a much larger Ubuntu partition.. 

Thanks again in advance,
[SIZE=1]Psil0cybin[/SIZE]

---

### Post by varunendra on 2013-03-14
Nothing is impossible. There are ways and methods for everything you want to achieve. What you choose should be based on your own priorities.> **Psil0cybin said:**
> Thank you so much for your tips guys! So what im concluding is that it is better and easier to format both partitions and install from scratch than to repartition both windows and Ubuntu, gathering from my **fdisk** output?
Or do you guys still think its possible to take all the gathered precautions, and than attempt a modification of the windows 7 partition with windows tools and enlarge ubuntu using gparted?
If both installations are fresh and important stuff has been backed up, then logically it is best to wipe out partitions and start fresh.

For learning and experience point of view the second choice is better - resize partition, use it for Ubuntu. If you want to preserve the settings, custom apps you might have installed on either, then also this is a better choice.

By the way, 60 GB is more than plenty for Ubuntu installation alone. A normal installation with normal applications (they're huge in number, but small in size) does not usually exceed 20 GB. You can store your user data on a different partition, and it CAN be a windows partition if you need.

You can also create a separate ext3/4 partition ANYWHERE on the disk and set it as your "Home". Most of the program settings and ALL of the user data goes in home, so you can even 'shrink' Ubuntu root partition to about 30-40 GB afterwards.

That said, I'd leave the decision upto you to choose the way to go. I think you have enough information to make a decision now, and we are right here if you need more.

I'm glad Mark joined us as he has a lot of experience in dual booting. As for using clonezilla, here are a couple of tutorials :

[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
(old one, but tested and it still works the same way)

[http://www.dedoimedo.com/computers/clonezilla.html](http://www.dedoimedo.com/computers/clonezilla.html)
(new one from the same author, looks good, although I haven't read it in detail yet.)

Feel free to ask if you have more questions.

---

### Post by Psil0cybin on 2013-04-10
Really you think 60GB's should be more than enough?
I guess I dont game, and your right I can store all my videos and music in my windows partition..
So I guess it will work out for now :)
Thanks again, gave me a nice perspective.. Im going to bookmark this thread so when I have a bunch of spare time
Ill play around (having backed up all important information obviously)

---

