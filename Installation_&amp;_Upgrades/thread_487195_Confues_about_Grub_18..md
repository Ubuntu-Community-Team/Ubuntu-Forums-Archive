---
title: "Confues about Grub 18."
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by Mike7171 on 2007-06-28
Hi, 

I have been to a lot of sites and forums discussing this problem, but none seem to help. Either they don't have to do with my particular situation, or they are confusing. My problem is that I have installed Ubuntu on my comp. I originally had Windows, and had the intention to dual boot, but something went wrong and I ended up deleting all the partitions other than hda1, and hda2. 

So now, I installed Ubuntu again, and it went smoothly. Everything was fine until I rebooted, and i got the Grub Error 18. I am currently running off of the Ubuntu disc. In terminal, this is the fdisk -l specs:

> Disk /dev/hda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
 
   Device Boot      Start         End      Blocks          Id   System
/dev/hda1   *             1       30233     242846541  83   Linux
/dev/hda2           30234       30515     2265165     5     Extended
/dev/hda5           30234       30515     2265133+   82   Linux swap / Solaris


I have read that the solution is to re-install Ubuntu, but manually set the partition size. They tell me to make a /boot partition at the beginning of the drive at a certain size. This is Chinese to me. I do not understand how to do this. Can someone please help me by putting what I am supposed to do in very simple terms, as I do not know much about computers.

Thank you,
Mike7171

---

### Post by confused57 on 2007-06-28
Here's some possible solutions for grub error 18:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)
setting up a separate /boot partitions is the usual method, but you might want to try one of the other methods first, e.g. set bios controller to "auto".

It's relatively easy to install & set up a separate /boot partition...select the manual partitioning option...you could start by deleting the partitions that you have with the partitioner...click on the unallocated space & select new partition(or you can move the slider),  make the partition approximately 200 Mb, format as ext2, click on the drop-down menu for mountpoint select /boot, select primary partition.
Then create another partition for root, make it approximately 20 Gb, mountpoint /, format as ext3, select primary partition.
You would then need to create a /home partition, size it to all but approx. 1-2 Gb, set the mountpoint as /home, format as ext3, select primary partition.
The last partition in the remaining unallocated space would be your swap partition, set the mountpoint as swap, it's not really formatted(it may give you an option to format as swap), make it a logical(or extended partition).

When you're finished, the installer will summarize your selections:
1.) /boot...200 Mb, format as ext2, primary partition
2.)/.........20 Gb, format as ext3, primary partition
3.)/home....all but 1-2 Gb of remaining disk space, format as ext3, primary partition
4.)swap....1-2 Gb, mountpoint swap, formatted as swap?, logical(or extended) partition.

I always use the alternate installer, but this should give you some idea of how to do manual partitioning with the desktop install cd,  here's an excellent guide:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

By having an extended partition, you can always shrink your /home partition and create new logical partitions within the extended partition.

---

### Post by Mike7171 on 2007-06-28
In my BIOS I can not seem to find the Bios Controller setting. Im not sure how old my computer is, so maybe that causes a difference. The Bios is called AwardBIOS. 

So I am about to try the partition editing method. Hopefully that will work. 
Ill let you know how it goes, 
Thank you alot for your help!

Mike7171

---

### Post by Mike7171 on 2007-06-28
I deleted the partitions and am creating a boot one. Problem is that there is nothing in the drop-down menu for mountpoint. Should I just write "/boot"?

---

### Post by confused57 on 2007-06-28
> **Mike7171 said:**
> I deleted the partitions and am creating a boot one. Problem is that there is nothing in the drop-down menu for mountpoint. Should I just write "/boot"?
Yes, try typing in "/boot", without the quotes...it "should" work OK.

---

### Post by Mike7171 on 2007-06-28
I am getting an error when I try to create the Swap partition. It says "Cannot have End before the Start" or something like that,

---

### Post by confused57 on 2007-06-28
> **Mike7171 said:**
> What size should the Swap partition be?
It really depends on how much memory you have...if you have 1-2 Gb memory, then 1 Gb should be sufficient, if you have 512 Mb or less, then I'd say 1.5 Gb swap.

