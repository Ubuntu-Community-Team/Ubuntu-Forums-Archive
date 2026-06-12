---
title: "Scared noob - Is it posible to install Win XP after ubuntu is up and running?"
date: 2005-10-01
forum: Installation &amp; Upgrades
---

### Post by prs444 on 2005-10-01
Is it possible to install Ubuntu and then create partitions to install WinXP so I can have a Dual Boot system? Or Do I have to Install WinXP first then use Partition Magic or equivalent to set up the partition for Linux?
I am really think I will be ok without WinXP especially since I found out about the emulator "Wine". If I get stuck and need a Windows program hopefully it will run under Wine.
Any recommendations as to which way to do it? Linux first then Windows if I have to, or install WinXP first then Linux?:confused:
Thanks in advance for your help, so far the Ubuntu community has been unbelievably helpful!:)  
Paul

---

### Post by rippon on 2005-10-01
Windows gets confused if it doesnt come first. Not saying it isnt possible, but If you had the choice, Windows 1st or Linux 1st, go with Windows 1st. Windows likes to be on the first partition of the first harddisk for some reason. 

Just make sure to leave some room on the disk for linux. It will ask you how big you want to make the partition, etc. leave enough "FREE SPACE" and letting ubuntu ( or other distro) auto partition the free space is quickest. Linux will put grub or lilo in the MBR, so you can dualboot. 

--Also look on the forums to setup Windows INSIDE ubuntu. I know I read that here. Im guessing it is like wine, but launches the entire Windows OS. Look into it.

But If you think you can get by w/out windows all the power to you. I personally need it becuase I game, that is it.

Hope I helped, and let some expert respond too! Im kinda noobish.
Dan Rippon

---

### Post by aysiu on 2005-10-01
Any of those possibilities you mentioned are *possible*--doesn't mean they're easy.

The best way to do it is:

1. Partition drives
2. Install Windows on first partition
3. Install Ubuntu on second partition (put Grub on MBR!)

Of course, the partitioning part is the tricky part. If you have a live CD like Knoppix, you can use QTParted to do it. You can always install Ubuntu part-way and have the Ubuntu installer do the partitioning. Or you can pay for Partition Magic and have Windows do the partitioning.

---

### Post by rippon on 2005-10-01
Here is a link for a howto get Windows running in ubuntu.
[http://ubuntuforums.org/showthread.php?t=39513](http://ubuntuforums.org/showthread.php?t=39513)

---

### Post by Herman on 2005-10-01
I think the normal way to do it is to install Windows first and just allow Windows to format the your entire disk. Then after Windows is installed, just put the Ubuntu install CD in your drive and re-start your computer and let Ubuntu's own partitioner do the partitioning for you. It will all go pretty well automatic then. I have done lots of installs this way and it's really easy and nothing ever seems to go wrong. The Ubuntu installer's partitioner is free. Here's how I do it:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Irony on 2005-10-01
Its very simple to install XP and whilst doing it use the XP install disc to partition the drive. I say this because the XP partitioning facility is very easy.
First boot-up from the XP install disc;
[I]
Enter > Esc (for fresh install) > Delete any existing partitions (just delete everything) > Select your partitions sizes and types (here you will see the total size of the disc, as you select the partitions the remaining size goes down. Note select primary partitions. You may only want 2 partitions. Once you've created the partitions they can be altered in type but not size after the install) > Enter to install to C > Format > Copying > Rebooting > Continuing install > Done[/I]

After the XP install is complete go to;

*Start > Programs > Accessories > Computer Management > Disk Management (I think that's the path)*

Right click on the partition you want to install Ubuntu to and click unallocate (note you can't accidently delete the C partition here). Ubuntu will see this as FREE space on installing it. 

You can then install Ubuntu to one of the spare partitions.

You could also simply install XP to the entire disc instead of partitioning it then use the Ubuntu installation disc to shrink the XP partition so that you can install Ubuntu. See [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

