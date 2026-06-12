---
title: "[SOLVED] Reinstalled Hardy; Grub won't boot Linux; error 18"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by fox.esq on 2008-06-01
I reinstalled Ubuntu 8.04 to fix some stuff I couldn't remember how to undo.  I used the alternative CD because liveCD just won't work for my advanced computer.  Everything appeared to reinstall just fine but when I rebooted, grub would start and get to the point where it said 'please wait', then say error 18, then just hang there and do nothing.  I tried doing the installation over again a couple more times with the same result.

I have a dual boot set-up with Windows XP on my first hard drive, and Ubuntu intended for my second hard drive.  When I reinstalled I reinstalled the same way as I did the first (which was successful and operated almost problem free) time and on the same disk, using the entire hard disk.  I thought reinstalling would wipe everything, but apparently it is not.

I would get error 18 in grub previously when I tried to boot the new kernel 2.6.24-17; -16 would not give me any problems.

I've tried using Super Grub, but the instructions really don't tell you in plain English what you're doing.  When I tried reinstalling Grub there it wouldn't work, and when I tried booting Ubuntu from Super Grub it wouldn't work either; I could only get Windows to boot up.  Super Grub for me is Super Crap; I couldn't even get it to delete Grub, it would simply fail and reset the computer.  Error 15 was a common excuse for not working.

Is there a trick to grub when reinstalling? Do I have to uninstall it somehow?  How can I wipe everything clean and reinstall without snags?

---

### Post by Pumalite on 2008-06-01
I had trouble reading your post. I think it would help immensely a normal font.
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by fox.esq on 2008-06-01
Thanks for the link. I have already looked at it.  I might give it a try, but it looks very complicated.  The thing is, when I reinstall I used the original CD I used the first time, and with no internet connection, so it should be using kernel ...24-16, not -17 which was giving me the error 18 problem.  What I don't understand is why it worked the first time and not the second time when, in theory, it should be installing under identical conditions - on a wiped clean hard drive.  Also, my motherboard is recent, and the build date of the Bios is 01/24/07 - it's an Asus P5W DH Deluxe.  Is Grub placed on the same harddrive as Windows XP? if so, does reinstalling Ubuntu also cause Grub to be reinstalled there too, or is there another way to wipe it clean?  -- What I'm afraid of is that fragments of the newer kernel remain from the former installation and are corrupting the new re-installation.

I can't take 'Herman's' advice either because I can't access Ubuntu period.  I also can't use live CD, only the alternative.

I've also already tried to switch the drives in the Bios and booting from the one with linux on it.  No luck.

Also, My hard drives are connected with SATA cables not IDE.

---

### Post by meierfra. on 2008-06-02
> - What I'm afraid of is that fragments of the newer kernel remain from the former installation and are corrupting the new re-installation.
That seems extremely unlikely.

But it  does seem to be the  typical Error 18, out of reach of the bios problem.     Some bios are only able to see the first 137 GB of your hard drive (although  that does seem unlikely with your fairly new bios)
Your kernel has been placed somewhere on the ubuntu partition. If it happens to be within the 137 GB, then the bios can see the kernel. If not, then not. A  new kernel might be placed outside the 137 GB, and suddenly you get error 18.

You will get error 18, before the computer even looks at the  contents of your kernel. So a kernel update really shouldn't  be able to produce error 18, unless it has to do with the location of the file.

Are you able to boot other LiveCD, say Knoppix or  Gparted?   It would be useful to see the output of 

```
sudo fdisk -l
```

---

### Post by fox.esq on 2008-06-02
I can look into Gparted.  I was reading some posts about it but there was nothing clear whether I could use the cd to boot from, or whether it would solve my problem.  Where would be a good place to get a functional recent copy to download of Gparted?

---

### Post by confused57 on 2008-06-02
> **fox.esq said:**
> I can look into Gparted.  I was reading some posts about it but there was nothing clear whether I could use the cd to boot from, or whether it would solve my problem.  Where would be a good place to get a functional recent copy to download of Gparted?
Here's a link to the Gparted live cd:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Ubuntu Gutsy 7.10 live cd also has gparted...System---Administration---Gnome Partition Editor

---

### Post by meierfra. on 2008-06-02
> or whether it would solve my problem. 

I believe the best way to solve you problem  is to create a separate boot  partition. Gparted is the good tool for your partitioning.

 Also you can open a terminal in gparted and post  the output of "sudo fdisk -l". This will tell us the exact the size and location of your Ubuntu partition.

---

### Post by fox.esq on 2008-06-02
Ok.  I am downloading and burning Gparted now.  I should know in the next hour what's going on.  I will open the terminal and plug in "sudo fdisk -1" and try to send you what it says.  Hopefully you can make sense of the info and instruct me from there.

