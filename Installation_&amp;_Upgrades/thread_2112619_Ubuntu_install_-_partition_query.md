---
title: "Ubuntu install - partition query"
date: 2013-02-05
forum: Installation &amp; Upgrades
---

### Post by pabl013 on 2013-02-05
hi, have been unable to find a similar thread/solution...i have used ubuntu previously, so am not a newbie, but then again, i'm not an expert.

i have 3 partitions, one currently Win 7, the other two i use for storing files etc. i have tried to install ubuntu, but am confused by the options that come up. i want to install ubuntu on the first partition, instead of Win 7. 

i am given the option to install it over Win 7 (thus losing all files etc associated with windows), but it's unclear whether that option reformats (just) the first partition, or whether it reformats the whole drive (ie losing everything on the other two partitions too)? 

i have had a look at the other options, which shows you all the partitions etc, but i found that very confusing, and did not want to make a mistake and risk losing all my data on the two partitions. 

therefore, can someone clarify whether installing over win 7 will safely do so on the one partition, or whether it will clean the whole drive?

in the past i have installed ubuntu on a second (older) drive which made the install process easier for me to manage, but that drive has recently failed.

cheers.

---

### Post by Mark Phelps on 2013-02-05
You should probably first do the following: open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  This will list out the partitions on your drive along with their filesystem types and sizes.

Presuming you want to overwrite Win7, if it came preinstalled, there would be two partitions -- a boot partition and a Win7 OS partition.  If you installed it yourself, there is likely to be only one partition.

But, either way, Ubuntu will not install to a Windows filesystem partition -- which may be why your not seeing the option you want.

If you really want to install over Win7, then boot from an Ubuntu LiveCD or LiveUSB, choose Try Ubuntu, when the desktop comes up, use the Dash to launch the Gnome Partition Editor (GParted) and use that to remove the Win7 partition.

You can then install Ubuntu into the free space using the "something else" option.

---

### Post by TheFu on 2013-02-05
> **Mark Phelps said:**
> You should probably first do the following: open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  This will list out the partitions on your drive along with their filesystem types and sizes.

@Mark - has fdisk been fixed to handle GPT formats, HDDs over 2TBs and automatically align on 4K sectors?  I've been recommending that people stop using fdisk completely until those issues are resolved.  **parted** and **gparted** "do the right things" today on those HDDs.

---

### Post by SBFree on 2013-02-05
Hi:
You should be able to choose the partition that Linux installs into with the standard installer. There should be a choice for installing a scheme that is "Something Else" as a choice for using your partitions. I have attached a pic. Choosing Something else will take you to the partitioning screen. You will have the choice to choose the partition you want. The simplest scheme would be to assign / to the partition and save a small segment for the swap partition. My thought is you will have to reformat the Windows partition as Ext4 and resize it to allow for a Swap partition. At any point you can back out and cancel changing the partitions.
Hope this helps.
Scott

---

### Post by sudodus on 2013-02-05
Welcome to the Ubuntu Forums, pabl013 :-)

Always ***backup your data*** before editing partitions or installing operating systems!
--
I suggest that you edit the partition, where you want to install Ubuntu before you really install it.

Boot from the Ubuntu install drive, run a live session 'try Ubuntu'. Use ***gparted*** to

1. delete the partition where Windows is now.
2. create an extended partition
3. create a swap partition of the same size as the RAM or slightly larger (in Gibibytes, multiples of 1024 ...).
4. create an ext4 file system of the rest of the unallocated space (for example: Windows had 100 GB. You have 4 GB RAM. Make a swap partition with 4096 MB or a little more. Use the rest (90-something GB) for the ext4 file system.
--
Then during the installation, when you arrive at the screen "Installation type", see the page in the attached file, select "***Something else***".

And here you should select the ext4 drive, you have prepared with gparted for the root partition ***/***
--
This way you should not jeopardize the data in the other partitions, but there are always risks when editing partitions, so I recommend that you ***backup your data*** (at least your personal files) before you start. It might also be a good idea to make a complete image of your Windows installation or create a rescue disk, if you would like to get it back in the future, maybe for dual booting.

---

### Post by pabl013 on 2013-02-05
okay, many thanks for the responses, much appreciated. yes, i have backed up data.

from that i get the impression that the simple option of installing over Win 7 will wipe the whole drive. i'll have a go at the suggested way forward when i am at my computer tonight.

cheers (Y).

---

### Post by sudodus on 2013-02-05
> **pabl013 said:**
> okay, many thanks for the responses, much appreciated. yes, i have backed up data.

from that i get the impression that the simple option of installing over Win 7 will wipe the whole drive. i'll have a go at the suggested way forward when i am at my computer tonight.

cheers (Y).

There is a risk that the data will be destroyed, but if successful (95% of the cases), only the windows partition will be affected, so the data in the other partitions should survive (according to my previous post).

---

