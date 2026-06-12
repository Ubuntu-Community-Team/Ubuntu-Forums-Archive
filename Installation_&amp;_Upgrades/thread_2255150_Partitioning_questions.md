---
title: "Partitioning questions"
date: 2014-12-02
forum: Installation &amp; Upgrades
---

### Post by michael-piziak on 2014-12-02
I am currently running 12.04 on machine that can do 64 bit.  If I install 64 bit of 12.04 on half my system to try it out, how difficult is it to wipe out the 32 bit one if I like the 64 bit one or to wipe out the 64 bit one if I dont like it and reclaim the entire computer for the 32 bit one ?

---

### Post by yancek on 2014-12-02
You could use GParted which is on the Ubuntu installation medium to select whichever partition you want and re-format it.  You would then be able to use it for data.  Not a problem.  What you would have to do is make sure you are booting with the Grub from the system you want to keep before doing this.

---

### Post by grahammechanical on 2014-12-02
What do you expect to be different between a 32 bit and a 64 bit version of Ubuntu?

First you load the Ubuntu that you want to keep. Then you run these two commands

```
sudo update-grub
sudo grub-install /dev/sda
```

Assuming that sda is the only disk in the machine. You see, one Ubuntu will be in charge of the Grub boot menu and if you delete that Ubuntu you will not be able to boot the remaining Ubuntu. But those two commands will fix that problem before it happens.

Then you run a live session and at the live session desktop you open a partitioner program called Gparted. You delete the partition containing the Ubuntu that you no longer want. That will create unallocated space. So, you use the partitioner to move/resize the partition containing the Ubuntu that you have kept.

Of course, you have backed up your data before hand. Here is another idea. Simply dual boot between the 2 Ubuntus. Then when you want upgrade to 14.04 you will have a partition to install/upgrade to 14.04 into so that you can test it out and see if it sets up to your liking before upgrading the daily work load Ubuntu.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Regards.

---

### Post by michael-piziak on 2014-12-02
> **yancek said:**
> You could use GParted which is on the Ubuntu installation medium to select whichever partition you want and re-format it.  You would then be able to use it for data.  Not a problem.  What you would have to do is make sure you are booting with the Grub from the system you want to keep before doing this.
The one thing that confuses me is you said select which ever partition you want and reformat it.  Did you mean to say select the one you do not want and format it ?

---

### Post by michael-piziak on 2014-12-02
> **grahammechanical said:**
> What do you expect to be different between a 32 bit and a 64 bit version of Ubuntu?

First you load the Ubuntu that you want to keep. Then you run these two commands

```
sudo update-grub
sudo grub-install /dev/sda
```

Assuming that sda is the only disk in the machine. You see, one Ubuntu will be in charge of the Grub boot menu and if you delete that Ubuntu you will not be able to boot the remaining Ubuntu. But those two commands will fix that problem before it happens.

Then you run a live session and at the live session desktop you open a partitioner program called Gparted. You delete the partition containing the Ubuntu that you no longer want. That will create unallocated space. So, you use the partitioner to move/resize the partition containing the Ubuntu that you have kept.

Of course, you have backed up your data before hand. Here is another idea. Simply dual boot between the 2 Ubuntus. Then when you want upgrade to 14.04 you will have a partition to install/upgrade to 14.04 into so that you can test it out and see if it sets up to your liking before upgrading the daily work load Ubuntu.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Regards.
Please tell me the definitions of sda, grub, and also what is a live session.  Also I thought 64 bit would speed up things, especially games or games that are 64 bit.   Am I wrong ?

---

### Post by Mark Phelps on 2014-12-02
> Also I thought 64 bit would speed up things,

Common misconception ... have tested 32-bit and 64-bit on the same hardware and have found no significant performance improvements running 64-bit.

---

### Post by michael-piziak on 2014-12-02
> **Mark Phelps said:**
> Common misconception ... have tested 32-bit and 64-bit on the same hardware and have found no significant performance improvements running 64-bit.

I was hoping that the 64 bit version would speed up my gaming - particularly the game 0 A.D.    
Have you tested many games like this on 32 bit and 64 bit?   If I watch my System Monitor, only one of my 2 chips is working hard when I play that game.  Chip processor one is maxed out to nearly 100%, while Chip 2 is barely working.  I was hoping a 64 bit version would make both chips share the load.  As it is, the cursor on the game is too slow to make the game playable.

Comments please.

---

### Post by yancek on 2014-12-02
> The one thing that confuses me is you said select which ever partition  you want and reformat it.  Did you mean to say select the one you do not  want and format it ? 		

You asked how to remove a partition so my response was to select the one you want to remove and reformat it.  You don't need to delete any partition just re-format the one you no longer want to use.

---

### Post by Mark Phelps on 2014-12-02
>  I was hoping a 64 bit version would make both chips share the load.

Processor sharing is a function of the app/game code itself.  I have a 6-core 64-bit chip and monitor the core usage real-time both in Windows and in Linux.  And, despite that fact that I am running 32-bit versions of both, I regularly see all the cores being used, not necessarily equally.

---

### Post by michael-piziak on 2014-12-02
> **Mark Phelps said:**
> Processor sharing is a function of the app/game code itself.  I have a 6-core 64-bit chip and monitor the core usage real-time both in Windows and in Linux.  And, despite that fact that I am running 32-bit versions of both, I regularly see all the cores being used, not necessarily equally.

On my 32 bit system, I also see both processor chips being used with the majority of my emulation games and other apps.   However, on this one game that I really want to play, which is 0 A.D., only 1 processor chip is being taxed for nearly all the load while the other chip is barely even doing anything - which I think is perhaps why I'm getting choppy mouse movement and game play on this game.

Your thoughts on that - ?

---

### Post by michael-piziak on 2014-12-02
> **yancek said:**
> You asked how to remove a partition so my response was to select the one you want to remove and reformat it.  You don't need to delete any partition just re-format the one you no longer want to use.

Thanks so much for the clarification.  It was simply a communication break down on my part as I thought you meant for me to select which partition I wanted to keep and format it when you typed "[COLOR=#000000]*select which ever partition you want and reformat it" *[/COLOR]

---

### Post by yancek on 2014-12-02
Just remember if you do this, make sure the system you want to keep is the one which has Grub installed to the master boot record.  Much easier if you do this before than after you make the change.  Lots of posts here about people who did not do this and end up with unbootable systems.

---

### Post by michael-piziak on 2014-12-02
> **yancek said:**
> Just remember if you do this, make sure the system you want to keep is the one which has Grub installed to the master boot record.  Much easier if you do this before than after you make the change.  Lots of posts here about people who did not do this and end up with unbootable systems.

I'm assuming that the previous poster who said the below is what will take care of this Grub requirement.   p.s. What is Grub anyways, is it the thing that controls the boot up screen choice (like boot to this OS or boot to that OS).

[COLOR=#000000]First you load the Ubuntu that you want to keep. Then you run these two commands[/COLOR]

[COLOR=#000000]Code:
sudo update-grub
sudo grub-install /dev/sda[/COLOR]

---

### Post by QIII on 2014-12-02
GRand Unified Bootloader.

It takes control when the Master boot record finds it as the second stage bootloader and passes control to it after loading it into RAM.

GRUB then hands off to the selected OS.

---

