---
title: "How to install without losing install partition"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by sporkubus on 2007-12-10
So I have an Aspire 5100 laptop, which comes with a partitioned drive with a fresh Windows installer on it. I want to install Ubuntu, but when I open up the installer it tells me I have two options: Guided install for the whole hard drive, or Manual. I tried to install to my extra non-Windows storage partition using Manual, and it gave me the error "No root file system is defined. Please correct this from the partitioning menu."

I guess my questions are, how do I get past this error, and will this keep me from being able to install Windows from the extra partition again?

---

### Post by Pumalite on 2007-12-10
In the space you have, you have to create a partition for '/', another for /swap and one for /home if you want.

---

### Post by mikewhatever on 2007-12-10
Simply follow the guide [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing). Make sure you specify the correct mount point (/) for the root partition.

---

### Post by pieisgood4589 on 2007-12-10
I agree with the guy who first posted. OR, install Ubuntu using the entire disk. Then, install Windows and resize the partition beforehand, but after the installation of Ubuntu with GParted.

---

### Post by erfahren on 2007-12-10
> **sporkubus said:**
> So I have an Aspire 5100 laptop, which comes with a partitioned drive with a fresh Windows installer on it. I want to install Ubuntu, but when I open up the installer it tells me I have two options: Guided install for the whole hard drive, or Manual. I tried to install to my extra non-Windows storage partition using Manual, and it gave me the error "No root file system is defined. Please correct this from the partitioning menu."

I guess my questions are, how do I get past this error, and will this keep me from being able to install Windows from the extra partition again?
I don't know whatyou mean by the "install Windows from the extra partition again?" part.

I'll tell you what I know.
Acer has a Recovery Partition to restore Vista and the beginning of the drive. 

The extra partition ("D" in Windows) Vista on the Acer needs to be able to access (actually, the Acer "eRecovery" application in Vista needs to access it. I've seen somewhere that someone figured out a way to disable that. If you went ahead and installed Ubuntu to that partition you're probably going to need to look into that.

---

### Post by Pumalite on 2007-12-10
You can add ubuntu to the windows boot loader:

Boot from the LiveD.

Step 1) Install Ubuntu. On the last screen click on the "advanced" button and replace (hd0) by /dev/sda3. (Here you need to replace sda3 by whatever partition Ubuntu is on)

Don't reboot immediately. Instead stay on the LiveCD.

Step 2) Mount your Windows partition:

Code:

sudo mount  -t ntfs-3g  /dev/sda2 /windows

(Here replace sda2 by whatever partition Windows is on)

Step 3) Copy the first sector of the Ubuntu partition to a file on the Windows partition:

Code:

sudo dd if=/dev/sda3 of=/windows/ubuntu.bin bs=512 count=1

(Be very careful when using "dd". Info on dd)

Step 4) Add ubuntu to the windows boot loader:

Open "boot.ini" from the Windows partition via
Code:

sudo gedit /windows/boot.ini

Add this line to the end of the file:
c:\ubuntu.bin="Ubuntu"

Save the file.

Reboot and you should get a menu with a Windows and Ubuntu choice.
__________________

---

### Post by sporkubus on 2007-12-10
> **erfahren said:**
> I don't know whatyou mean by the "install Windows from the extra partition again?" part.

I'll tell you what I know.
Acer has a Recovery Partition to restore Vista and the beginning of the drive. 

The extra partition ("D" in Windows) Vista on the Acer needs to be able to access (actually, the Acer "eRecovery" application in Vista needs to access it. I've seen somewhere that someone figured out a way to disable that. If you went ahead and installed Ubuntu to that partition you're probably going to need to look into that.

I guess it is the recovery partition, but I don't understand what you're saying. I know that whenever I want to completely reinstall Windows, all I have to do is hit F10 while I'm starting up and it goes into Recovery Mode. But my computer didn't come with an install disc or anything like that, so I need to keep that partition intact. What I'm afraid of is that I'll install Ubuntu and it will delete this partition.

I'm sorry, but I still don't understand any of this. The installation guide that someone posted didn't help, it just told me how to get where I am already, but there's no "Guided" option for installing both Ubuntu AND Windows for some reason. That would be ideal but for some reason it doesn't appear as an option. I don't know anything about partitioning or any of that so I'm not sure what to do once I get to the partition manager and I DO want a dual boot system.

---

### Post by erfahren on 2007-12-10
> **sporkubus said:**
> I guess it is the recovery partition, but I don't understand what you're saying. I know that whenever I want to completely reinstall Windows, all I have to do is hit F10 while I'm starting up and it goes into Recovery Mode. But my computer didn't come with an install disc or anything like that, so I need to keep that partition intact. What I'm afraid of is that I'll install Ubuntu and it will delete this partition.

I'm sorry, but I still don't understand any of this. The installation guide that someone posted didn't help, it just told me how to get where I am already, but there's no "Guided" option for installing both Ubuntu AND Windows for some reason. That would be ideal but for some reason it doesn't appear as an option. I don't know anything about partitioning or any of that so I'm not sure what to do once I get to the partition manager and I DO want a dual boot system.
1) your actually supposed to create the Acer recovery disks yourself. In Acer this is done with the eRecovery application in Vista (look in the manual - it should be in an Acer folder off of "All Programs")

