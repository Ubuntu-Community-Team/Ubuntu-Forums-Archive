---
title: "[SOLVED] HELP installing on Single HDD but separate partition"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by davidkyn on 2008-03-13
So far most of my friends do not like ubuntu as they are having trouble installing on a separate partition so that they can keep their existing OS.  I have to agree with them...I am using the Ubuntu 7.10 i386 that loads on restart into its own GUI for the install.
Despite have two separate Partitions Ubuntu seem to only recognise one HDD giving me the option to make it bigger or smaller...As for the rest, It just seems to scary as two of my mates lost their OS trying to use the options.
I want vista on my Laptop but I also want UBUNTU as I know how good it is...How do I install it on my HDD...I partitioned using vista...Is it because UBUNTU can’t see the NTFS partitions that it won’t let me install on the one I made for it.

Please help...tell me what to do and I will do it....cheers

---

### Post by forestpixie on 2008-03-13
> Is it because UBUNTU can&#8217;t see the NTFSyes it is indeed taht

if you fire up the livecd - open the partition editor in system menu

use it to format the partition you made for gutsy to ext3 - you can't install to a ntfs partition, then make a note of the partition - it'll be sda something and use that when you install
if you're not sure, once you've booted the livecd - open a terminal in apps>accessories and paste this command in and post the output

```
sudo fdisk -l
```

don't format the wrong one though or you'll be unhappy :)

---

### Post by davidkyn on 2008-03-13
I opend the partition editor and did as you said, then I went to the terminal and put in the recomended command but am unsure if it was the right Partition as it is listed as /dev/sda2 anyways, I took a chance and this is the reponse it gave

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$ 

hopefully you will have time to get back to help me...I am going to load the live cd and see if the install sees the new ext3 partition...thanks for you help to...lets see how I go...back in 20 min or so

---

### Post by forestpixie on 2008-03-13
if a command gives you an error - try pasting it in until you're sure - the l is a lower case L not a 1 :)

---

### Post by davidkyn on 2008-03-13
It's amazing how the simplist mistakes can get one so frustrated:
Bad news is, I was impatient and messed around with flagging the drive and editing this and that and now my windows vista boot file is corrupt and will not start. Arghhhh

Anyways after I coppied the right command in this is what I got back:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91d49fef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       21434   172161024    7  HPFS/NTFS
/dev/sda2           21434       30402    72035328   83  Linux
ubuntu@ubuntu:~$ 


I guess I am supose to carry on with somthing else from there but have no idea.....

anyways, while I tried to install to the partition manually in Prepare Partition window...........first it came up with
"specify a partition for the root file system (mount point"1") with a minumum of 2gb and a swap file partition of at least 256mb...you may also set up other partitions it you wish"   YEA RIGHT>>>LOL

anyways I right clicked on my partition to get an edit command where upon I found a mount point/ thingy, which I thought might help the above error...no good..."NO ROOT FILE SYSTEM DEFINED>>>>

I think it was after this I gave up and went back to windows, were I disovered I had some how corupted the vista boot file....OMG

Oh well.......I went back in to undo the boot flag that was now on my most wanted ubuntu partition, but to late...windows still wont boot.....

it's all my fault for not being patient......

Can I install Ubuntu now with the option to put Vista on afterwards somehow...It's not only that I want vista for games....(only some as I can get a lot to run on linux) but bloody ubuntu wont let me use headphones and I tried everything on that!!!!sound still comes out of speakers when using them...

Need a guide to get both OS's running would be good.....
Thanks bud:popcorn:

---

### Post by forestpixie on 2008-03-13
First things first - don't panic :)

Second -lets get buntu installed and then you can deal with Vista afterwards, I'm not too good with that as I've seen it a grand total of 2 times. But there are many helpful people here - I'd use the Absolute Beginners forum - threads can move a bit faster there.

To start with I'm going to hazard a guess at your RAM - we'll say 1GB for now - you need to specify some amount for your swap partition, I have 1Gb Ram and have 1Gb swap but it doesn't get used very much, if however you hibernate - it will be needed - usually 1.5xRAM

Open the partition editor again in the livecd and do these things in order - obviously to the partition you've made for linux

Highlight that partition - sda2
delete it and then click apply 
you will now - again- have unallocated space
in that space create an extended partition - click apply

now work out how much space you want to have for swap, take that away from the partition size eg 10Gb partition - 1Gb for swap

create a new partition within the extended partition - format as ext3
in the remaining space create a new partition and format it as swap, you won't be able to do anything else - click apply

Now you should have 
sda1 - the vista partition
sda4 - extended partition (I'm dredging memory for these)
sda5 - linux partition - ext3
sda6 - swap partition - swap

close and check again with the fdisk command I gave earlier

Now install - when you get to partitioning - choose manual

it will give you a list of partitions on the hdd - choose the ext3 partition we have just created - edit it and you will get a mountpoint box - choose / 

that should be it - it will now install to the ext3 partition and will find swap for itself

To be sure - make a note of the sda number for the partition and then check when you get the "this is what the insall will do" message.

Good luck

---

### Post by davidkyn on 2008-03-13
It,s ok,
once again, could not wait, have vista installed already and am finishing with chipset drivers and what not ready for some updating then will finsih of with final driver tweaks.........

Once finished with that I am going to try this LINK:

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

I will keep you posted...Vista is already back on...SOZ...you have been very helpfull, and this is why I want UBUNTU back, because the hep is there if I need it.....let me know what you think of that link as it might use a different version to ubuntu 7.10

---

### Post by forestpixie on 2008-03-13
no that's a good link - seen it before 

good luck

can you mark thread solved

---

### Post by davidkyn on 2008-03-13
Problems SOLVED...now have Ubuntu and Vista on single HDD...great for Lap tops:

Hey,
That linked worked!!!!!!!!!!! Just one last question Forest...I know it's important to enable stuff in Software Resources so I can actually do some important stuff as well as use 3D desktop and all that...could you have a quick look and tell me what's safe enough to enable so that I can download most files........

Thanks again...I'll hunt around for other questions...Just want to get the software resources right the first time around is all....cheers again:popcorn:

---

### Post by forestpixie on 2008-03-13
easyily done - open software sources - it's in the system>admin menu

tick the boxes - except the source button, untick the cd-rom

then reload
should see it sorted for you - then till you know about apt-get and aptitude - usee add/remove and for much more choice use synaptic

If by 3d desktop you men compiz - that is installed as standard, but to get it to work how you've seen - make sure you have graphics card installed - use restricted drivers first, then you will need the compiz settings manager

---

