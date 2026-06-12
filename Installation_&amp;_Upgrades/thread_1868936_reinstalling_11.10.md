---
title: "reinstalling 11.10"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by sfsreporter on 2011-10-25
I had made an attempt to install 11.10 but failed due to inadequate allocation of space and the installer crashed (i guess i did not change the slider). now when i try to re install, i don't get that slider anymore. It opens me to a partitioner which i don't know how to change which sda has to be changed and to how much. I am using windows 7 in parallel. dont want to download 18 GB for wubi can't afford that much data download. please let me know how to partition or is there any way to remove whatever is present and start from scratch.

EDIT: Just to add i'm using a bootable USB prepared as instructed and here a screenshot of the installation window.

---

### Post by varunendra on 2011-10-25
> **sfsreporter said:**
> dont want to download 18 GB for wubi can't afford that much data download.
What do you mean by "18GB download for WUBI"? it downloads only the iso image which is less than 700MB. And if you have a Live USB, you won't need to download it at all.

Anyway, even though it is easy, I won't recommend a WUBI installation. From your screenshot it is clear you have four primary partition in your hard drive (one of which is 'extended' in which there are other 'logical' partitions). So your best and safest option is:

[LIST]
[*]boot into windows,
[*]defragment your largest partition,
[*]open its disk manager and shrink that partition to provide more empty space for Ubuntu
[*]Now boot into live mode from the live USB (choose "Try..." option, not "Install..")
[*]open gparted, and delete the swap and ext4 partitions inside the extended partition
[*]delete the extended partition itself (it should be empty after above step)
[*]re-create extended partition using entire empty space, and recreate the ext4 and the swap partitions
[/LIST]
The recommended size for swap is 2GB, although even 200 should do just fine (provided you have more than 1GB of RAM). Also, is there a specific reason why you are using two ext4 partitions? If there is none and you want to allocate minimum possible space to Ubuntu, a single 5-6 GB partition (+the swap partition) would be sufficient and good. The more (space) the better.

If there is some confusion in this, please post a screenshot of gparted with your hard drive.

---

### Post by sfsreporter on 2011-10-25
the ext4 partitions are probably because of the virtual drives i have created by power iso. i don't know if i should delete them. Or it could be itself created at the time of making attempts to install 11.10 and the uninstalled 11.04 which i got by wubi. I am not an expert with fragmentation and am not much aware of gparted. i am attaching few more screen shots which appear when i boot my pc and select install ubuntu on this device option from a dos like menu. see if i can make the partition changes from this window. what i guess u need me to do is delete both the swap (swap + linux-swap) ones and decrease some of 8830 ntfs and add an ext withe same as the one decreased from ntfs which is probably for win 7.

---

### Post by varunendra on 2011-10-25
Your current partition table is different to what you posted earlier, and definitely represents some messed-up partitioning scheme. Accordingly, what I need you to do now is:

[LIST]
[*]Boot into live session with "Try Ubuntu...." option. Do not attempt to install it yet.
[*]Run gparted. It should be already included in the Live cd/USB
[*]post its screenshot for me to make it easier to provide exact step-by-step instructions. Although it is as easy and friendly as any disk manipulation software can be, an incorrect use of it is as risky as any other such application can be!
[/LIST]
I'd recommend you to read this short guide about using gparted to become comfortable with it: [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

I do not want you to even touch the 8830 MB partition as it may be your windows recovery partition and thus resizing it with gparted may cause booting errors. This reminds me of an important question - How many partitions can you see when in Windows? What are their sizes and labels?

---

### Post by sfsreporter on 2011-10-25
My C drive is as it is.. no partitioning there.

F is my actual cd drive
G & H are virtual drives.

gparted is not working .. i found it in search from the home folder .. when i ask to open, it says unsafe to open and suggests to open if source is known. But it gives no option of opening it any time.

---

### Post by varunendra on 2011-10-25
> **sfsreporter said:**
> 
G & H are virtual drives. Virtual **cd drives** I guess? What is the size of C: drive? (486GB approx. I guess)
If there are no other drive letters visible, the layout must be exactly what I guess it is. For confirmation, I need the screenshot of gparted.
> **sfsreporter said:**
> gparted is not working .. i found it in search from the home folder .. when i ask to open, it says unsafe to open and suggests to open if source is known. But it gives no option of opening it any time.For the method you are using to open it, that message and behaviour is normal. Press **Alt+F2**, then type and enter **gparted** to open it normally.

---

### Post by Mark Phelps on 2011-10-25
Messing around with GParted on a drive that also contains Win7 OS partitions is asking for trouble.  It real easy to corrupt the Win7 OS filesystem and render it unbootable.

If Win7 is still working, then BEFORE you do anything else, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from your partitioning activities.

---

### Post by sfsreporter on 2011-10-25
i am not sure what to do but still since you asked for what is the device case here it is..

is there no way than messing around with the partitions.. as Phelps says its might be dangerous ?

---

### Post by varunendra on 2011-10-25
> **Mark Phelps said:**
> Messing around with GParted on a drive that also contains Win7 OS partitions is asking for trouble.  It real easy to corrupt the Win7 OS filesystem and render it unbootable.
That's why I asked to defragment > shrink the partition from 'within windows' in my first post. From his initial setup it doesn't look likes the OP wants to allocate a lot of space for ubuntu. And messing with anything within an extended partition is not going to do any harm to the windows partition. So I think it is quite safe, provided he uses windows itself to shrink its partition.

But I agree with the idea of creating backup/repair cd/dvd. It is always a good idea to have one.

---

### Post by sfsreporter on 2011-10-25
> **Mark Phelps said:**
> 

If Win7 is still working, then BEFORE you do anything else, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from your partitioning activities.


 I have about 350 GB of data on the hard disk .. do you think the backup feature can handle that much data?

---

### Post by varunendra on 2011-10-25
If you have an external drive available, it is best to move all the data to it before proceeding with partition manipulation.

The problem is - you need to shrink the windows partition to the right side (creating empty space in its left). I don't know if windows disk manager tool can handle this. If it can, there is no problem at all. But still it would be a good idea to move all the data to an external drive as it will very significantly reduce the manipulation time afterwards (which may extend to several hours with that much data to manipulate).

If windows disk manager can't shrink it to the right, you may still get sufficient space in the right side, but then you will have to sacrifice that 4GB space which is currently taken up by the extended partition (sky-blue boundary). Which means, you will have to delete it and leave it unused. Then will have to recreate one in the right side of the windows partition in the space obtained by shrinking the partition.

So as the first space, please tell us if you have an external drive available.

---

### Post by sfsreporter on 2011-10-25
chuck everything.. just gave a second attempt to wubi.. i guess i was wrong . the installation size by wubi is 18 GB but i guess the download was of 700 MB only just took under a minute to get reboot request from windows and now i have got my dual boot all set up !

---

### Post by varunendra on 2011-10-25
Nice to hear you got it anyway :)
Just remember not to update or re-install grub or grub-pc as it may render it unbootable. To lock these packages, follow this:
> Go to System > Administration > Synaptic Package Manager and  select the grub-pc and grub-common packages. Click on Package > Lock  Version.For more info, you should read the WUBI megathread by Rubi1200: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Now that you have it installed on Windows partition, you can safely delete that 'extended partition from within windows (will appear as 'unknown' partitions in windows disk manager). Be informed though - a WUBI installation won't be able to give you full performance of Ubuntu due to being on an NTFS partition. But is definitely safer than messing with partitions ;).


**PS:**
Please mark the thread as [Solved] now that it is. Follow my signature to see how.

---

