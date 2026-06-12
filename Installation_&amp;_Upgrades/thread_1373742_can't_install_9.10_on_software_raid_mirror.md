---
title: "can't install 9.10 on software raid mirror"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by oldunixguy on 2010-01-06
I am trying to install 9.10 64-bit workstation on a software raid1 without success. I am not using fake raid on the motherboard.

I have two clean 1TB sata drives and the Ubuntu installation CD.

I have spent the past week attempting methods spelled out in the Ubuntu installation guides, scoured the forums on the topic and tried each method to no avail.

Let me summarize the first approach since it was the simplest configuration. The guides state that one can create a single large partition and a swap and the installer should work. It doesn't. Here is what I did:

1. boot the live CD to operational state.
2. sudo apt-get install mdadm
3. using gnome->system->administration->disk utility (titled palimpsest disk utility) I created a software raid of the entire 1TB drive on each drive for a 2-member mirror.
4. started the Ubuntu installer
5. selected from the partition step to manually partition
6. /dev/md0 was listed. created a 12GB swap
7. created a 988GB ext4 partition for /
8. continued. here the large partition got formatted and then the installer thew up an error dialog box that reported can't mount swap. Well, swap is not supposed to be mounted! It only allowed me to go back to the partitioner and not continue on.

Next, I tried again using the installer's partitioner.
1. still running the live CD I started the installer.
2. selected manually partition and then selected the /dev/md0
3. deleted all the partitions.
4. created partitions of: ext4 / of 250MB, ext4 /tmp of 250MB, ext4 /var of 3GB, ext4 /usr of 6GB, swap of 12GB and the rest ext4 /home
5. it complained that the / was too small and it wanted 2098261504 bytes!
6. I ignored it and continued. here it formatted the first partition (/dev/md0p1). Then it failed while trying to format the second one (/dev/md0p2).

Next, I tried a different approach.
1. While still running on the live CD I did a sudo gparted /dev/md0
2. deleted all the partitions.
3. created partitions of: ext4 / of 250MB, ext4 /tmp of 250MB. When I tried to perform the second it reported an error on mkfs.ext4 -j -O extent -L "" /dev/md0p2 as "no such device or address".

Following the installation of mdadm and the creation of the software raid I can see that the 2 discs are wokring together when the first partition is being formatted, especially if it is the large partition. Nonetheless, I can't get the installer to continue regardless of the partition arrangement.

HELP!

---

### Post by lister171254 on 2010-02-05
Have you tried using the alternative installation. This will allow you to configure your raid1 as part of the installation.

---

### Post by oldunixguy on 2010-02-06
Thanks for your response! Could you explain what the "alternative installation" is? I have been on hold stopping all work hoping someone would respond with a solution. More importantly I was expecting those developers responsible for the installation process to be reading these error posts that they would come back and either ask for my voluminous logs or even say "we fixed it". That never happened. So where are the developers?

I selected the installation type of 64 bit and workstation since that is what I needed. If you are implying that I need a different type of installation then that means it would be some configuration that didn't fit my use. There is so little good instructions and from what I can see NONE on how to use some other package (which I think this is what you are getting at) to overcome the bugs in the type I did select yet still cause the "alternate installation" to end with the same result of having the workstation package installed.

I wanted a package that could quickly get me to a 64-bit workstation setup with program development tools, documentation tools, and a simple desktop. So I picked the 64-bit Workstation. Other selections I saw would not get me there as well as they seemed much more complicated. If the documentation was a lot better maybe it could happen.

So, can you tell me what "alternate installation" to use and how to accomplish the same end result of the workstation setup or point me to some competent secret documentation that does it?

I sure hope so.

By the way, do you know any direct contacts for the developers of the installation software so I can send them these bugs since they aren't reading this?

thanks a bunch,
rich

PS. The installation type I did select said in many places around the ubuntu community that I could create a raid1. It just doesn't work as I have already reported.

---

### Post by lister171254 on 2010-02-06
The location for the alternat install .iso seems to change for releases, bit for Karmic I did the following.

Go to the Download page and select "Alternative Download options, Including Ubuntu...." (see attached t1.jpg)

Select Bit Torrent (see attached t2.jpg)

Pick the version you need.

When you install, you will see the difference.

Cheers

---

### Post by oldunixguy on 2010-02-08
I took your advice and got the "alternate amd64 iso" using bit torrent. I created the CD and booted it. I got the text menus and reached the partitioner. I have 2 identical 1TB sata. As I have attempted with the Desktop Installation, I partitioned entire sda as one primary raid, entire sdb as one primary raid. Then I selected "configure software raid". I used both drives, 0 spare.

