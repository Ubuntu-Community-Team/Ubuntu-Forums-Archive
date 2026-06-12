---
title: "install problem with ubuntu 8.04.1"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by blitz_mohit on 2008-08-22
i have a 160GB SATA II drive and i had already partioned it to have a 20Gb partion for installing ubuntu 8 x64..i am also using fedora and windows vista on that drive..
i am always getting a error during the partion manager part of installion..
i always click forward on the default by it gives error Invalid size
and when i start up ubuntu using cd and then try again sometimes the partion manager just fails and sometimes gives error Invalid size..
didnt find any updates for the installer and the partion manager

---

### Post by niyonk on 2008-08-22
hi,
what does 'sudo fdisk -l' show...
Maybe we can take a look and see how your partitions are arranged...

Or you already exceeded the number of primary partitions...not sure

You could also try the 'Manual' method instead of 'Guided'

---

### Post by blitz_mohit on 2008-08-22
thanks for the wonderfully fast reply...
using vista now and deleted fedora also and now have one primary partition before deleting i had two primary partitions and now going to try installing again..if unsuccessful will post the output of sudo fdisk -l..

---

### Post by blitz_mohit on 2008-08-22
tried installing again but failed with same error(Invalid size)
here is the output of sudo fdisk -l

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2dd52dd4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       20023   140351872+   f  W95 Ext'd (LBA)
/dev/sda5            2551        6629    32764536    b  W95 FAT32
/dev/sda6            6630       10708    32764536    b  W95 FAT32
/dev/sda7           10709       14787    32764536    b  W95 FAT32
/dev/sda8           14788       17337    20481024    b  W95 FAT32
/dev/sda9           17338       20023    21575263+   b  W95 FAT32

and i don know how to install through manual..if u could guide me through that too..

---

### Post by niyonk on 2008-08-22
why exactly do you have all of those extended partitions??

What i did in my case was go to computer management and create a partition from there, then at the installation i used the manual method and sliced the partition i created from windows into other pieces like swap and home partition.

---

### Post by coffeecat on 2008-08-22
> **niyonk said:**
> why exactly do you have all of those extended partitions??

Sorry to nitpick, but it's important to get this right; sda5, 6, 7, 8 and 9 are **logical** partitions. The extended partition is sda2 which is the container for the five logicals - see the cylinder counts.

**blitz_mohit**, your hard disc is completely full. You have no less than five fat32 logical partititions, four of which are larger than your primary Windows partition, and one [noparse](sda8)[/noparse] is the same size as your Windows partition. Do you know how you managed to get those?

I can't quite work out what you did at the installer stage, but I should imagine the error messages are because there is no room on the HD.

Tell us what you want to achieve, then someone can advise you what to set up in Gparted - which you can find at System > Adminstration > Partition Editor in the live CD - **before** you go into the installer. Then you just tell the installer which pre-prepared partitions you want to use, and the rest should be straightforward.

---

### Post by blitz_mohit on 2008-08-23
when i first bought this computer the hard disk was already partitioned into 5..i had windows xp then..afterwards i installed vista on the first one..then installed ubuntu through windows..and fedora after giving it one of the logical partitions for itself..then yesterday i decided that i wanted to give more space to ubuntu so i cleared up 1 logical partition,uninstalled it from windows and tried to install through cd but it kept giving me the error messages..so i just deleted the fedora partition and made it fat32..and tried again..but it doesnt work..instead i screwed up my computer and had to install vista again..

all i want is that i should get ubuntu in main partition and use vmware on it for windows..and pls i didnt get wats wrong with the hard disk any step to correct that too would be really nice..
pls guide me through as i am a total noob..

---

### Post by coffeecat on 2008-08-23
> **blitz_mohit said:**
> pls guide me through as i am a total noob..

The Vista partition (sda1) is about 30-35 GB, and I'm not sure whether you want to keep that or not. So...

**Option 1** - The easy option - Blitz everything.

Only do this if you don't want Vista and you have nothing on those five logical partitions you want to keep.

