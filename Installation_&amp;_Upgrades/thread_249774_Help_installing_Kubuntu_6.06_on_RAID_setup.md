---
title: "Help installing Kubuntu 6.06 on RAID setup"
date: 2006-09-03
forum: Installation &amp; Upgrades
---

### Post by Ub3r-L33ch on 2006-09-03
I have 2 WD 36GB Raptors in RAID 0.  Currently its split in to two partitions, one for windows and the other for windows games.  I used Partition Magic and created about 10GB of free space for Kubuntu.  I've been reading the information here: 
[https://help.ubuntu.com/community/FakeRaidHowto#head-6dd3fe67c8a7ec379d22fd2e6de9b3cf99a47f7e](https://help.ubuntu.com/community/FakeRaidHowto#head-6dd3fe67c8a7ec379d22fd2e6de9b3cf99a47f7e)
and here:
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)
but cant seem to figure it out.

I should mention that it is software RAID.  Its on my motherboard DFI Expert SLI-DR, I'm not using a RAID card.

I have to use Synaptic and install dmraid or something so that the installer will recognize the RAID setup?  I cant find where I need to go to get to the Synaptic Package Manager.

If I could just figure out how to install dmraid I'd probably be good from there.

On a side note, will I be able to setup a dual boot option to load Windows and Kubuntu with this kind of configuration?

Thanks.

---

### Post by oboontoo on 2006-09-04
I have 4 Raptors in my setup (a combo of raid 0,1 and 5) and it seems as if the gparted tool does not support raid configs (or at least I couldn't figure out how to)

I had to install in text mode, which allow you to do software raid configuration.

Martin

---

### Post by Milenko on 2006-09-04
Ub3r,
     I'm having the same problem. My difference is that i'm trying to do the same thing in Ubuntu.  I found dmraid which looked like it helped as Gparted then could see my array and partitions. But for some reason i am unable to create the primary partition.  It managed to put my swap inside my extended partition. 

You need to download dmraid from the synaptic package manager.  That;s the gui one.  You can also do it from command line using apt get i think but not 100% sure.  Let me know if you find anything out.

M

---

### Post by Ub3r-L33ch on 2006-09-04
Installing dmraid with apt-get does not seem to work.  I forget what the error was but I think it has something to do with being a Live CD, it cant write to anything.

How could I setup software RAID support via text mode?

---

### Post by Ub3r-L33ch on 2006-09-04
Ok so I found out its not possible to install on a RAID setup with the LiveCD.  I downloaded the Alternate Install CD which supposedly allows software RAID configurations, here's what happens.

I go threw the setup in text mode, I get to the partition setup screen and I choose "Configure Software RAID"
It asks if I want to Keep Current Partition Layout and Configure RAID - I say yes
I then have these choices:
Create MD device
Delete MD device
Finish
I select "Create MD device"
Then I select RAID 0 (my 2 drives are in RAID 0 config)
I get the message: "No RAID partitions available"
I've tried delete MD device and Finish, doesnt get me anywhere

Dont know where to go from here, any ideas?

---

### Post by oboontoo on 2006-09-04
You first have to setup the partitions you want to use in the raid array.
For raid 0 you need at least 2 partitions on seperate physical disks
For raid 1 you need at least 2 partitions on seperate physical disks
For raid 5 you need at least 3 partitions on seperate physical disks.

With my 4x74Gb Raptors I ended up with
100Mb for  /boot using raid-1 (I'm not sure u can boot off software raid 0)
4 Gb for /swap using raid-0
4 Gb for /tmp using raid-0
9 Gb for /home using raid-5
the rest for / with raid-5

Since you just have two raptors you won't be able to do raid 5 so it should be quite simple for you.
You just need to create the partition you want, twice one for each HD. After you are done you're asked to pick which 2 partitions from HDA and HDB should make up the software raid partition.

Eg.
HDA
100Mb to be used for /boot in raid-1
1 Gb to be used for /swap in raid-0
the rest for / in raid-0 or raid-1 depending one whether you want speed or mirroring

HDB
100Mb to be used for /boot in raid-1
1 Gb to be used for /swap in raid-0
the rest for / in raid-0 or raid-1 depending one whether you want speed or mirroring

When you are done you start configure the raid
/boot is made up from HDA/boot* and HDB/boot*
/swap is made up from HDA/swap* and HDB/swap*
/     is made up from HDA/*     and HDB/*

* Note: the actual HDA and HDB partitions don't have mount points at this point. I'm just using /boot /swap etc as labels to describe the partitions here.

Good luck

martin

---

### Post by Ub3r-L33ch on 2006-09-04
Ok, I think I understand that.  If I already have existing information on the RAID Array (such as Windows) then by doing those steps I will lose all the information.

So, would it be possible to install Kubuntu first, and then install Windows and dual boot?

---

