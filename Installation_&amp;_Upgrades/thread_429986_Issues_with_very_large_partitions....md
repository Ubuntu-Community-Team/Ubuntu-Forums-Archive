---
title: "Issues with very large partitions..."
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by philipMac on 2007-05-01
Hi, I posted this : [http://ubuntuforums.org/search.php?searchid=19273558](http://ubuntuforums.org/search.php?searchid=19273558) up previously. 

First of all, I probably should have posted here rather than servers, since it was an installation problem. That might have been why I received no replies... 

What I wanted to point out was that the parted partitioner cannot seem to deal with my large 7TiB partition. 
If I try to do an automatic partition I get the "No root defined" error, if I try to install the OS on the 7Tb partition manually it seems to partition but fails to ever boot. 
I got around this by carving a smaller 20G boot vol out of the big RAID vol. Then I ignore the big partition, and load the Os onto the small 20G part. 

From here I boot the OS, (Feisty) and ran 

sudo parted /dev/sdb1 mklabel gpt
sudo parted /dev/sdb1 mkpart primary 0 6989GB
sudo mkfs.ext3 /dev/sdb1

but then  
cat /proc/partitions
gives
8    16 6814820352 sdb
8    17  372369375 sdb1

and it fails fsck on boot sequence. 
so, I tried 
sudo mkfs.jfs /dev/sdb1
then when I cat partitions I see

  8    16 6814820352 sdb
  8    17 6814820319 sdb1
Good. 
and tested with fsck, which said it was fine, I updated fstab with jfs rather than ext3, and rebooted, and it failed fsck. When I cat partitions again I see it
is back to the 
8    16 6814820352 sdb
8    17  372369375 sdb1
state.

What is the problem? I thought ext3 on a 64 bit machine can handle 7Tb partitions? Why does it keep insisting it is only 370Gigs all the time?

Thanks...

---

### Post by louieb on 2007-05-01
> **philipMac said:**
>  That might have been why I received no replies... 
What I wanted to point out was that the parted partitioner cannot seem to deal with my large 7TiB partition. 
What is the problem? I thought ext3 on a 64 bit machine can handle 7Tb partitions? Why does it keep insisting it is only 370Gigs all the time?
Thanks...
Probably the reason you did not receive a reply:  not many here if any have 7TB of space to play with. People tend to help others with Linux problems they have had to work thought themselves. GRUB Beryl etc.  
Good luck, I hope you find a solution might try the enterprise section of [LinuxQuestions.org]("http://www.linuxquestions.org/") :guitar:

---

### Post by philipMac on 2007-05-01
Right... eh, ok. No one else has large partitions like this then?

I should point out that this is in fact the partition is 16x500G raw, but effectively this ends up being ~7Tb when under RAID6,  and it is a hardware RAID. There is no problem with the RAID card, or the system I feel, just the OS's treatment of the partition. 

If people are not familiar with these sizes, can anyone tell me if it is a "bad thing" to allocate the big RAID partition as /dev/sdb rather than /dev/sdb1. 

I dont care about re-sizing it, I just want something that works reliably, and isn't going to corrupt 6 months down the line etc.

---

### Post by bukwirm on 2007-05-02
The problem may be that your BIOS (or the linux kernel) doesn't allow booting from a partition larger than a certain size (just a guess, I'm not entirely sure). This doesn't keep you from using all of your 7TiB, though - just make a small partition (<1GB) for /boot, and a larger partition for /.

---

### Post by philipMac on 2007-05-02
> **bukwirm said:**
> The problem may be that your BIOS (or the linux kernel) doesn't allow booting from a partition larger than a certain size (just a guess, I'm not entirely sure). This doesn't keep you from using all of your 7TiB, though - just make a small partition (<1GB) for /boot, and a larger partition for /.

I should have explained the situation better maybe. 
I have carved a volume from the RAID, 20Gs. From this volume, I have partitioned off the necessary partitions, boot, swap, root, var, etc. 