2)If you took the option to install Ubuntu to the entire drive then yes, it probably would wipe that recovery partition

3) the Acer eRecovery application (in Vista) makes its backups to that Windows "D" partition (or "Data" partition) so it looks for it - probably while booting Windows - since it's set up to start with Windows. As I mentioned, I've seen someone that said how to disable that. I think they mentioned that it took more than just disabling it in Windows startup processes (msconfig) though.

(pls don't make me boot into Vista to look at this stuff!) 

BTW: if you ever used eRecovery to make a backup, the backup is in a hidden folder on that D (or Data) partition.

Anyway...

I'll tell you what I did..

I was in the same position and didn't want to totally get rid of Vista. Ubuntu doesn't really need much space, 20GB is plenty. Especially when you have another partition available for storage.

This is what I did. In Vista, I deleted the backup folder on the Data partition. Then used Vista's Disk Manager (available through the Administrative Tools) to resize the partition to leave about 20GB free and formatted it (I used FAT32 out of habit, but Gutsy has native read/write ability to NTFS now.)

So now there's about 20GB free space to install Ubuntu on.

Then you can just go by psychcat's guide and use the "Manual" option. You'll see that free space in the partition table. Just create a partition for root ( / ) and leave (a little over) 1GB for swap.
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
NOTE: I won't go into partitioning rules here, but you first need to make an *extended* partition out of the entire free space and then make the root and swap partitions logical ones inside of it.

---

### Post by erfahren on 2007-12-10
here is that post I mentioned about the problem with deleting the "D" (Data partition) on Acers and its eRecovery program: [http://ithacafreesoftware.org/forum/viewtopic.php?t=251](http://ithacafreesoftware.org/forum/viewtopic.php?t=251)

(note to non-acer users: all the Acer utilities are called *e*This and *e*That ... it's just about *e*Stupid if you ask me! - LOL )

---

### Post by sporkubus on 2007-12-11
> **erfahren said:**
> 1) your actually supposed to create the Acer recovery disks yourself. In Acer this is done with the eRecovery application in Vista (look in the manual - it should be in an Acer folder off of "All Programs")

2)If you took the option to install Ubuntu to the entire drive then yes, it probably would wipe that recovery partition

3) the Acer eRecovery application (in Vista) makes its backups to that Windows "D" partition (or "Data" partition) so it looks for it - probably while booting Windows - since it's set up to start with Windows. As I mentioned, I've seen someone that said how to disable that. I think they mentioned that it took more than just disabling it in Windows startup processes (msconfig) though.