---

### Post by Mike7171 on 2007-06-28
> **confused57 said:**
> It really depends on how much memory you have...if you have 1-2 Gb memory, then 1 Gb should be sufficient, if you have 512 Mb or less, then I'd say 1.5 Gb swap.

Alright. Changed the size, and the error is gone. There is Free Space in between the /home partition and the Swap one though, Is this alright?

---

### Post by confused57 on 2007-06-28
> **Mike7171 said:**
> Alright. Changed the size, and the error is gone. There is Free Space in between the /home partition and the Swap one though, Is this alright?
It won't hurt anything, as long as everything is working...you can always resize your /home partition to take up the unallocated space...I wouldn't suggest doing this right yet, until you're a little more experienced with Ubuntu, because it will change your /home filesystem's UUID...it's not difficult to make the change, but you might not want to attempt it just yet...how much unallocated space are we talking about?

---

### Post by Mike7171 on 2007-06-28
228267 Mb.

---

### Post by confused57 on 2007-06-28
> **Mike7171 said:**
> 228267 Mb.

Not quite what I expected, if you made the /home partiton the remainder of the unallocated space, except for 1.5 Gb for swap...open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
-l is a small "L"

Also, post the output of:
```
gedit /etc/fstab
```

---

### Post by Mike7171 on 2007-06-28
The output of fdisk is the same as before because the changes have not been made yet. I am doing all of this in the Ubuntu installer Partition step.

Outpost for fdisk:

> Disk /dev/hda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30233   242846541   83  Linux
/dev/hda2           30234       30515     2265165    5  Extended
/dev/hda5           30234       30515     2265133+  82  Linux swap / Solaris



Outpost for fstab:

> 
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hda5 swap swap defaults 0 0