I load the OS onto this volume, onto these partitions, and everything is fine. 
The problems only start when I try to partition the large 7Tb remaining partition. 
The issue is that if I do anything other than treat the entire volume as a single partition, eg 
if I say 
sudo mkfs.ext3 /dev/sdb

rather than 
sudo mkfs.ext3 /dev/sdb1

then everthing seems to work ok. 
But, I am thinking that this might be a bad thing.I have been told that it is. Is this true for a start?
I don't really want to hear rumours that someone heard from someones friend that it might be a bad idea, I want actual yes no concrete answers ;) 

take it easy....

---

### Post by philipMac on 2007-05-02
its so weird...
sudo parted /dev/sdb mklabel gpt
sudo parted /dev/sdb print

Disk /dev/sdb: 6978GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      17.4kB  6978GB  6978GB  ext3         primary  

sudo parted /dev/sdb mkpart primary 0 6978GB

sudo mkfs.ext3  /dev/sdb1

cat /proc/partitions
   8     0   20971519 sda
   8     1     248976 sda1
   8     2    1951897 sda2
   8     3   18763920 sda3
   8    16 6814820352 sdb
   8    17 6814820319 sdb1

sudo fsck /dev/sdb1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sdb1: clean, 11/851853312 files, 26779760/1703705079 blocks

sudo vol_id /dev/sdb1

>/etc/fstab : UUID=blah	/test	ext3	defaults	0	0

reboot.

sudo fsck /dev/sdb1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
The filesystem size (according to the superblock) is 1703705079 blocks
The physical size of the device is 93092343 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? yes

cat /proc/partitions 
major minor  #blocks  name

   8     0   20971519 sda
   8     1     248976 sda1
   8     2    1951897 sda2
   8     3   18763920 sda3
   8    16 6814820352 sdb
   8    17  372369375 sdb1


wtf???
What has changed? I dont get it. I just reboot, and everything goes to hell.

---

### Post by philipMac on 2007-05-03
No ideas?

What about the idea that the MBR on sda is msdos labeled, and therefore has the old 2Tb limit, and this is being read for both sda and sdb, causing problems?

I should note that the sdb is labeled gpt, which is well able to deal with 7Tb partitions. 

Seriously, does no one else run these big partitions?

---

### Post by supermonkeyman2004 on 2007-05-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/parted/+bug/107326](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/107326) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've exactly the same problem. Turns out it's a bug, a serious bug with the ubuntu version of parted.