Boot up the live CD, and go into Gparted. You can find that at System > Administration > Partition Editor. Highlight each of the partitions in turn, starting at the bottom and press delete after you have highlighted each. Now click on Apply. You have now completely erased all partitions and your whole hard disc is 'unallocated'. Close Gparted and and start the installer. When you get to the partitioning stage, choose the first option and the installer will partition the HD for you. You will end up with a huge root partition - plenty of room to install Windows in VMWare - but this doesn't give you much flexibility for the future.

**Option 2** - Keep Vista

Make sure you have backed up any data you may have on the five logical partitions, boot up the live CD and go into Gparted as above. Select each of the logical partitions, sda5, 6, 7, 8 and 9 for deletion and click on Apply. **Do not delete sda1 or sda2**.

Now click on New. Make the size of the new partition equal to your RAM, choose logical (it can't be anything else with that big extended partition), and filesystem type 'swap'. OK that. Click on New again. This time make the size as big or as small as you want it. This is going to be your root partition. Let's say 40GB. Choose logical again and filesystem type ext3. OK that and click on Apply.

You now have two new partitions as follows: sda5 = swap, sda6 = ext3.

Close Gparted and open the installer. When you get to the partitioning stage, choose the last option - I think it's called custom. It will pick up sda5 automatically as your swap, and tell it to make sda6 your root partition. The code for that is /. Make sure you specify a mountpoint for Vista - say /media/Vista - and then let it install.

If you do this you will have a big enough Ubuntu root partition for the time being and plenty of space left on the hard drive for future use - data partition(s), other Linux distros, whatever you like. What I haven't suggested is a separate /home. Some people prefer this but for now this might just be an added complication for you.

Final word. Take it slowly and think it through. I have offered you two suggestions. Others may have other ideas. Do this at your own risk.

---

### Post by blitz_mohit on 2008-10-29
> **coffeecat said:**
> The Vista partition (sda1) is about 30-35 GB, and I'm not sure whether you want to keep that or not. So...

**Option 1** - The easy option - Blitz everything.

Only do this if you don't want Vista and you have nothing on those five logical partitions you want to keep.

Boot up the live CD, and go into Gparted. You can find that at System > Administration > Partition Editor. Highlight each of the partitions in turn, starting at the bottom and press delete after you have highlighted each. Now click on Apply. You have now completely erased all partitions and your whole hard disc is 'unallocated'. Close Gparted and and start the installer. When you get to the partitioning stage, choose the first option and the installer will partition the HD for you. You will end up with a huge root partition - plenty of room to install Windows in VMWare - but this doesn't give you much flexibility for the future.

**Option 2** - Keep Vista

Make sure you have backed up any data you may have on the five logical partitions, boot up the live CD and go into Gparted as above. Select each of the logical partitions, sda5, 6, 7, 8 and 9 for deletion and click on Apply. **Do not delete sda1 or sda2**.

Now click on New. Make the size of the new partition equal to your RAM, choose logical (it can't be anything else with that big extended partition), and filesystem type 'swap'. OK that. Click on New again. This time make the size as big or as small as you want it. This is going to be your root partition. Let's say 40GB. Choose logical again and filesystem type ext3. OK that and click on Apply.

You now have two new partitions as follows: sda5 = swap, sda6 = ext3.

Close Gparted and open the installer. When you get to the partitioning stage, choose the last option - I think it's called custom. It will pick up sda5 automatically as your swap, and tell it to make sda6 your root partition. The code for that is /. Make sure you specify a mountpoint for Vista - say /media/Vista - and then let it install.

If you do this you will have a big enough Ubuntu root partition for the time being and plenty of space left on the hard drive for future use - data partition(s), other Linux distros, whatever you like. What I haven't suggested is a separate /home. Some people prefer this but for now this might just be an added complication for you.

Final word. Take it slowly and think it through. I have offered you two suggestions. Others may have other ideas. Do this at your own risk.


pls tell me exactly how to give a mount point for vista..

---