Next I selected "finish" and it reported "no root file system defined".

Well, my top-level is an MD raid "RAID1 device #0". It shows under it a #1 1.0 TB and nothing else. It shows my sda and sdb as 1.0 TB raid. In this partitioning menu I cannot select any other operation to the top-level raid partition or the #1 below it. ! I can't create files systems in it.

I'm stuck again.

this crap just doesn't work.

Any other ideas?

thanks, rich

[IMG]http://usmartdigi.com/Partitions%202.JPG[/IMG]

[IMG]http://usmartdigi.com/cant%20use%20raid.JPG[/IMG]

[IMG]http://usmartdigi.com/no%20root%20fs.JPG[/IMG]

---

### Post by lister171254 on 2010-02-08
I'm dpong this from memory, but here are the steps.

I'm assuming you have two disk of 1TB each and you want to mirror the disks.

1) Format disk1 as with a size of 998Gb and mark it as a software raid device
2) Format the rest of disk1 as swap
3) Format disk2 to the same as step 1
4) Format the rest of disk2 as step 2
5) Now select 'Configure Software RAID' from the options. It should ask you for the type of RAID.
6) Select RAID 1. This should prompt you for the two disks you want to use. Chose the disks partitioned in steps 1 and 3.
7. I think you then need to say that you are done with this step. You should get back to the 'Partition disk screen and should have a new device
8 Select that device and ensure that you make the file system EXT3 or EXT 4 amd make sure that you choose the entire disk as root '/'. (or whatever partitioning you wish


That should be it.

Cheers

---

### Post by oldunixguy on 2010-02-08
Thanks for the suggestion. However, I am trying to raid1 the "entire drive". That is, all partitions are on the same, single software MD raid, even the swap. All of the ubuntu "raid" info on the various user guides say this is supposed to work and it should. It is just that none of the installers will work correctly to do it.

If you closely read what I did with the "alternate" you will see the entire drive is a single raid and then the MD software raid uses that.

What the problem is here is that the "alternate" has no features to partition the newly created MD software raid partition.

If you look way back in my initial post you will see that I actually got much farther using the normal "desktop distribution". Here I created the entire drive as a raid partition (on both drives), created the MD software raid1 and even created the / partition ON the MD software raid. The only problem there was that the installer could not for some bug reason map to it and continue the process.

Here with the "alternate" it will not even let me create a partition on the software raid- even worse than before.

Sorry for the bad news but this still doesn't work as it should.

thanks,
rich

---

### Post by lister171254 on 2010-02-08
Select the drive "#1" under "RAID 1 devices #0. This will say something like that the drive is currently not being used. Make the file system EXT3 or EXT 4 amd make sure that you choose the entire disk as root '/'.

---

### Post by oldunixguy on 2010-02-08
Doesn't work. This is what is displayed in the 2nd image and why I attached it. On that image you can see more or less "empty" partition settings. If one positions the cursor over any of this it does not allow any actions. So it is a dead end. Bottom line- can't then create a partition on the software raid MD.

r

thanks,
rich

---

### Post by lister171254 on 2010-02-08
You must select the 
"Use As: Do not use" and hit return

---

### Post by oldunixguy on 2010-02-16
Ah HAH. That is not documented. And since the operations are listed below them as "Copy..., Erase..., Done..." one doesnt know there are functions that can be displayed.

That said, I was able to change the #1 partition (shown in image 1) to ext4 and mounted as /.

However, I can't create the swap in the top-level Raid1 device #0. I can only get it to create the one partition (shown in the first image as #1). I want to create a / and a swap.

If I delete this Raid1 device #0 and start over I still only get to create a single partition #1. 

Ironically, I could create the MD raid1 with any number of top-level partitions on the raid1 using the workstation CD but it would not properly continue and recognize the partition mapping to functions like / and swap.

With this alternate method I also have no control on the size to create this partition #1.
How then do I set the partition #1 size and create the partition #2 as swap here?

thanks,
rich

---

### Post by lister171254 on 2010-02-16
From you screen shots I take it that you have allocated all of the two 1TB drives to the RAID. Unfortunately, you cannot treat the RAID as you would a physical drive (ie. you cannot partition a RAID only the physical drive).

My suggestion is to do the following:

1) Go Back to the section where you configure the software raid and delete the RAID you have created. 
2) You should now only have the two dribes SCI4 on sda and SCI2 on sdb