---

### Post by fox.esq on 2008-06-02
Alright I ran "sudo fdisk -l" and this is what it came up with:

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes

Device____Boot____Start____End_____Blocks______ID____System
/dev/sda1__*_______1______20022___160826683+_7____HPFS/NTFS

Disk  /dev/sdb: 164.6 GB, 164696555520 bytes
etc., etc., etc., 

Device_____Boot____start_____End______Blocks_____Id____System
/dev/sdb1____________1______19205___154264131__83____Linux
/dev/sdb2__________19206____20023____6570585____5____extended
/dev/sdb5__________19206____20023____6570553+__82____Linux swap / Solaris

Disk  /dev/sdc: 0 MB, 327680 bytes

Disk  /dev/sdc   doesn't contain a valid partition table


(Exclude the line in between the numbers, I put them in so it would line up with the category heading)

I hope this helps.  It kind of makes sense to me; it appears that Linux is at the begining and everything else is at the end.

---

### Post by fox.esq on 2008-06-02
Above are the results of running "sudo fdisk -l" in Gparted live CD.

---

### Post by meierfra. on 2008-06-02
According to fdisk your ubuntu partition is about 77GB  and starts at the beginning of the disk. So all parts of your ubuntu partition  are well within the 137GB limits. And your bios really shouldn't have a problem with the earlier 8GB limits.


In short, I have no clue what is going on. I still suggest to create a separate boot partition, see [Hermanzone ]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition") for instructions.

But I  really  do not know whether this will solve you problem.

Before you start to partitioning, I just want to make sure that Grub is installed correctly. 

Which drive are you booting from?
Are you able to switch the boot order in the bios?
Post you menu.lst: Open a terminal in the  GpartedLive cd. Type

```
mkdir ubuntu
mount -t ext3 /dev/sdb1 ubuntu
cat ubuntu/boot/grub/menu.lst
```

I also want to see what happens if you boot from a different drive. So we will install grub to the MBR of both drives. We will to  this in two ways, From gparted and from supergrub, start with Supergrub

Boot  from Supergrub and press "c".

(In gparted  LiveCD type "grub" in a termimal. This might fail, I'm not sure the Gparted LiveCD has  "grub")

In either case continue like this

```
find /boot/grub/menu.lst
```
(l is a lowercase L)

The output should be either "(hd0,0)" or "(hd1,0)"

```
root (hd1,0)  # use the output from the previous command
setup (hd0)
setup (hd1)
```

In gparted type "quit"  and in supergrub "reboot" to exit.

This installed grub to the MBR of both of your hard drives.  Try booting from each of them and see whether you can get to the Grub Menu.


There is a fair chance that "find /boot/grub/menu.lst" will return "file not found" in SuperGrub. This would confirm the theory that the Bios are unable to read your ubuntu partition.

---

### Post by memekthecat on 2008-06-02
Sorry, if I post my problems in the wrong thread..hope to hear something about it from anyone out there...
Here is the situation, I tried to reinstall ubuntu live cd, first its was normal as what it has to be but then the words "starting up" appeared...half an hour later i got something like this..
**[1822.511647] kernel panic - not sycning : Attempted to kill the iddle task!**
Please help me... ](*,) I'm running out of the booze here.

---

### Post by meierfra. on 2008-06-02
This really is the wrong thread. Please start your own thread.

---

### Post by fox.esq on 2008-06-03
> In short, I have no clue what is going on. I still suggest to create a separate boot partition, see [Hermanzone ]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition") for instructions.

But I  really  do not know whether this will solve you problem.

Before you start to partitioning, I just want to make sure that Grub is installed correctly. 

Which drive are you booting from?
Are you able to switch the boot order in the bios?


I am booting from the first drive, the one with Windows on it; the NTSF drive.  This is the same drive I was booting from when I originally had Hardy installed and there were no problems except that once the kernel was upgraded, I couldn't boot it, I had to use the older ....24-16 instead of -17.

I am able and have switched the boot order in the bios.  I also switched which hard drive was being booted from.  Linux wouldn't  start either way.  Now when I start my computer, there is no grub, it simply goes directly to booting Windows (which for now is convenient).

Perhaps the master boot record on the NTSF drive isn't being properly wiped in the re-installation?

Is there a way to wipe my second hard drive (including all its partitions)with Gparted so I'm really working from a clean slate when I reinstall Ubuntu?  Also, is there a way to refresh the MBR from the NTSF drive (or wipe it completely if it isn't necessary)so that upon re-installation, it won't mess up the installation of GRUB?

---

### Post by meierfra. on 2008-06-03
To completely wipe you drive, use "dban" (just google it). But I don't think this will solve your problem. If you start from scratch, make sure to use a separate boot partition.

---