See this thread... [https://bugs.launchpad.net/ubuntu/+source/parted/+bug/107326](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/107326)

I've a 3TB raid in a HP DL320s server with a 80GB mirrored boot partition. Boot is fine.

Like you, I can create a XFS partition on the raid (/dev/cciss/c0d0 in my case), and put data onto it. However, post boot, it's always knackered - returning the following:

root@machine:~# **mount /dev/cciss/c0d0p1 /raid**
[COLOR="Red"]mount: /dev/cciss/c0d0p1: can't read superblock[/COLOR]

Hopefully someone will fix this, otherwise I'm off to another distro which isn't broken.

-- D.

---

### Post by philipMac on 2007-05-07
Oh man. 
This is bad news... this means I have to run another OS on the machine? 

What happens in 6.10?

Is parted knackered end of story, or just not working in Feisty? 

Is there any other options here, like can we partition with something other than parted, and load the OS on these partitions?

---

### Post by philipMac on 2007-05-07
OK, it looks like this is only in Feisty. 

I am going to give Edgy a go, and see what the story is I think...

---

### Post by philipMac on 2007-05-07
This sucks. 

Edgy install just craps out completely at the Partition Disks step, and hangs in a blank blue screen. 


Arg. 

Is there a way to partition the disks with something else, and then load the OS on later?

---

### Post by philipMac on 2007-05-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/parted/+bug/107326](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/107326) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This sucks huge donkey balls. 


Is there any work around here? Is there any way you can label a disk as GPT without using parted?
cfdisk doesn't work either. 

What about the solution that uses /dev/sdb rather than /dev/sdb1 as the partition, ie basically have no partition table.

This seems to work, but I am being told that this is a bad thing. Does anyone know if this is true or not?

---

### Post by tgalati4 on 2007-05-07
You are definitely and edge case.  That would be Donkey Dung or Bovine Balls.

Can you create 2 terabyte partitions?  Sometimes instead of fighting the problem work with it.  Find the largest partition that will stick and make a lot of them.

Or wait until Linux catches up with the hardware.

---

### Post by philipMac on 2007-05-07
So, ok... create 2Tb partitions, and then combine them with LVM or something? But, then my RAID 6 numbers are killed, fewer spindles and all that. 


The thing is, that this is not a problem with Linux. It seems to be a problem with Ubuntu's screwed up parted.  I can create the partitions perfectly, its only on reboot that everything goes wrong. 

There is this volume control thing in the RAID card. Maybe I will try carving lots of 2Tb volumes out of the single RAID 6 partition and then combine them with LVM. 

Man... this is so annoying. 

No takers on whether using /dev/sdb as a single partition is safe or not, no? 
I am inclined to believe that it is not such a hot idea, but, the fact of the matter is it works apparently flawlessly. You have no labels, no partition tables, nothing on the disk, just one massive partition. 

Seriously, is this an ok solution?
Ie, 
20G boot vol carved from the big RAID partition, 
split up into swap /boot /var / etc and then /dev/sdb as the other partition.

---

### Post by tgalati4 on 2007-05-07
Perhaps you can explain what you are setting up.  What is the advantage of having one huge partition?

Inode tables will be huge, more CPU cycles will be used just to find stuff on the disk.  I am missing the advantage.

You have noted the difference between sdb and sdb1.  It certainly looks like fsck gets confused when checking the virtual size of the file system and comparing it with the physical size.  I don't know what to recommend here.  Perhaps there is a switch with fsck to duplicate the problem in the current session, then disable that switch during boot up.  Perhaps there is a way to bypass the fsck upon boot.  Afterall you trust Ubuntu with 6TB of data, why bother checking it.

There are other partition tools, including ones that come with the disks themselves.  Usually you can format them with a generic "Linux" (probably ext2) partition.  You might have better luck booting into windows and using the drive manufacturer's latest windows drivers to format the disk.

The other suggestion is to get a copy of SLES (SUSE Enterprise Server edition 10) and use the partition tools on it.  I got eval copies at SCALE 5X of both SLES and SLED.  I've only installed SLED on a demo machine, and I must say it has a lot of polish.  The server edition is designed to be installed on blade systems with mega disks.

Again, it boils down to selecting a distribution that works with your hardware.  You can fight it, but sometimes just choosing the proper distro will reduce the amount of donkey dung.

How many music files can put on a 6TB array?

---

### Post by philipMac on 2007-05-08
Alright... first of all, the issue is fixed. 

Score. 

Issue : Ubuntu's parted is broken. 
To Fix : get gnu's latest parted code, compile it, run it, everything works. 
(You will need to grab some things, off apt-get etc, g++, ncurses-devel, readline, blah blah, just pay attention to the config file output.)

relabel the disk, partition it up, stick on a file system (ext3 in my case), cat /proc/partitions, looks good, fsck /dev/sdb1 works, update fstab, hold breath, reboot, bingo. 


Ok, to tgalati4, I am setting up a NAS, for a genomics department. These people have *lots* of data, I want to give them somewhere to keep it, safely. A single partition (either logical or otherwise) makes life easier for me. 

Why I want lots of disks in an array, because the numbers just work out better. This is a hardware RAID, I am RAID6ing it, the card does all the work for me. 

The reason I want to use Ubuntu... is I really like Debian, I like the way it deals with packages, and the way it does things. I am migrating / migrated the rest of the machines about to Ubuntu, and it just makes life for me lots easier to be dealing with a single distrib. 

Especially since I am not really a sys admin...

---

### Post by tgalati4 on 2007-05-08
I'm glad you shared your solution.  Most sys admins would chose a different distro for this application.  But report back in a year and let us know how well Ubuntu holds up with large RAID arrays.

---

### Post by supermonkeyman2004 on 2007-05-11
Hi.

Great news on your parted fix for Ubuntu :KS .

I'm currently banging my head against a brick wall. One chap mentioned using SLES10 - utter crap that is too!

The same DL320s (remember with 80GB mirrored boots, 5x750GB raid5/6 'data) fails under SLES10 - looks like parted is broken on that box too! :mad: 

The parted on SLES10 (1.6.25.1 and kernel 2.6.16.27-0.9-smp) does **NOT** seem to like anything above 2TB as a source drive/device size.

Any chance you could post more details (or a link to your new parted binary for Ubuntu Server 7.04) of how you got parted to come good on UB?

Cheers,

-- D.

---

### Post by philipMac on 2007-05-11
hey... 

I will do a walk through:

fire up synaptic. 
remove Parted and libparted (1.7 on mine).

(terminal)

% wget [http://ftp.gnu.org/gnu/parted/parted-1.8.6.tar.gz](http://ftp.gnu.org/gnu/parted/parted-1.8.6.tar.gz)

% tar zxvf parted-1.8.6.tar.gz

% cd parted-1.8.6

(synaptic) 

(Now, at this point, i needed to get some more stuff to make configure working. On my machine it was the following, but make sure you read what ./config is telling you, and sort the issues there.)

g++ and deps.
uuid-dev.
libncurses5
libreadline-dev

% ./configure

% make

% sudo make install 
(just accepting the default location...works fine, change this if you like)

sudo parted /dev/sda
GNU Parted 1.8.6
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
blah. mklabel works, everything seems fine. 


Its very easy when you know what's wrong. I almost feel a bit silly posthing this all up, but, here it none the less. 

Best,
Philip.

---

### Post by mawalters1 on 2008-01-05
Thanks **philipMac **and tgalati4.
I have been fighting these limits as well with 4TB and now 7TB arrays.
I have used on 32bit system, LVM with stripping which yields great performance, however defeats the purpose of using LVM in the typical usage.  Then I had 3ware raid controller that allowed for allocation of boot area (carving), essentially show up as 2 drives. 

Then I  config'd (2 drive, or virtual drives), the liveCD process I partition drive one with standard /boot, swap, /, then for sdb I used I used mklabel and used loop.  The used mkfs.ext3 over the big fricken array... I called it BFR.

Not the best solution but that was better than the LVM one in my opinion. I didn't mention with our LVM, I had to do JBOD, which solve other needs, we needed RAID5/6 things. So BFR proved interesting workaround in a 32 bit space.

I would then wire up and mount the sda3, mkdir boot, mount the sda1 to that locale, then I would drop one of our agnostic images over the top.
We use dump/restore.  Turned out to be nice solution for restore images to any size system.  Just ahve to twiddle the grub.conf, fstab accordingly...used mount -o bind directives to map the large array into position.

Same idea, let the RAID5 or RAID6 handle the recovery elements.

Thanks also to **tgalati4 **for performance ideas over not using ext3 in this situation, which is useless in the large array single partition space.

Now I need to go get my parted, that seemed to work, or get all the package installed into the live session of the ubuntu 64bit install I am using, which I thought due to 64bit would have no issues in addressing 7TB.  

In ending you are not alone in this PITA stuff.
AFter all this, I will have to scrap my internal slax6 usage.
Then when all said and done, I have to use ghost to make a image to send off to CFI... another good PITA exercise....

---