Follow my original suggestion about formatting the drives and configuring the software RAID (ie.

1) Format SCI4 (sda) as with a size of 998Gb and mark it as a software raid device
2) Format the rest of disk1 as swap
3) Format SCI2 (sdb) to the same as step 1
4) Format the rest of disk2 as step 2
5) Now select 'Configure Software RAID' from the options. It should ask you for the type of RAID.
6) Select RAID 1. This should prompt you for the two disks you want to use. Chose the disks partitioned in steps 1 and 3.
7. I think you then need to say that you are done with this step. You should get back to the 'Partition disk screen and should have a new device
8 Select that device and ensure that you make the file system EXT3 or EXT 4 and make sure that you choose the entire disk as root '/'. (or whatever partitioning you wish


Cheers,

leo

---

### Post by darkod on 2010-02-16
Not relevant. :)

---

### Post by darkod on 2010-02-16
> **oldunixguy said:**
> Ah HAH. That is not documented. And since the operations are listed below them as "Copy..., Erase..., Done..." one doesnt know there are functions that can be displayed.

That said, I was able to change the #1 partition (shown in image 1) to ext4 and mounted as /.

However, I can't create the swap in the top-level Raid1 device #0. I can only get it to create the one partition (shown in the first image as #1). I want to create a / and a swap.

If I delete this Raid1 device #0 and start over I still only get to create a single partition #1. 

Ironically, I could create the MD raid1 with any number of top-level partitions on the raid1 using the workstation CD but it would not properly continue and recognize the partition mapping to functions like / and swap.

With this alternate method I also have no control on the size to create this partition #1.
How then do I set the partition #1 size and create the partition #2 as swap here?

thanks,
rich

I think during the process somewhere you did create one single partition on the RAID1 device. I see from the screenshot you correctly created the RAID1 device but at one point you need to create partitions on it and you can definitely select the size. Repeat the process or delete partition #1 from the RAID1 device and try again creating / partition (but not from the whole available space) and then swap from the remaining.

---

### Post by oldunixguy on 2010-02-16
I am getting mixed messages on what ubuntu can and cannot do. Elsewhere ubuntu raid documentation indicates one can 1) take 2 discs, 2) create a single entire-disc partition destined for raid on each, 3) create a single md0 MD software raid1 and 4) put on that single md0 both / and swap.

This is important to do because 1) it is only a single MD partition which greatly simplifies the configuration and maintenance AND 2) it embodies ALL of the ubuntu partitions (like / and swap) so if the disc fails the system will continue to work.

What it appears that lister wants me to do in post #12 is to create multiple raid1 such as md0 and md1 that map to multiple physical partitions on the 2 physical discs in the set. It would be something like this:
md0
      #1    sda partition 1, sdb partition 1 mounted as root
md1
      #1    sda partition 2, sdb partition 2 used as swap
sda
      #1    988 gb ext4
      #2     12 gb swap
sdb
      #1    988 gb ext4
      #2     12 gb swap

I'm pretty sure this would work but it is clearly not a single raid1 MD.

If lister feels I should be able to create the single md0 then I'm a bit confused on the procedure.

darkod in post #14 seems to think the Alternate CD installer can do something I cannot get it to do. Using the Alternate CD I:

1. create a single entire-disc ext4 partition on each of 2 physical 1TB discs.
2. select "create software raid"
3. "create md device" asks only 5 questions:
   a. raid:  1
   b. number of active devices:  2
   c. number of spare:   0
   d. select the sda free #1 and sdb free #1:  check a and b
   e. write the changes?  yes

Notice it NEVER asks for the partition size that it will create for the md0. It in fact results to what is in image #1 in this post. It creates it the same size as the individual member discs' and that is 1 TB.

Once this is done there is no way to 1) change the size or 2) create the swap. Selecting the created raid1 device #0 line in the display and hitting RETURN does nothing but refresh the display. Selecting the raid1 device #0 next line partition #1 and hitting RETURN brings up the screen showing the "use as: do not use". Here one can cursor over it and hit RETURN but this adds nothing other than making it show ext4 for example and then allowing the "format..., mount point... and mount options...". Again, no size stuff. And no adding another partition (such as swap).

As an additional bug report, the Alternate CD partitioning section does NOT allow one to delete any partitions that are set up, possibly wrongly by the user. If the user makes an error or changes their mind they cannot delete anything.

Maybe the ubuntu documentation is WRONG and creating a single md with / and swap just can't be done. I see elsewhere that it is claimed that the LVM can do this. Maybe I will try that next.

thanks,
rich

---

### Post by darkod on 2010-02-16
> **oldunixguy said:**
> 
darkod in post #14 seems to think the Alternate CD installer can do something I cannot get it to do. Using the Alternate CD I:

1. create a single entire-disc ext4 partition on each of 2 physical 1TB discs.
2. select "create software raid"
3. "create md device" asks only 5 questions:
   a. raid:  1
   b. number of active devices:  2
   c. number of spare:   0
   d. select the sda free #1 and sdb free #1:  check a and b
   e. write the changes?  yes



Hold on. Did you write ext4 by mistake in number 1? If not, that's what you're doing wrong.
When you create the single entire-disk partitions for both drives, you mark them as RAID member (don't remember the exact wording right now). You never select the filesystem at this stage. It's in the same menu, under the filesystems you have options for RAID member, LVM member. I think that mght be the problem.

If all is correct, when you create the array, initially it will show it and under need it should say Free Space 1TB, just like it said Free Space for both drives when you were starting all this.
It is at this point that you can select the Free Space, hit Enter and it will open the usual menu for creating partitions and you can select the size, filesystem, mount point, etc.
If you want LVM, you create again single entire-size partition from the RAID1 Free Space but mark it as LVM member.
Then go to Configure LVM and after creating the LVM logical volume, it will add it in partitions list again with Free Space underneath it. It is only now that you create partitions.

To summarize, you only start creating ext4 partitions when the partitioning list looks like:
If using only RAID:

RAID1 device
Free Space 1TB

/dev/sda
raid member

/dev/sdb
raid member

If using RAID+LVM:

LVM device
Free Space

RAID1 device
lvm member

/dev/sda
raid member

/dev/sdb
raid member

---

### Post by darkod on 2010-02-16
Give me few minutes to set up virtual box, I'll give you some exact screenshots. It's gonna be good practice for me too.

---

### Post by darkod on 2010-02-16
I apologize. Leo in post #12 was absolutely right. I have only tried setting up raid+lvm and not only raid.

The thing is:
1. If you want only raid, you have to do like he said in post #12. Create large partition on /dev/sda and mark it as volume for raid (no filesystem at this point, although I think marking it as ext4 will do the same at the end). Then create small partition for swap and mark it as volume for raid too.
2. Do the same for /dev/sdb.
3. Select Configure RAID and create one RAID1 device from the root partitions. Again select configure raid and create another device for the swap partitions.

That should be it. I'm just doing an install in virtual box to see whether it will succeed completely.

If you want to use raid+lvm you can still have one single entire-size partition for the RAID array which can server as volume for LVM. Then the LVM will allow you to create more than one partition on it.

---

### Post by lister171254 on 2010-02-16
Just a few more comments.

It usually makes not much sense to have swap in the RAID as this will slow down disk writes; this is why I usually partition the disks prior to configuring the RAID.

Given that there are two swap partitions in the config I suggest, the system will carry on if one of the disks fails.

leo

---

### Post by darkod on 2010-02-16
If you are still interested in making this work, it seems the main issue is to have /boot partition outside the array.
I tried two installs in VB. First to have only / and swap as separate raid1 devices, the install failed on 85% and also when trying to continue and install grub, it failed that too.
Then I created first a /boot partition outside the array, swap partition also outside because they can be used like that as Leo said, and / partitions on both disks configured as software raid1. That worked right away.

I'm attaching the picture of the partitioner before proceeding with the install.

---

### Post by lister171254 on 2010-02-16
Is there a reason why you want to not mirror boot or you want boot on a different partition, which is not mirrored?

If that's what you want you should be ok, but be aware that you will lose /boot if the disk fails, which is probably not what you want.

Cheers,

leo

---

### Post by darkod on 2010-02-16
If the question was for me, I didn't manage to make it work without separate /boot, in other words if boot is a folder inside / on the array. But it worked when I took /boot out of the array.
I'm new to raid so this was the first step. I'll figure out how to mirror it later hopefully.
Another thing that can create issues is that I'm trying this in VirtualBox and I have only one hdd. Of course, I created 2 virtual disks to play with raid but I'm not sure how VB can handle that on single hdd. I'm new to VB too. :)

---

### Post by crimzon on 2010-07-22
What would happen if one selected "ext4" instead of "raid member" on the individual drives for use in the array? Am I going to have to reinstall for the fifth time this week to get this thing to work properly? =D

Edit:

I keep reading, and I keep getting more confused. Here's what I am going for:

(3) 1TB drives in a software RAID 5 to do video editing in Ubuntu Studio 10.04.

Question is: what is the optimal partition setup for this, including sizes, swaps, boot sectors, boot flags, raid options, etc. I just want the best data throughput possible for HD Video editing. Thanks!

Edit2:

Looks like Ubuntu Developers are smarter than the average bear. The "configure software raid" option in the installer fixed my fubar with the filesystem types. Grub was installed to the MBR of all three drives automatically, so I should be ready to rock.

---