### Post by fox.esq on 2008-06-03
For some bizzare reason I was able to get the Ubuntu Live CD to work.  Can you give me instructions on how to partition my hard drive so that it will install and boot up correctly?  Hermanzone's instructions are just too complicated for me.  What is the difference between Swap and ext3 formats?  Is swap for Grup?

> Post you menu.lst: Open a terminal in the GpartedLive cd. Type

Code:

mkdir ubuntu
mount -t ext3 /dev/sdb1 ubuntu
cat ubuntu/boot/grub/menu.lst

I was not able to get this to work.  I don't know how to plug this stuff in. do you hit enter after each line?  If so, after I entered in the first line it came up with some "root" complaining.

---

### Post by meierfra. on 2008-06-03
I just noticed that I must have been asleep when I looked at your "fdisk" the last time . For some reason, my brain did  divide all the numbers by 2.  So actually your Ubuntu partition is 160 GB. And so  the kernel might have ended up outside the 137 GB limits. That makes  me  much more confident that creating a separate boot partition will solve your problem. 

> Can you give me instructions on how to partition my hard drive so that it will install and boot up correctly? 


Since resizing a "160GB" partition  might take longer than reinstalling,  I suggested to just deleted all your current partitions. And, if want you, can use "dban" although I don't think it will make any difference.

Boot from the Gparted LiveCD. Then 

1)  Deleted all current  partitions.

2)  Create a primary partion of size  200MB and   format ext3. This  is your /boot partition.

3)  Create a extended partition using all the unallocated space. (An extended partition is just a container for other partition)

4) Create  a logical  partition of size  20GB and format ext3. This is  your / partition.

5)  Create a logical partion of format Ext3  using almost all of the unallocated space (but leaving enough space for a swap partition).This is your  your /home partition.

6)  Create a logical   partition of size 2GB and format Swap. This is your Swap partition.

The actual size you  should use for your swap partition depends on your ram. I usually use this rule:

Twice the ram, but not more than 2GB. But if you use hibernation than it needs to be at least  as large as your ram.

If you follow this scheme you will have  the following partition 

sdb1  200MB   /boot
sdb2   ~160GB  extended
sdb5   20GB    /
sdb6   ~137GB  /home
sdb7    ~2GB Swap

Now then you install Ubuntu, choose "manual" partitions.
You need to edit the following partition:
 
sdb1: Use  as ext3 with mount point /boot 
sdb5:  Use  as ext3   with mount point /
sdb6: Use as ext3   with mount point /home

> What is the difference between Swap and ext3 formats? Is swap for Grup?

ext3 is the file system most people us for / and /home

swap is the format  used for a swap partition. The swap partition is used as a substitute for ram in case your ram is all used up. (I have 2GB of ram and  my swap partition never gets used)

> 
mkdir ubuntu
mount -t ext3 /dev/sdb1 ubuntu
cat ubuntu/boot/grub/menu.lst

I was not able to get this to work. I don't know how to plug this stuff in. do you hit enter after each line? 


Yes.

> If so, after I entered in the first line it came up with some "root" complaining.

I'm not sure what happened.   You might try it again from the Ubuntu LiveCD.

---

### Post by fox.esq on 2008-06-04
Ok, I followed your instructions for partitioning with gparted and your instructions for installation with Ubuntu Live CD and everything appears to working now.  I updated Hardy and use the new ....24-18 kernel and it looks like it is working without any problems!  Thank you very much for you help!

I am still dumbfounded as to why I had no problems the first time I installed Hardy, and then after updating the kernel I would, then also after reinstalling Hardy.  I'm wondering if I'm just working my way around a problem or if it was really solved.

Anyway, it's working and I'm glad there aren't any problems -- as of yet!

Thanks again!

-Brian

PS: would you happen to know how to make Ubuntu load more quickly?  My parent's computer is older, slower and has a lot less RAM than mine, but their's seems to start loading before the rectangular bar bounces back to its starting point, while mine takes upto a minute of bouncing back and forth before loading and then, on rare occasion, jump into some script mode.

---

### Post by meierfra. on 2008-06-04
> I am still dumbfounded as to why I had no problems the first time I installed Hardy, and then after updating the kernel I would, then also after reinstalling Hardy. I'm wondering if I'm just working my way around a problem or if it was really solved.

I'm pretty sure you solved your problem. Any new kernel will be installed in you /boot partition. You boot partition is only 200MB, so your bios will always be able to see the kernel.  You problem  arose  when a new kernel was put to the far end of your ubuntu partion, outside the reach of the bios.

> Would you happen to know how to make Ubuntu load more quickly? 

Sorry, I don't know anything about that. But I know that there are plenty of threads devoted to this subject. So it should be possible to find an answer.

Would you mind marking the thread as solved:

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads ]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