(pls don't make me boot into Vista to look at this stuff!) 

BTW: if you ever used eRecovery to make a backup, the backup is in a hidden folder on that D (or Data) partition.

Anyway...

I'll tell you what I did..

I was in the same position and didn't want to totally get rid of Vista. Ubuntu doesn't really need much space, 20GB is plenty. Especially when you have another partition available for storage.

This is what I did. In Vista, I deleted the backup folder on the Data partition. Then used Vista's Disk Manager (available through the Administrative Tools) to resize the partition to leave about 20GB free and formatted it (I used FAT32 out of habit, but Gutsy has native read/write ability to NTFS now.)

So now there's about 20GB free space to install Ubuntu on.

Then you can just go by psychcat's guide and use the "Manual" option. You'll see that free space in the partition table. Just create a partition for root ( / ) and leave (a little over) 1GB for swap.
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
NOTE: I won't go into partitioning rules here, but you first need to make an *extended* partition out of the entire free space and then make the root and swap partitions logical ones inside of it.

I'm still a little confused but I am going to try this method, but my Aspire 5100 is one of the older ones that came with XP instead of Vista so I'm not sure how to do this within XP.

---

### Post by erfahren on 2007-12-11
> **sporkubus said:**
> I'm still a little confused but I am going to try this method, but my Aspire 5100 is one of the older ones that came with XP instead of Vista so I'm not sure how to do this within XP.
actually, it's really no different. What you do is move everything off that Data partition (while in Windows). If you ever did a backup using eRecovery the backup will be there as well (in a hidden folder). I *think* it's ok just to delete that, or go into eRecovery to delete it from there. (If you've never used eRecovery then don't worry about that.)

Anyway, in Windows go to Disk Manager (it's part of the Administrative Tools), there are a number of ways to get to that, just look around (Contol Panel in Classic View),

In Disk Manager click on (or right-click on) that Data drive and select edit, resize or whatever you need to do. Resize it to 15 to 20GB and format it with the same file system it had previously (it may be FAT32). 

(My hard drive is 80GB with 40GB for C:\ and 40GB for D:\ originally, I assumed yours would be the same, but maybe not. In any event, if you leave about 15 to 20GB free that will be plenty fo Ubuntu. - basically just divide it in half)

Windows should see the new (shrunken) partition as D:\ again.

So once you have the free space created you can boot into the LiveCD and start the install. Select to manually edit the partition table. Then you should see that empty space in the partition table.
[http://img379.imageshack.us/my.php?image=feistydual10ea7.png](http://img379.imageshack.us/my.php?image=feistydual10ea7.png)

Highlight  the free space and select Edit partition (maybe right-click on it) and where it says "Type for the new partition" select "Logical". Reduce the partition size to leave a little over 1GB free (for swap). Where it says "Mount point" enter in / (for root). Leave the location at "Beginning" and the file system as "ext3".

Out of the 1GB you have left create a partition and set it as swap. 

When you go to the next screen that asks you if you want to write the changes it should only mention the 2 changes you made.

I can't really explain it better than that. To see more comprehensive info on that partitioning see:
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)
(he explains it well)

---

### Post by sporkubus on 2007-12-11
This makes a lot more sense, but I'm in Disk Manager and I can't find an edit or resize option. When I right click on D: my options are Delete Partition, change Drive Letters and Paths, and Format.

---

### Post by lswest on 2007-12-11
if i remember correctly XP can't actually resize from the Disk manager, you're going to have to install a different Partition Manager, and stay away from the trials, they don't usually do anything more than show you how it COULD work:P

---

### Post by erfahren on 2007-12-11
> **lswest said:**
> if i remember correctly XP can't actually resize from the Disk manager, you're going to have to install a different Partition Manager, and stay away from the trials, they don't usually do anything more than show you how it COULD work:P
hmmm. that's odd, *since I used it to change my D partition on two different computers*. One with WinXP and one with Vista. 

I aplogize for missing your post sporkubus, but actually I guess you would need to delete it (there shouldn't be anything on it anyway), then recreate a new partition (primary) out of the free space that's about half the size of it (like 20GB or so - like I was saying before).

Then format it the same file system it was before.

I aplogize for not remembering that's how it's done, it's been awhile. 

I feel like the poster above should've been able to figure that out instead of jumping in with: "you gotta go buy Partition Magic" or something! I've managed to do this a few times without it.

---

### Post by erfahren on 2007-12-11
I have a little more time now, and wanted to mention that *all* of the partitioning could very well be done using the LiveCD's partitioner (GParted).

I usually don't mention that since there would be more steps to do with GParted and I don't know of any good screenshots that could display all that. I also think that Windows users new to Ubuntu would be more comfortable editing/resizing a Windows "D:\" partition from within Windows before going on to using GParted in the LiveCD. 

A third-party partition manager is really not needed and can actually cause more problems than it solves.

I think the AlternateCD (text based installer) is much easier to use when creating a dual boot with Windows when 2 or 3 partitions already exist, and [hermanzone's site](http://users.bigpond.net.au/hermanzone/) cover's that well.

I guess I should've went ahead and tried to explain all that with just using the LiveCD. 

hope you got it going sporkubus. I apologize for any confusion,

---

### Post by Pumalite on 2007-12-11
Stick to Gparted Live CD and resize your XP partition (right click: choose 'resize' from menu). Then install Ubuntu.

---

### Post by sporkubus on 2007-12-11
Hi guys,

I'm going to try to do this on Thursday (finishing a research paper right now and don't want to take any risks :) and I'll let you know how it goes... thanks a lot for all the great help!

---

### Post by sporkubus on 2007-12-11
So guess what! I got impatient and did it anyway :) and everything worked great. Thanks so much guys!

---

### Post by sporkubus on 2007-12-11
OOPS spoke too soon! Now when I try to enable Normal or Extra effects, I get an error saying The Composite extension is not available... any ideas?

---

### Post by erfahren on 2007-12-11
> **sporkubus said:**
> OOPS spoke too soon! Now when I try to enable Normal or Extra effects, I get an error saying The Composite extension is not available... any ideas?
yeah, that's a common one. You most likely have an ATI card. You need enable the propriitary driver and install xserver-xgl.

you need to connect to the internet first, Then go to Software Sources ( System > Admin > Software Sources ) and make sure all the check boxes are selected except "Source Code". - it may ask you to reload. 

(for Gutsy) -- then just do what this says: [http://ubuntuforums.org/showpost.php?p=3547657&postcount=7](http://ubuntuforums.org/showpost.php?p=3547657&postcount=7)

---

### Post by erfahren on 2007-12-11
oops, I guess I should verify that you have an ATI card first.

if you already know you do go on with what I posted. otherwise, in the teminal enter:
```

lspci

```
and look for the "VGA compatible controller:" line

---

### Post by sporkubus on 2007-12-12
I do have an ATI card, and I did do this :) it worked.

Thanks again!

---

### Post by Pumalite on 2007-12-12
Congrats. Would you be kind enough to write down your solution for the benefit of others in the forum?

---