(Those cirlces at the end have dots in them. I'm not sure how to post codes like you did.)

---

### Post by confused57 on 2007-06-28
Whew, that makes it a lot easier...select  to create a new partition in the unallocated space, use the entire space(if you've already made your swap partition)...set the mountpoint as /home, format as ext3, and choose primary partition(you could actually choose logical or extended, it doesn't really matter)...the main thing is that your swap is set as logical.

Check back over my first reply for what your partition layout will be...

Added:  If you've already designated a /home partition, just use the slider to enlarge the partition to use the entire space...make sure you have /boot, / , /home, and swap partitions setup with these mountpoints.

---

### Post by Mike7171 on 2007-06-28
So i create a new /home one along with the one that I already made?

That outpost I sent you is from before. My changes have not been made yet.

In my Installer, I have as follows:

hda1   ext2   /boot      197 MB
hda2   ext3   /            20480 MB
hda3   ext3   /home    1019 MB
FREE SPACE
hda5   swap               1028 MB

I just want to make sure I get this right. I was up until 5 am this morning trying to fix things.

---

### Post by confused57 on 2007-06-28
> **Mike7171 said:**
> So i create a new /home one along with the one that I already made?

That outpost I sent you is from before. My changes have not been made yet.

In my Installer, I have as follows:

hda1   ext2   /boot      197 MB
hda2   ext3   /            20480 MB
hda3   ext3   /home    1019 MB
FREE SPACE
hda5   swap               1028 MB

I just want to make sure I get this right. I was up until 5 am this morning trying to fix things.

Use the slider or you should be able to right click on the /home partition to resize, so that you can use the rest of the FREE SPACE for your entire /home partition...no, you're not creating another /home, you're just making the one that you have "much" larger, which is the benefit of having a separate /home..**..it might be best to delete the swap partition(for now), expand the /home partition to all but 1028 Mb, then create a new swap partition on the 1028 Mb.**

---

### Post by Mike7171 on 2007-06-28
I deleted the swap partition and the /home one (there is no slider in the installer Manual section to change size one it is already chosen), to make a new /home one. I am trying to make it so it takes up all the remaining space except 1028 MB like you said, but it gives me and error saying "Cannot have end before the start"

The only thing that has a slider is the Gnome Partition Edititor, but I am doing all of this in the Ubuntu Installer step 4 in the Manual part.

---

### Post by confused57 on 2007-06-28
> **Mike7171 said:**
> I deleted the swap partition and the /home one (there is no slider in the installer Manual section to change size one it is already chosen), to make a new /home one. I am trying to make it so it takes up all the remaining space except 1028 MB like you said, but it gives me and error saying "Cannot have end before the start"

The only thing that has a slider is the Gnome Partition Edititor, but I am doing all of this in the Ubuntu Installer step 4 in the Manual part.
Can you go back in the installer to the Gnome Partition Editor?  If you can't, it might be easier to start the installation over...you already have the /boot partition and / partitions setup, you'd still need to reset the mountpoints, filesystem, primary partition again, but you should be able to start over with your swap & /home...instead this time, make your swap(1024 Mb, mountpoint swap, logical)  before you set up  your /home, then you can use the rest of the FREE SPACE for your /home, setup the way I mentioned earlier(ext3, primary, /home).

Sounds like you've already partitioned and are on the next step, so in my opinion, starting the install over would be the easiest...maybe someone more experienced with the live cd installer would know an easier way?

Added:  It's not necessary to have a separate /home partition...if you feel more comfortable just setting up  /boot, /, and swap partitions, that's your option.

---

### Post by Mike7171 on 2007-06-28
The only problem that seems to be happening is that when I try to make the /home partition in the installer, it gives me the "Cannot have end before start" error.

I have my /boot, /, and swap partitions. Theres 229287 MB of free space in between / and swap, which is where im trying to put /home, but I keep getting that error.

---

### Post by confused57 on 2007-06-28
> **Mike7171 said:**
> The only problem that seems to be happening is that when I try to make the /home partition in the installer, it gives me the "Cannot have end before start" error.

I have my /boot, /, and swap partitions. Theres 229287 MB of free space in between / and swap, which is where im trying to put /home, but I keep getting that error.
I believe it has something to do with the physical location on the hard drive of the partitions, in relation to each other, if that makes any sense.  I would have thought your /boot would be at the very beginning, then /, /home, and swap...in that order, as far as the physical location on the disk and it should show up this way in the Gnome Partition Editor.

It still might be easier to start over with the installation & partitioning, keeping this in mind....but if you start over, I'd set it up:  /boot, /, swap, /home....unless someone else might see a problem with this.

---

### Post by Mike7171 on 2007-06-28
I did start the installation over. But should I be doing all of this in the Gnome Partition Editor instead of the Installation?

---

### Post by confused57 on 2007-06-29
> **Mike7171 said:**
> I did start the installation over. But should I be doing all of this in the Gnome Partition Editor instead of the Installation?
Yes, I would think so...gparted is the part of the installer where you set up your partitions, before the actual installation of Ubuntu.  With gparted, you should be able to partition your hard disk as I described...your primary aim is to set up a separate /boot partition at the beginning of the hard drive, whether you want a separate /home or not is up to you...if you'll look at your output of "sudo fdisk -l", all you'd really need is another partition at the beginning of the hard disk for /boot(but you'd need to repartition to do this)...  Sorry for my not communicating what you need to do clearly enough.

---

### Post by Mike7171 on 2007-06-29
It's not your fault, I should of realized. I greatly appreciate all of this help. 
So, in Gnome, when I create a new partition, I can not choose the mountpoint. So I have another problem going, I also can not delete hda2 (extended) and 5 (linux swap)

---

### Post by Mike7171 on 2007-06-29
In the installation, I figured out that the error is caused when I make the /home partition with a very large size. So Im guessing that I will have to leave free space?

---

### Post by confused57 on 2007-06-29
> **Mike7171 said:**
> It's not your fault, I should of realized. I greatly appreciate all of this help. 
So, in Gnome, when I create a new partition, I can not choose the mountpoint. So I have another problem going, I also can not delete hda2 (extended) and 5 (linux swap)

I'm definitely fumbling with the desktop live cd installer...wouldn't have any problem with the alternate cd, but I think we can get you through the install.  Don't worry about deleting the  swap, especially since it's located at the very end of the disk.
I thought you might be able to set mountpoints in gparted, but you may only be able to do that in the next step after you create your partitions.  For now, you might want to just create a /boot partition(ext2 or ext3) and a / partition(ext3) and you should be able to use the same partition for swap(currently hda5(within extended partition hda5).  

I'm not sure if I would have been able to manually partition for Ubuntu on the day that I first installed it, probably not.

Added:  Just saw your last reply...how large does the partitioner allow you to make your /home partition?

---

### Post by Mike7171 on 2007-06-29
So heres what's happening so far. In Gnome Partition Editor, I now have

hda1 - ext2 - 196 MB 
hda3 - ext3 - 20 GB
Unallocated
hda2 - extended
hda5 - linux swap

ADDED: (saw last reply) Im not sure. I accidentaly set it to 1028 mb, but thats how much I wanted remaining. It worked. Then I realized what I did, Set it back to taking up all the space but 1028, and it got that error.

---

### Post by confused57 on 2007-06-29
> **Mike7171 said:**
> So heres what's happening so far. In Gnome Partition Editor, I now have

hda1 - ext2 - 196 MB 
hda3 - ext3 - 20 GB
Unallocated
hda2 - extended
hda5 - linux swap

ADDED: (saw last reply) Im not sure. I accidentaly set it to 1028 mb, but thats how much I wanted remaining. It worked. Then I realized what I did, Set it back to taking up all the space but 1028, and it got that error.

Can you just right-click on the unallocated space and select "create new partition"(ext3), or something to that effect?  Then in the next step, you should be able to set the mountpoint as /home.

---

### Post by Mike7171 on 2007-06-29
How do I change them to /boot or /home? What is the next step. Do I right-click them or something? I made the first one Boot by right-clicking and going to "manage flags" and clicking Boot. There are no choices for Home or Root however,

---

### Post by confused57 on 2007-06-29
> **Mike7171 said:**
> How do I change them to /boot or /home? What is the next step. Do I right-click them or something?
If you have your partitions set up, there should be a step that you can set the mountpoint(s) and how you want the partitions formatted...if your partitions are already formatted, then the next step "should" allow you to select your mountpoints.../boot, /, /home, swap.  Once these are set, then the installer should proceed.

Added:  You only need to set the boot flag on the /boot partition.

---

### Post by Mike7171 on 2007-06-29
Oh, I've been setting them up in Gnome Partition Editor. They are set up in there, with the right space (I think), so If I go into the installer, it should detect my changes?

Then I would have to figure out how to mountpoint them in there.

---

### Post by Mike7171 on 2007-06-29
Alright, So I started the Install over again, and it detected my changes. Everything is perfect now! I just need to make sure the sizes are all right. Here they are:

hda1 - ext2 - boot - 205 MB
hda3 - ext3 - / - 21476 MB
hda4 - ext3 - /home - 225602 MB
FREE SPACE - 1390 MB
hda5 - swap - 2319 MB

If this is all good, should I install?

---

### Post by confused57 on 2007-06-29
> **Mike7171 said:**
> Alright, So I started the Install over again, and it detected my changes. Everything is perfect now! I just need to make sure the sizes are all right. Here they are:

hda1 - ext2 - boot - 205 MB
hda3 - ext3 - / - 21476 MB
hda4 - ext3 - /home - 225602 MB
FREE SPACE - 1390 MB
hda5 - swap - 2319 MB

If this is all good, should I install?
Everything looks good...I assume you meant the mountpoint for hd1 to be /boot, not boot:
```
hda1 - ext2 - **/boot** - 205 MB
hda3 - ext3 - / - 21476 MB
hda4 - ext3 - /home - 225602 MB
FREE SPACE - 1390 MB
hda5 - swap - 2319 MB
```

You need to make sure it is actually set as mountpoint /boot, not boot.
Otherwise, everything else looks good...

---

### Post by Mike7171 on 2007-06-29
Oh, sorry. It is " /boot ", I didn't type the slash in here.

I'll let you know what happens after the install and reboot.

---

### Post by confused57 on 2007-06-29
> **Mike7171 said:**
> Oh, sorry. It is " /boot ", I didn't type the slash in here.

I'll let you know what happens after the install and reboot.

Good luck, hope everything works...fingers crossed.

---

### Post by Mike7171 on 2007-06-29
Ah, now another problem. I hit "Forward" to continue with the installation, and it gave me an error saying something was incompatible, then this"

> The test of the file system with type ext2 in partition #1 of IDE1 master (hda) found uncorrected errors.

If you do not go back to the partitioning menu and correct these errors, the partition will be used as is.

---

### Post by confused57 on 2007-06-29
> **Mike7171 said:**
> Ah, now another problem. I hit "Forward" to continue with the installation, and it gave me an error saying something was incompatible, then this"

You could go back and change the filesystem to ext3, if this is the incompatibility error....ext2 "should" work, that's what's used in Gentoo for the /boot partition, if you want to take a chance on continuing...might be best to go back & change it?

---

### Post by Mike7171 on 2007-06-29
Tried changing it to ext3 and moving on, and this came up:

> The file system on /dev/hda3 assigned to / has not been marked for formatting. File systems used by the system (/, /boot, /usr, /var) must be reformatted for use by this installer. Other file systems (/home, /media/*, /usr/local, etc.) may be used without reformatting.

So I guess it has to stay ext2

---

### Post by confused57 on 2007-06-29
> **Mike7171 said:**
> Tried changing it to ext3 and moving on, and this came up:



So I guess it has to stay ext2

All of your partitions, except possibly for swap, need to be selected(checked) for formatting, after you have made your partitions in gparted.  The summary screen after you have selected you partitions have a check box that you need to check to be formatted...if you don't select to format, then your previous install's data will not be overwritten when it's reformatted.

You might want to see these links:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://img379.imageshack.us/my.php?image=feistydual10ea7.png](http://img379.imageshack.us/my.php?image=feistydual10ea7.png)

It's almost 2 AM, I may have to be getting to bed shortly...there are some excellent guides in the 2nd link in my signature, that you might want to check out if you have problems.  Again, good luck and I'll be checking back in later on this morning to see how you're doing.  There are many competent people in the forum who will be able to assist you, if I happen not to be logged in to the forum, or even if I am.

---

### Post by Mike7171 on 2007-06-29
I left it as ext2, and checked all of the boxes. It finally let me move on to the next step. This hopefully might be it!:D

Added: In case it doesn't finish before you leave, Thank you for your help. Every time I try to do something on a computer it messes up. Endless problems. Anyway, Ill post what happens once it's all done.

---

### Post by Mike7171 on 2007-06-29
Just letting you know that it worked perfectly! Ubuntu is up and running! Again, thank you so much for your help. I greatly appreciate it,

---

### Post by confused57 on 2007-06-29
> **Mike7171 said:**
> Just letting you know that it worked perfectly! Ubuntu is up and running! Again, thank you so much for your help. I greatly appreciate it,

Good job...manual partitioning during install is definitely a challenge for a rookie, I didn't even know what a partition was when I first installed Ubuntu.  You'll learn more about Linux and computers than you ever thought you would and it'll be fun at the same time.

You're probably an expert now, as far as installing Ubuntu.  After you've been using Ubuntu for a period of time, you'll have it customized and configured and you'll have data stored in your /home partition...if you ever have to reinstall for some reason, just don't check the box to format your /home partition and your settings/data will be preserved...you'd still need to format /boot & /, but but you'd retain your settings...enjoy using Ubuntu.

---

### Post by Mike7171 on 2007-06-29
Thanks for the tips! I'll have things figured out soon enough.

---

