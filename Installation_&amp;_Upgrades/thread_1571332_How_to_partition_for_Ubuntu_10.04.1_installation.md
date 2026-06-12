---
title: "How to partition for Ubuntu 10.04.1 installation??"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by virsto on 2010-09-09
I have now reached a point in the installation of Ubuntu 10.04.1 (64-bit) for dual-boot with Windows 7 where I need help, urgently!
'
During the setup for the installation of Ubuntu (using the **Ubuntu-10.04.1-desktop-amd64.iso** cd), I reached the step where it need to prepare partitions and I am faced with the following:
  
**/dev/sda1**
 *type*--ntfs
* size*--208 MB
 *used*--69 MB
**/dev/sda2**
 *type*--ntfs
 *size*--619875 MB
* used*--75957 MB
**/dev/sda**3
* type*--ntfs
* size*--19939 MB
* used*--16713 MB
**/dev/sda4**
 *type*--fat32
 *size*--108 MB
* used*--33 MB

I would like to install Ubuntu in **/dev/sda2** as a dual-boot with Windows 7 which now occupies a small part of this partition. How can I accomplish this without risking a problem with my Windows 7 installation?

Note, in the previous window during installation I was given only the choice of using the entire drive or partitioning! I actually thought I should be given a choice that allowed installation side-by-side with Windows 7 (i.e., dual-boot system)--- but this was not the case!.

I then went back into Win7 and shrunk the C: partition (see attachment) then rebooted into Win7 several times. I then tried again to install Ubuntu 10.04.1. I get to step 4 of 7 (Prepare disk space) and I am again faced with the choice of:

 * Erase and use entire disk
or,
   Specifiy partitions manually (advanced)

Clearly, I choose the second one, but, again I am faced with how to use the free disk space??

Help would be greatly appreciated.

---

### Post by ronparent on 2010-09-09
The first problem is that it appears that all four of your partitions are primary - what you will run into is that you won't be able to create the swap because you are limited to four primary partitions on one disk. What you have to do is to create an extended partition. The biggest problem may be that if your partition sizes are actually as quoted, you may not have enough room for a full install of Ubuntu. In terms of newer systems a Ubuntu install including swap would be modestly served by 4 GB of disk space. If your space is as indicated your computer would probably be approaching ten or more years and there may be more serious system limitations. Give us more information and someone should be able to advise you.

---

### Post by virsto on 2010-09-09
> **ronparent said:**
> The first problem is that it appears that all four of your partitions are primary - what you will run into is that you won't be able to create the swap because you are limited to four primary partitions on one disk. What you have to do is to create an extended partition. The biggest problem may be that if your partition sizes are actually as quoted, you may not have enough room for a full install of Ubuntu. In terms of newer systems a Ubuntu install including swap would be modestly served by 4 GB of disk space. If your space is as indicated your computer would probably be approaching ten or more years and there may be more serious system limitations. Give us more information and someone should be able to advise you.

Ok thanks for answering my distress call :p

I do have plenty of "free disk" space; but, I don't know how to tell the installer how to use it. I actually thought that the installation software would be able to figure this out easily, since there is plenty of free disk space, just waiting for a full installation of Ubuntu 10.04.1. Note, I was able to install with Wubi on this same system with very little installation problems (once I had a direct cable connection to the internet). I unstalled this Wubi installation before trying to get a full installation of 10.04.1 --- this is where I started having problems and I do not understand why, I thought this should go very smooth. :(

--V

---

### Post by virsto on 2010-09-09
If one goes to [http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)
one will find...

> After shrinking the Windows partition, you should reboot once into  Windows prior to installing Ubuntu or further manipulating the  partitions. This allows the Windows system to automatically rescan the  newly-resized partition (using chkdsk) and write changes to its own  bootup files. (If you forget to do this, you may later have to repair  the Windows partition bootup files manually using the Windows Recovery  Console.) 
If done this way, there is no problem installing Ubuntu as the  second operating system and it is done automatically from the Ubuntu  LiveCD. Allow the Ubuntu LiveCD to install to "largest available free  space." 
I did follow this recipe; but, this just did not happen --- install to "largest available free space" was never an option for me!

--V

---

### Post by Pumalite on 2010-09-09
[http://www.pcnineoneone.com/howto/clean3.html](http://www.pcnineoneone.com/howto/clean3.html)

---

### Post by ronparent on 2010-09-09
OK I see that the disk space is GB rather than MB. 4 GB should be plenty for an install with 2 GB or so for the swap. Win7 apparently allows you to create more than four primary partitions (your screen shot) but ubuntu won't. What you have to do is to get at least one of the primary partition into an extended partition along with enough unallocated space to create the partition you want to install to and a swap. This could get complicated.

I don't believe I was ever able to find a way to create an extended partition with Win7. Gparted will in a live cd, but, won't until you can winnow four partitions down to three. Hopefully you won't have to move your other two partitions to make room for an extended at the end of the drive. Then the extended partition could be created to fill the unallocated space. Are you really ready to face all this to install Ubuntu into its own space (you could continue to use wubi)?

Edit: I just saw your latest post. The basic problem you face now is that with four primary partitions already on the disk, the installer will not allow you to create another.

---

### Post by virsto on 2010-09-09
> **ronparent said:**
> OK I see that the disk space is GB rather than MB. 4 GB should be plenty for an install with 2 GB or so for the swap. Win7 apparently allows you to create more than four primary partitions (your screen shot) but ubuntu won't. What you have to do is to get at least one of the primary partition into an extended partition along with enough unallocated space to create the partition you want to install to and a swap. This could get complicated.
 
I don't believe I was ever able to find a way to create an extended partition with Win7. Gparted will in a live cd, but, won't until you can winnow four partitions down to three. Hopefully you won't have to move your other two partitions to make room for an extended at the end of the drive. Then the extended partition could be created to fill the unallocated space. Are you really ready to face all this to install Ubuntu into its own space (you could continue to use wubi)?
 
Edit: I just saw your latest post. The basic problem you face now is that with four primary partitions already on the disk, the installer will not allow you to create another.
 
Ok,
I have used Win7 to extend the C: partition (see attached screenshot), rebooted twice into Win7 withoit problems. I then started the Ubuntu install again --- same problem! It either wants the entire disk or for me to manually parttion it (which I do not understand how or why I need to do this). In anycase, I have been unable to get good/correct information on how do perform this manual partitioning. 
 
I am now considering the abandonment of Ubuntu on my laptop --- I have spent many, many hours on good installations, both with Wubi and now with the full installation. I just can not understand why my system does not respond as the instructions given for the full installation say it should??
 
--V
 
PS. Please note, that I did have a full Ubuntu 10.04 installed on this same system (no hardware differences) a few days ago, until I was unable to boot it (see some of my earlier postings on this). I actually had been working with it for over a month and the installation was done from the downloaded CD (for 10.04 64-bit). So again, I just can not understand why I am unable to install 10.04.1 using the same configuration as I had earlier. This has been an extremely frustrating experience with Ubuntu --- first being unable to boot to 10.04 and then unable to install 10.04.1.
 
This brings up a fundamental question --- Is the installation of Ubuntu really that reliable for dual-boot with Windows 7?

---

### Post by virsto on 2010-09-09
> **Pumalite said:**
> [http://www.pcnineoneone.com/howto/clean3.html](http://www.pcnineoneone.com/howto/clean3.html)
 
But, I do not believe that this link and information is applicable to my problem.
 
Thanks for taking a look at my problem.
 
--V

---

### Post by ronparent on 2010-09-09
You are apparently either unwilling or can'r count to four!

---

### Post by virsto on 2010-09-09
> **ronparent said:**
> You are apparently either unwilling or can'r count to four!
 
But, as I stated in my previsou posting. **I have had the full 10.04 version running in dual-boot mode on the same hardware and same disk partitioning (4 partitions) that is now present and which now does not allow me to install the full 10.04.1 release!**
 
Sorry, but I do not know how to state this more clearly.
 
--V

---

### Post by Hobgoblin on 2010-09-09
> **virsto said:**
> Ok,
I have used Win7 to extend the C: partition (see attached screenshot), rebooted twice into Win7 withoit problems. I then started the Ubuntu install again --- same problem! It either wants the entire disk or for me to manually parttion it (which I do not understand how or why I need to do this).
Because it cannot create another primary partition as you have reaced the limit (4).

>  In anycase, I have been unable to get good/correct information on how do perform this manual partitioning. 

Because it seems HP have in their infinite wisdom made it impossible.
 
> 
PS. Please note, that I did have a full Ubuntu 10.04 installed on this same system (no hardware differences) a few days ago, until I was unable to boot it (see some of my earlier postings on this). 
Was that a wubi install? If so that might be your answer.
 
> This brings up a fundamental question --- Is the installation of Ubuntu really that reliable for dual-boot with Windows 7?

Yes, if the manufacturer of the PC hasn't knobbled it by creating 4 primary partitions on the HDD.

---

### Post by virsto on 2010-09-09
> **Hobgoblin said:**
> Because it cannot create another primary partition as you have reaced the limit (4).
 
 
 
Because it seems HP have in their infinite wisdom made it impossible.
 
 
Was that a wubi install? If so that might be your answer.
 
 
 
Yes, if the manufacturer of the PC hasn't knobbled it by creating 4 primary partitions on the HDD.
 
But, your statements about the limitations on number of partitions can not be true since I have had the full 10.04 running on my current system with four partitions. Note, this was before a Wubi type installation was possible! 
 
I will give a summary of main events that I believe are relative to my problem and also relative to some of the responses that I have so far received:
 
1. Thie laptop that I have been using for the past 6 months has not changed.
 
2. My first Ubuntu (10.04) was installed a few months ago without any problems of the type that I am experiencing now (e.g. with the partitioning)
 
3. Later, after boot failures with the installed 10.04 (see earlier posting on this), I installed 10.04.1 with Wubi and it worked ok.
 
4. I removed the Wubi Ubuntu file using Windows 7 to uninstall it --- this was successful.
 
5. During this time, from the first installation of 10.04, and later when Wubi was used to install 10.04.1, **no changes were made to the partitioning, no changes were made to the hardware -- NONE! **This means that both 10.04 (full installation) and the Wubi installation, which created a Ubuntu file in the C: partition, were both working with four partitions!
 
6. Then (AFTER THE PROBLEM with the installation of 10.04.1) I shrunk partition C: and tried to install (see my previous postings).
 
7. I have now restored the original partitioning (extending C: to four); but, as you now know, I am still unable to install the full 10.04.1, even though 10.04 installed with no glitches for the same partitioning!
 
I am sorry if this was not clear earlier. I hope it is now.

---

### Post by oldfred on 2010-09-09
This will tell what is where. From liveCD download & run this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by srs5694 on 2010-09-09
> **virsto said:**
> But, your statements about the limitations on number of partitions can not be true

I'm afraid you're almost certainly mistaken. See the [Wikipedia article on the Master Boot Record (MBR)](http://en.wikipedia.org/wiki/Master_boot_record) partitioning scheme, which is used by most non-Apple computers today. MBR is limited to either four primary partitions or three primary partitions and an arbitrary number of logical partitions. Although there are ways around these limitation (see below), AFAIK none of them has been used by HP on its computers.

> since I have had the full 10.04 running on my current system with four partitions. Note, this was before a Wubi type installation was possible!

I see several possible explanations; in order of decreasing probability:


[list=1]
[*]This was a WUBI install, which puts Linux inside a file in a Windows partition. I'm not sure when WUBI became available, but it was long before Ubuntu 10.04, so if it was a 10.04 installation, it could have been a WUBI installation, despite what you seem to think. You wouldn't be the first person to have a WUBI install and not realize it.
[*]Your partitioning scheme changed between the time you had Linux installed and now, and you're simply unaware of that fact.
[*]You installed Linux to another physical hard disk.
[*]Your computer uses GPT rather than MBR partitions. This is unlikely, but not impossible. GPT has a limit of 128 partitions by default (the limit can be raised to arbitrary levels with appropriate software).
[*]You used a weird boot loader that rewrites the partition table with each boot, to swap more than four primary partitions in and out of the four available MBR partition "slots." I've never used such a boot loader, but I've heard of them; they were moderately common in the Windows 9x/Me days, but seem to have faded into obscurity since then. This explanation also implies explanation #2.
[/list]

 
> 7. I have now restored the original partitioning (extending C: to four); but, as you now know, I am still unable to install the full 10.04.1, even though 10.04 installed with no glitches for the same partitioning!

What do you mean by "extending C: to four"?

As I see it, you've got a few options for how to install Ubuntu:


[list=1]
[*]Perform a WUB install of Ubuntu.
[*]Install Ubuntu to another hard disk.
[*]Delete one of your existing partitions, create an extended partition in its place, and install Ubuntu in logical partitions inside the extended partition. Depending on what partition you delete, you might need to move/resize other partitions to get a nice contiguous chunk of free space.
[*]Convert a partition into a logical partition inside an extended partition, thus enabling creation of additional logical partitions. I don't know of any point-and-click tools to do this conversion, but it is possible. It may require resizing at least one partition to make room for the necessary data structures.
[*]Wipe out everything on the disk; re-install Windows from a standard Windows disc (not from the computer's restore disc), which will give you an install on just one or two partitions; and install Ubuntu on this new system.
[/list]


Concerning option #3, it's likely that you can delete D: or E: with few or no repurcussions; however, you'd be wise to back it up before attempting this. If I'm correct, D: contains the equivalent of your Windows installation DVD, and there's probably a utility on your hard disk that will create physical DVDs from its contents. If you haven't already done so, you should run this utility (whatever else you do) so that you'll have physical restore media in case your hard disk dies. With these media in hand, D: becomes superfluous. I'm not entirely sure what E: is, but it's likely extra tools that HP included with the computer. You should be able to copy these tools to another location, but you should check them out yourself to be sure.

---

### Post by virsto on 2010-09-10
> **srs5694 said:**
> I'm afraid you're almost certainly mistaken. See the [Wikipedia article on the Master Boot Record (MBR)]("http://en.wikipedia.org/wiki/Master_boot_record") partitioning scheme, which is used by most non-Apple computers today. MBR is limited to either four primary partitions or three primary partitions and an arbitrary number of logical partitions. Although there are ways around these limitation (see below), AFAIK none of them has been used by HP on its computers.
 
I see several possible explanations; in order of decreasing probability:
 

[LIST=1]
[*]This was a WUBI install, which puts Linux inside a file in a Windows partition. I'm not sure when WUBI became available, but it was long before Ubuntu 10.04, so if it was a 10.04 installation, it could have been a WUBI installation, despite what you seem to think. You wouldn't be the first person to have a WUBI install and not realize it.
[*]Your partitioning scheme changed between the time you had Linux installed and now, and you're simply unaware of that fact.
[*]You installed Linux to another physical hard disk.
[*]Your computer uses GPT rather than MBR partitions. This is unlikely, but not impossible. GPT has a limit of 128 partitions by default (the limit can be raised to arbitrary levels with appropriate software).
[*]You used a weird boot loader that rewrites the partition table with each boot, to swap more than four primary partitions in and out of the four available MBR partition "slots." I've never used such a boot loader, but I've heard of them; they were moderately common in the Windows 9x/Me days, but seem to have faded into obscurity since then. This explanation also implies explanation #2.
[/LIST]
 
I was not aware of a Wubi being available that early, but, **I am positive that it was not a Wubi installation.** Why? 1) I had a very large free area for my Ubuntu after the installation which was over 200 GB, and 2) The first menu presented during installation of Wubi is quite different from the one presented when installing the normal 10.04 and 10.04.1. This means that 1. was not the case. Your 2. is possible. I have no other physical disk on my laptop (this was made clear in my early postings), so 3. is not possible for me. I agree that 4. is very, very unlikely. I am unfamiliar with the use of boot loaders, and I have certainly not ever tried to change anything related to the bootloader, so I believe that this makes 5. very unlikely also.
 
>  
What do you mean by "extending C: to four"?

 
This was not worded well. I should have said that I just returned the partitioning to 4 after shrinking C: so that 5 were present (as shown in one of the attached screen shots). Now, after "extending C:" in Win7, I have restored the original 4 partitions as given in the last screen shot attached.
 
> 
As I see it, you've got a few options for how to install Ubuntu: 

[LIST=1]
[*]Perform a WUB install of Ubuntu.
[*]Install Ubuntu to another hard disk.
[*]Delete one of your existing partitions, create an extended partition in its place, and install Ubuntu in logical partitions inside the extended partition. Depending on what partition you delete, you might need to move/resize other partitions to get a nice contiguous chunk of free space.
[*]Convert a partition into a logical partition inside an extended partition, thus enabling creation of additional logical partitions. I don't know of any point-and-click tools to do this conversion, but it is possible. It may require resizing at least one partition to make room for the necessary data structures.
[*]Wipe out everything on the disk; re-install Windows from a standard Windows disc (not from the computer's restore disc), which will give you an install on just one or two partitions; and install Ubuntu on this new system.
[/LIST]
 
I can easlily do 1. (at least I have done this several times now with no problems). But the limited size is a real problem. I am handling sets of very large biomedical data (e.g. EKG, EEG) and I need at least 100 GB in the File System. I did look up documentation on this and found that extending the size occupied on the C: partition is not supported in 10.04, so I dropped this approach. In addition I believe that the Wubi installation runs a little slower than the normal installation --- this could be a problem in the future. 
 
I do not see 2. as a possibility for me --- adding another physical disk to my laptop is not something for me. However, I do have several rather large external (USB) hard drives --- is this a possibility?
 
3. is possible, but I would certainly need some guidance on this.
 
4. perhaps, but again, I would need some guidance to accomplish this (if it is possible).
 
5. is not possible since I do not hae standard Windows 7 CDs or DVDs for installation, and I know of no way to reinsntall it after it has been erased.
 
 
>  
Concerning option #3, it's likely that you can delete D: or E: with few or no repurcussions; however, you'd be wise to back it up before attempting this. If I'm correct, D: contains the equivalent of your Windows installation DVD, and there's probably a utility on your hard disk that will create physical DVDs from its contents. If you haven't already done so, you should run this utility (whatever else you do) so that you'll have physical restore media in case your hard disk dies. With these media in hand, D: becomes superfluous. I'm not entirely sure what E: is, but it's likely extra tools that HP included with the computer. You should be able to copy these tools to another location, but you should check them out yourself to be sure.
/QUOTE]
 
--Thanks very much for digging into my problem, and I will definitely look into your suggestions on removing D: and E: --- this looks promising :)
 
I have not given up yet ;)
--V

---

### Post by virsto on 2010-09-10
> **oldfred said:**
> This will tell what is where. From liveCD download & run this:
 
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

 
Ok I will try this, but at the moment I do not have Ubuntu on my sysem (as stated in my previous posting). However, I will try to install with Wubi again and follow the instructions given at this URL.
 
>  
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

 
Thanks very much for this tip. I wll return on this...

---

### Post by virsto on 2010-09-10
I was just on the phone with HP technical support and let me summarize some things that came out of this conversation and is relevant to this problem:
 
1. My particular model of the HP pavilion laptop was delivered with 4 partitions as exists now.
2. Partitiion D: (recovery) can be removed. However, I they recommended that I make DVDs of this for recovery --- this I am doing now.
3. I plan to Delete partition D: after this has finished.
 
--V

---

### Post by oldfred on 2010-09-10
You do not need to install wubi to run the script. You often run it from a liveCD which you will need to have to do any install. If just starting out you do not need to run it now.

I prefer the elimination of a partition and installing at least / (root) and swap. If you are going to share with windows you may want to have a NTFS partition for shared data. You can read & write the windows C: partition but I only suggest reading from any system partitions with foreign systems except for repairs. Many windows users suggest a separate data partition so when you have to reinstall your system your data is separate. Of course you still need backups.

You can install to an external drive. It will be a little slower as the USB connection is not as fast as a SATA internal drive connection.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
Full Disk install Lucid Graphical
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Use windows tools to shrink the windows partition. You can then use the auto install into free space or if you want to create partitions in advance you can use gparted and then manual install to choose which partition is root.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by srs5694 on 2010-09-10
> **virsto said:**
> This was not worded well. I should have said that I just returned the partitioning to 4 after shrinking C: so that 5 were present (as shown in one of the attached screen shots). Now, after "extending C:" in Win7, I have restored the original 4 partitions as given in the last screen shot attached.

Just to clear up some confusion: Neither of your screen shots shows five partitions on a single disk. One of them gives that impression because it shows four partitions and a large unallocated space. That unallocated space, though, is *not* a partition -- that's why it's called "unallocated." Without deleting one of the four partitions or doing something more exotic (converting to GPT or converting at least one partition to a logical partition, say), you couldn't create a new partition in that space, given MBR's four-primary-partition limit.
 
> I do not see 2. as a possibility for me --- adding another physical disk to my laptop is not something for me. However, I do have several rather large external (USB) hard drives --- is this a possibility?

Yes, an external disk would work fine. An eSATA disk would be better than a USB disk, since the eSATA interface is faster than the USB interface (at least, as of USB 2.0; USB 3.0 devices are now available, but they're still rare).
 
> I was just on the phone with HP technical support and let me summarize  some things that came out of this conversation and is relevant to this  problem:
 
1. My particular model of the HP pavilion laptop was delivered with 4 partitions as exists now.
2. Partitiion D: (recovery) can be removed. However, I they recommended  that I make DVDs of this for recovery --- this I am doing now.
3. I plan to Delete partition D: after this has finished.

In other words, my suggestion #3. Some additional observations and suggestions:


[list]
[*]One of your screen shots shows space shrunk in such a way that the free space is adjacent to D:. This should make it easy to create one big extended partition to occupy all that free space. Linux can then reside on logical partitions in the extended partition. (Linux does *not* need to boot from a primary partition, unlike Windows.)
[*]When you install Ubuntu, I recommend you choose the custom partition option and create a root (/) partition of 10-20GB, a swap partition of 1-2x the RAM you've got on the computer, and another partition for /home occupying the rest of the space (but see the next point). Keeping /home on a separate partition is not done by the default Ubuntu installation options, but it can help in certain upgrade scenarios, since you can completely wipe the main installation without affecting your user data, which normally goes in /home.
[*]If you want to share data between Linux and Windows, I recommend creating another partition for this purpose and making it NTFS, which can be read by both Linux and Windows. That way you won't be forced to read/write the Windows boot partition from Linux, which is at least a little risky since Linux doesn't understand Windows' security features, making it too easy to accidentally delete critical Windows files from Linux. This partition can be (and in fact must be) another logical partition. Note that this partition can't be used as /home, since your user directory in /home must use filesystem features that NTFS doesn't provide. You'll have to decide, based on your expected needs, how much space to give to the shared partition and how much to give to /home. You can mount the shared partition anywhere you like, so long as it's not a directory that Linux normally uses. Something like /windows or /home/windows would work well for most people.
[/list]


Best of luck with your install. Many of the issues and problems you encounter in this sort of setup can be frustrating, but it is possible to get the two OSes to coexist quite well on one system.

---

### Post by virsto on 2010-09-10
> **srs5694 said:**
> Just to clear up some confusion: Neither of your screen shots shows five partitions on a single disk. One of them gives that impression because it shows four partitions and a large unallocated space. That unallocated space, though, is *not* a partition -- that's why it's called "unallocated." Without deleting one of the four partitions or doing something more exotic (converting to GPT or converting at least one partition to a logical partition, say), you couldn't create a new partition in that space, given MBR's four-primary-partition limit.
 
 
 
Yes, an external disk would work fine. An eSATA disk would be better than a USB disk, since the eSATA interface is faster than the USB interface (at least, as of USB 2.0; USB 3.0 devices are now available, but they're still rare).
 
 
 
In other words, my suggestion #3. Some additional observations and suggestions:
 

[LIST]
[*]One of your screen shots shows space shrunk in such a way that the free space is adjacent to D:. This should make it easy to create one big extended partition to occupy all that free space. Linux can then reside on logical partitions in the extended partition. (Linux does *not* need to boot from a primary partition, unlike Windows.)
[*]When you install Ubuntu, I recommend you choose the custom partition option and create a root (/) partition of 10-20GB, a swap partition of 1-2x the RAM you've got on the computer, and another partition for /home occupying the rest of the space (but see the next point). Keeping /home on a separate partition is not done by the default Ubuntu installation options, but it can help in certain upgrade scenarios, since you can completely wipe the main installation without affecting your user data, which normally goes in /home.
[*]If you want to share data between Linux and Windows, I recommend creating another partition for this purpose and making it NTFS, which can be read by both Linux and Windows. That way you won't be forced to read/write the Windows boot partition from Linux, which is at least a little risky since Linux doesn't understand Windows' security features, making it too easy to accidentally delete critical Windows files from Linux. This partition can be (and in fact must be) another logical partition. Note that this partition can't be used as /home, since your user directory in /home must use filesystem features that NTFS doesn't provide. You'll have to decide, based on your expected needs, how much space to give to the shared partition and how much to give to /home. You can mount the shared partition anywhere you like, so long as it's not a directory that Linux normally uses. Something like /windows or /home/windows would work well for most people.
[/LIST]I like this last suggestion of yours (to be able to share data), this would be very nice and useful. I have now completed the creation of the recovery disks and no longer need partition D: --- Please tell me how I should procede to implement your last suggestion. 
 
--V

---

### Post by virsto on 2010-09-10
> **oldfred said:**
> You do not need to install wubi to run the script. You often run it from a liveCD which you will need to have to do any install. If just starting out you do not need to run it now.
 
I prefer the elimination of a partition and installing at least / (root) and swap. If you are going to share with windows you may want to have a NTFS partition for shared data. You can read & write the windows C: partition but I only suggest reading from any system partitions with foreign systems except for repairs. Many windows users suggest a separate data partition so when you have to reinstall your system your data is separate. Of course you still need backups.
 
You can install to an external drive. It will be a little slower as the USB connection is not as fast as a SATA internal drive connection.
 
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
Full Disk install Lucid Graphical
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
 
Use windows tools to shrink the windows partition. You can then use the auto install into free space or if you want to create partitions in advance you can use gparted and then manual install to choose which partition is root.
 
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
 
 
Ok, 
I am now poised to prepare my disk for Ubuntu; but, it is not clear to me how I should procede. That is, I can remove D: now; but, not sure what to do then --- this partiitioning area is something I do not feel comfortable with; but, I do have disk image backups should things go wrong.
 
--V

---

### Post by perspectoff on 2010-09-10
> **virsto said:**
> But, as I stated in my previsou posting. **I have had the full 10.04 version running in dual-boot mode on the same hardware and same disk partitioning (4 partitions) that is now present and which now does not allow me to install the full 10.04.1 release!**
 
Sorry, but I do not know how to state this more clearly.
 
--V

Wubi is not true dual-boot. It runs Ubuntu from within Windows as a Windows application, basically.

What you wish to do is create true dual-booting.

---

### Post by virsto on 2010-09-10
> **perspectoff said:**
> Wubi is not true dual-boot. It runs Ubuntu from within Windows as a Windows application, basically.
 
What you wish to do is create true dual-booting.
 
Yes, I know and I would like very much to get through this mess (and this is very true) and install a dual-boot (Ubuntu 10.04.1 with Windows 7) on my PC which has plenty of free disk space. It seems to me that this should be easier.
 
--V

---

### Post by perspectoff on 2010-09-10
> **virsto said:**
> If one goes to [http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)
one will find...

I did follow this recipe; but, this just did not happen --- install to "largest available free space" was never an option for me!

--V

The previous poster is correct. That option only appears if you have 2 or more primary partitions still available, which you don't. HP used them all up for you.

You will manually have to convert the D: recovery partition (currently a primary partition) into an extended partition. You apparently have already created Recovery Disks and erased the data on this partition, which is good.

You will need to use a Partition Manager (either partition Manager on the Ubuntu LiveCD, or the GParted LiveCD) to erase the D: partition altogether and then create a new extended partition that incorporates the previous D: partition as well as all your remaining free space. 

Once you have done that, you can create multiple logical partitions (as many as you desire) from the new extended partition. Linux OSs require two partitions at the minimum: one for RAM swap (called Linux-swap) and one for the / OS partition.

These two partitions can be logical partitions.

In my next reply I will step-by-step outline how I do this (which I also did for my HP computer).

---

### Post by virsto on 2010-09-10
Just to bring everyone that is trying to help me up-to-date, I have attached another screen shot of the current partitioning for my system (this is where I am currently stuck)
 
Again, I have tried to prepare (chkdsk /r has been run which took almost 3 hours, unnecessary files have been removed, disk defragmented, and backups have been made to an external hard drive and to DVDs).  I can also remove partition D: if necessary.
 
I would like to complete this; but, I am not sure what should be done next!

---

### Post by virsto on 2010-09-10
> **perspectoff said:**
> The previous poster is correct. That option only appears if you have 2 or more primary partitions still available, which you don't. HP used them all up for you.
 
You will manually have to convert the D: recovery partition (currently a primary partition) into an extended partition. You apparently have already created Recovery Disks and erased the data on this partition, which is good.

 
No, I have not erased or removed the D: partition yet --- I am in a hold state waiting for advice on what to do next!
 
> 
You will need to use a Partition Manager (either partition Manager on the Ubuntu LiveCD, or the GParted LiveCD) to erase the D: partition altogether and then create a new extended partition that incorporates the previous D: partition as well as all your remaining free space. 

 
But I am using Windows 7 and thus their partitioning tools. Ubuntu is not installed on my system yet!
 
>  
Once you have done that, you can create multiple logical partitions (as many as you desire) from the new extended partition. Linux OSs require two partitions at the minimum: one for RAM swap (called Linux-swap) and one for the / OS partition.
 
These two partitions can be logical partitions.
 
In my next reply I will step-by-step outline how I do this (which I also did for my HP computer).
 
I am anxiously awaiting your instructions!
One other thing --- How do I create a logical partition in Windows 7 and is it really necessary?

---

### Post by perspectoff on 2010-09-10
If I had your computer, here's what I would do.

I would download a copy of the GParted LiveCD .iso from 

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) 

and burn it to a CD using either InfraRecorder or other methods indicated here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

(or possibly using a Windows 7 CD Image burning utility).

I would boot into the GParted LiveCD (obviously select the CD as your boot device when starting the computer).

Allow GParted to load, allowing it to use the "default" US keymap and "US English" language.

I am presuming that you have a newer graphics card/monitor, but if you don't you will have to "Forcevideo"
and use "vesa" as the video drive and "1024x768" as your resolution.

This should give you the graphical partition manager of GParted. It will display your partitions in a similar manner to the "Disk Management" graphic you posted.

(We needn't worry about the Kingston drive/partition as this is apparently a removable drive.)

Leave /dev/sda1 alone. This is a primary NTFS partition. I have no idea what a System partition is (since my HP computer doesn't have one), but better safe than sorry.

Your Windows 7 NTFS partition is 302 Gb and is on dev/sda2. This is a primary (bootable) partition with the boot flag set. Leave it alone.

HP has placed some tools (HP tools) on the dev/sda4 in a FAT32 primary partition. I personally got rid of all the HP Tools (which are mainly junk in my opinion) but perhaps you use some of those and want to leave this partition intact.

You said that you created Recovery Disks already from the data on the D: partition (dev/sda3) so you can delete this partition altogether.

From GParted, highlight the dev/sda3 partition and then "Partition -> Delete -> Apply"

Now you should see the free space grow by 18.57 Gb from 274.54 Gb to 293 Gb free space total. (This is the free space that will be then used for the extended partition).

It is usually recommended to move the extended partition to the end of the hard drive, although this is not absolutely necessary, and if you are nervous, you needn't do it. In your case, you would move the 108 Mb FAT32 partition (which has the HP Tools on it) to the left by highlighting the partition and "Partition -> Resize/Move".

Leave the size of the partition exactly the same (i.e. don't change the New Size), but change the "Free Space Preceding" to 0 so that all the free space is in the "Free Space Following" option. You could also do this by dragging and dropping the partition icon in the upper graphical box.
When you are done, you should see the 108 Mb partition moved all the way to the left next to the dev/sda1 and dev/sda2 partitions, leaving about 293 Gb free space at the end.

Now you must create a new extended partition in the remaining free space, which hopefully is all contiguous on the hard drive at this time.

In GParted, highlight the free space and then "Partition -> New" and create a new extended partition that is the size of all the remaining free space. The extended partition does not have a filesystem. It is only there to be divided further into an (almost) unlimited number of logical partitions.

You can stop here, if you choose, and let the Ubuntu installer do the rest with the extended partition, or you can create the logical partitions yourself (in for a penny, in for a pound, right?)

Highlight the new extended partition and then "Partition -> New" and then create a new logical partition of filesystem "linux-swap" that is 2 Gb in size. Then use the remainder of the extended partition to create a new logical partition of filesystem type ext4 (or ext3, if you prefer) for use by the Ubuntu OS.

This is the point where you can create even more partitions, if you desire. If you only want an Ubuntu OS that needs 60 Gb for example, go ahead and make that logical partition 60 Gb (filesystem ext4 or ext3). If you then want an additional data partition (in which to store EEG/EKG data that is not on the same partition as any OS), then create one now, of any size. You can create it with filesystem ext3, or NTFS (although I don't recommend that), or, as long as it's less than 30 Gb, FAT32. 

If you do this, then when you install Ubuntu, you would choose manual partitioning. You would indicate during manual partitioning which is the linux-swap partition (usually the Ubuntu installer recognizes it automatically) and the ext4 (or ext3) partition you created for use by the Ubuntu OS. You would not use the data partition (if you created one) during installation. This partition will be detected later by Ubuntu once installation is complete.

I generally have been better off re-booting Windows (after changing the partitions) prior to installing Ubuntu, just to make sure Windows has a chance to recognize and record the settings for the new partitions before Ubuntu's bootloader (Grub2) goes mucking around with the hard drive.

My complete, rather complex instructions, are at 

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

You may be able to do all the partition deleting/moving/creating with the Partition Manager of the Ubuntu LiveCD as well, but I haven't done it that way recently and forget the steps. 

You might also be able to do some of the steps with the Windows 7 partition manager (Computer Management -> Disk Management), but that utility uses some non-standard terminology when referring to partitions that makes using it rather dicey for this purpose. The only thing safe to do with that utility, IMO, is to shrink or expand the Windows NTFS partitions themselves. Further, you can't create linux-swap or ext3 or ext4 partitions with that utility. You could probably only get to the point of creating the large extended partition.

As I think about it, if you really want to keep the Recovery Partition (which is not at all necessary if you have already created the Recovery CDs from it), you could delete the HP Tools primary partition instead. Your choice.

Were you to delete both the Recovery Partition and the HP Tools partition, you would only have two primary partitions left on your hard drive (SYSTEM on dev/sda1 and NTFS Windows 7 on dev/sda2). All the rest would be free space. In this case, were you to start the Ubuntu LiveCD installer, the "automatically install to free space" option would then appear and would then do the rest for you automatically.

---

### Post by virsto on 2010-09-10
> **perspectoff said:**
> If I had your computer, here's what I would do.
 
I would download a copy of the GParted LiveCD .iso from 
 
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) 

 
Done!
 
>  
and burn it to a CD using either InfraRecorder or other methods indicated here:
 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
 
(or possibly using a Windows 7 CD Image burning utility).
 
 
I would boot into the GParted LiveCD (obviously select the CD as your boot device when starting the computer).
 
Allow GParted to load, allowing it to use the "default" US keymap and "US English" language.
 
I am presuming that you have a newer graphics card/monitor, but if you don't you will have to "Forcevideo"
and use "vesa" as the video drive and "1024x768" as your resolution.
 
This should give you the graphical partition manager of GParted. It will display your partitions in a similar manner to the "Disk Management" graphic you posted.
 
(We needn't worry about the Kingston drive/partition as this is apparently a removable drive.)
 
Leave /dev/sda1 alone. This is a primary NTFS partition. I have no idea what a System partition is (since my HP computer doesn't have one), but better safe than sorry.
 
Your Windows 7 NTFS partition is 302 Gb and is on dev/sda2. This is a primary (bootable) partition with the boot flag set. Leave it alone.
 
HP has placed some tools (HP tools) on the dev/sda4 in a FAT32 primary partition. I personally got rid of all the HP Tools (which are mainly junk in my opinion) but perhaps you use some of those and want to leave this partition intact.
 
You said that you created Recovery Disks already from the data on the D: partition (dev/sda3) so you can delete this partition altogether.
 
From GParted, highlight the dev/sda3 partition and then "Partition -> Delete -> Apply"
 
Now you should see the free space grow by 18.57 Gb from 274.54 Gb to 293 Gb free space total. (This is the free space that will be then used for the extended partition).
 
It is usually recommended to move the extended partition to the end of the hard drive, although this is not absolutely necessary, and if you are nervous, you needn't do it. In your case, you would move the 108 Mb FAT32 partition (which has the HP Tools on it) to the left by highlighting the partition and "Partition -> Resize/Move".
 
Leave the size of the partition exactly the same (i.e. don't change the New Size), but change the "Free Space Preceding" to 0 so that all the free space is in the "Free Space Following" option. You could also do this by dragging and dropping the partition icon in the upper graphical box.
When you are done, you should see the 108 Mb partition moved all the way to the left next to the dev/sda1 and dev/sda2 partitions, leaving about 320 Gb free space at the end.
 
Now you must create a new extended partition in the remaining free space, which hopefully is all contiguous on the hard drive at this time.
 
In GParted, highlight the free space and then "Partition -> New" and create a new extended partition that is the size of all the remaining free space. The extended partition does not have a filesystem. It is only there to be divided further into an (almost) unlimited number of logical partitions.
 
You can stop here, if you choose, and let the Ubuntu installer do the rest with the extended partition, or you can create the logical partitions yourself (in for a penny, in for a pound, right?)
 
Highlight the new extended partition and then "Partition -> New" and then create a new logical partition of filesystem "linux-swap" that is 2 Gb in size. Then use the remainder of the extended partition to create a new logical partition of filesystem type ext4 (or ext3, if you prefer) for use by the Ubuntu OS.
 
This is the point where you can create even more partitions, if you desire. If you only want an Ubuntu OS that needs 60 Gb for example, go ahead and make that logical partition 60 Gb (filesystem ext4 or ext3). If you then want an additional data partition (in which to store EEG/EKG data that is not on the same partition as any OS), then create one now, of any size. You can create it with filesystem ext3, or NTFS (although I don't recommend that), or, as long as its less than 30 Gb, FAT32. 
 
If you do this, then when you install Ubuntu, you would choose manual partitioning. You would indicate during manual partitions which is the linux-swap partition (usually the Ubuntu installer recognizes it automatically) and the ext4 (or ext3) partition you created for use by the Ubuntu OS. You would not use the data partition (if you created one) during installation. This partition will be detected later by Ubuntu once installation is complete.
 
I generally have been better off re-booting Windows (after changing the partitions) prior to installing Ubuntu, just to make sure Windows has a chance to recognize and record the settings for the new partitions before Ubuntu's bootloader (Grub2) goes mucking around with the hard drive.
 
My complete, rather complex instructions, are at 
 
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)
 
You may be able to do all the partition deleting/moving/creating with the Partition Manager of the Ubuntu LiveCD as well, but I haven't done it that way recently and forget the steps. You might also be able to do some of the steps with the Windows 7 partition manager, but probably not creating the linux-swap partition. You could probably only get to the point of creating the large extended partition.
 
As I think about it, if you really want to keep the Recovery Partition (which is not at all necessary if you have already created the Recovery CDs from it), you could delete the HP Tools primary partition instead. Your choice.
 
Thanks very, very much **perspectoff** --- this is a big help and I will attempt to follow your instructions as close as possible. After reading through this information and checking the links I do not have any obvious questions (at least not yet!).
 
I appreciate your help very much, and will get back to you on the final results (or perhaps earlier, if I have some questions) --- this could take a few days. :)

---

### Post by perspectoff on 2010-09-10
In the past, HP took up the entire hard drive with Windows (Vista or Windows 7), making it even more difficult to install Linux on it, since shrinking the Windows Vista/7 partition by more than about 20 Gb is not really that easy (due some quirks with the Windows OS).

I wrote to them asking that they leave both free space and several partitions on the hard drive to enable us Linux users to install it.

They did that, and I have to give them credit for it. They almost got it right, too. They just created 4 primary partitions instead of 3 primary partitions and one extended partition. You see, when there is at least one extended partition, it can be expanded to include any remaining free space on the hard drive and additional logical partitions then created. This can't be done with primary partitions.

Looks like it's time for another letter to them.

By the way, the movie Avatar was created using Ubuntu on about 400 HP computers. I actually love my HP laptop with Kubuntu (and Ubuntu and Windows 7) on it, so I don't want to put down HP. 

They don't get everything exactly right, but they are trying pretty hard (disclaimer: I have no relationship with HP).

---

### Post by srs5694 on 2010-09-10
> **perspectoff said:**
> If I had your computer, here's what I would do.

For the most part, this is good advice. I have some comments and alternate suggestions, though....

> I would boot into the GParted LiveCD (obviously select the CD as your boot device when starting the computer).

Before doing this, I'd use the Windows partition tool to shrink the Windows C: partition. The to-be-deleted D: partition is only 18.57GB, which is large enough for an Ubuntu installation, but not much else. Of course, virsto, you'll have to decide for yourself just how much space to give to Linux (and to the Linux/Windows shared data partition you said in an earlier message you intended to create).

> Leave /dev/sda1 alone. This is a primary NTFS partition. I have no idea what a System partition is (since my HP computer doesn't have one), but better safe than sorry.

One caution: The partition label order might not match the order of the partitions shown in the screen shots virsto provided. I recommend identifying them by size, since each one has a unique size. The Linux partitioner will *not* show you the Windows drive letters ([noparse]C:, D:,[/noparse] etc.).

> Your Windows 7 NTFS partition is 302 Gb and is on dev/sda2. This is a primary (bootable) partition with the boot flag set. Leave it alone.

If you want more than 18.57GB for Linux (including its user data), the 302GB Windows partition will have to be resized. As noted above, I recommend doing this in Windows, since that's likely to be slightly safer than doing it in GParted; however, it can be done in GParted, if necessary. The trouble is that if GParted decides to move the start of the partition, Windows might then refuse to boot. Some people have had luck with this, others have not.

> It is usually recommended to move the extended partition to the end of the hard drive, although this is not absolutely necessary, and if you are nervous, you needn't do it. In your case, you would move the 108 Mb FAT32 partition (which has the HP Tools on it) to the left by highlighting the partition and "Partition -> Resize/Move".

Personally, I wouldn't bother with this. The only advantage to doing this is that the logical partitions, numbered from 5 and up, will come after all of the primary partitions, numbered 1-4, thus making it possible to keep the device numbers and the partition locations on the disk in sync. If you don't move the 108MB FAT partition, you'll have something where /dev/sda5 and up by device number come before /dev/sda4 (or whatever it is in Linux) on the disk. This can be confusing, but it's perfectly legal. IMHO, it's not confusing enough to risk the data or take the time to do it (although 108MB is pretty small, so it shouldn't really take long to move that partition).

> Highlight the new extended partition and then "Partition -> New" and then create a new logical partition of filesystem "linux-swap" that is 2 Gb in size.

Swap space should be 1-2 time the amount of RAM on the system. If it's less than the RAM size, then suspend-to-disk operations won't work, which could be important on a laptop. Too much swap space does no real harm, except that it's using disk space you might prefer to devote to filesystem data. If you want to have just enough swap space, I'd go a bit high (say, 2.2GB on a system with 2GB of RAM), just to be sure you don't run into rounding or GB-vs-GiB issues.

> This is the point where you can create even more partitions, if you desire. If you only want an Ubuntu OS that needs 60 Gb for example, go ahead and make that logical partition 60 Gb (filesystem ext4 or ext3). If you then want an additional data partition (in which to store EEG/EKG data that is not on the same partition as any OS), then create one now, of any size. You can create it with filesystem ext3, or NTFS (although I don't recommend that), or, as long as it's less than 30 Gb, FAT32.

FWIW, I recommend putting a multi-OS shared-data partition between the main partitions used by the two OSes -- so in this case it would be the first logical partition in the extended partition. This will minimize disk head seek time when accessing that partition from either OS. I'd also put swap space in-between the Linux root (/) and /home partitions, if they're separate, again to minimize disk seek times. (Actually, this reasoning might be a point in favor of moving your E: drive, but it's probably accessed so seldom that the slightly slower access times with Linux in-between it and the main Windows partition won't be important.)

> You would not use the data partition (if you created one) during installation. This partition will be detected later by Ubuntu once installation is complete.

You can call out the shared-data partition at install time. If you do, it will get whatever mount point you specify; for instance, you could tell the installer to access it at /home/shared or /shareddata. If you don't call it out during installation, it will get a mount point in the /media directory, probably named after whatever name you give the partition.

---

### Post by perspectoff on 2010-09-11
The guy already has 274 Gb of unallocated free space. He doesn't need to shrink the primary NTFS windows 7 partition.

The reason for deleting the Restore Partition is not to reclaim space (he has plenty) but to convert it from a primary partition to an extended partition. 

Moving an extended partition so that it is the last partition isn't necessary, I agree, but, in general, is good practice. The reason is that it ends up being easier to manipulate many logical partitions and shrink and grow the partitions without bumping up against primary partitions on both sides. A minor point, I guess... and I do see your point, though.

The Disk Management utility in Windows 7 is strange. If I understand it correctly, it now refers to primary partitions as "Simple Disks" which can be "active" (i.e. bootable with the boot flag set). Extended partitions are known as "Dynamic Disks," as far as I can tell. 

I don't know if Windows has real LVM-like capabilities, yet. LVM is what I would consider a true Dynamic storage system.

BTW, this user apparently stores is EEG and EKG storage. A topic close to my interests are PACS image (and DICOM image) storage. It takes a long time to fill up a 600 Gb hard drive with data, but it does happen eventually. That's when LVM becomes nice to have around. 

Expandable storage schemes work better when the expandable storage blocks are at the end of the hard drive, IMO. That's probably why I prefer to have any type of dynamic storage at the end of the hard drive.

> One caution: The partition label order might not match the order of the partitions shown in the screen shots virsto provided. I recommend identifying them by size, since each one has a unique size. The Linux partitioner will not show you the Windows drive letters (C:, D:, etc.).

Very good advice. When partitions are deleted, rearranged, or moved, their numbering also changes (dev/sda4 can become /dev/sda3). Yes, I always keep track of partitions by their size, as well. BTW, I never refer to partitions by the Windows drive letters, which don't correlate to partitions in a one-to one fashion anyway. Windows drive letters can refer to a lot of things, including virtual drives, network shares, etc. etc. Windows drive letters don't strictly have that much to do with partitions.

> FWIW, I recommend putting a multi-OS shared-data partition between the main partitions used by the two OSes -- so in this case it would be the first logical partition in the extended partition. This will minimize disk head seek time when accessing that partition from either OS. I'd also put swap space in-between the Linux root (/) and /home partitions, if they're separate, again to minimize disk seek times. (Actually, this reasoning might be a point in favor of moving your E: drive, but it's probably accessed so seldom that the slightly slower access times with Linux in-between it and the main Windows partition won't be important.)


High density drives have such fast seek times that I don't feel nanosecond savings are very important (or even noticeable) to most users. On the other hand, I re-arrange partitions and change their size so frequently that ensuring future ease of doing so is very important to me.

So on this point I don't agree with you.

> You can call out the shared-data partition at install time. If you do, it will get whatever mount point you specify; for instance, you could tell the installer to access it at /home/shared or /shareddata. If you don't call it out during installation, it will get a mount point in the /media directory, probably named after whatever name you give the partition.

Agreed. It is nice to name the mount point of a data partition (e.g. /sharedata or /ekgdata ) so that when you access the partition from different operating systems it is clear what actually resides in that partition.

I also agree with the double your RAM as the size of the linux-swap partition, but I read a study that suggests that anything over 2 Gb (or 2.2 Gb) isn't really used for swapping very much. Hence I routinely only recommend 2 Gb. Even for those with less than 2 Gb RAM initially, everyone eventually buys more. For those with > 8 Gb RAM, I doubt swap is really that important, anyway. Besides, for kernel 2.6 and later, swap files instead of swap partitions are more efficient for heavy load servers anyway. So I don't really ever see a reason for anything greater than a 2 Gb linux-swap partition.

---

### Post by srs5694 on 2010-09-11
> **perspectoff said:**
> The guy already has 274 Gb of unallocated free space. He doesn't need to shrink the primary NTFS windows 7 partition.

Not according to his latest screen shot, shown in [this post.](http://ubuntuforums.org/showpost.php?p=9829967&postcount=25) An earlier screen shot showed free space, but he wrote that he'd resized it back up after his initial failed attempt at installation.

> The Disk Management utility in Windows 7 is strange. If I understand it correctly, it now refers to primary partitions as "Simple Disks" which can be "active" (i.e. bootable with the boot flag set). Extended partitions are known as "Dynamic Disks," as far as I can tell.

A Windows "dynamic disk" is a volume in a Logical Disk Manager (LDM) partition, which is the Windows equivalent of a Logical Volume Manager (LVM) partition in Linux. I just checked, and at least as of Windows Vista, Windows reports NTFS and FAT logical partitions as "logical drives;" however, it misreported various Linux logical partitions as being primary. Both primary and logical partitions are reported as being "simple disks."

> I don't know if Windows has real LVM-like capabilities, yet. LVM is what I would consider a true Dynamic storage system.

I've never used it, but LDM seems to fit the bill. Check [its Wikipedia page](http://en.wikipedia.org/wiki/Logical_Disk_Manager) for starters.

> High density drives have such fast seek times that I don't feel nanosecond savings are very important (or even noticeable) to most users.

Nanosecond? I think not. I just checked the specs for a few drives at Newegg. They all had seek times in the 2.5-4 millisecond range. Of course, a single seek like that won't make much difference; but if you're doing something that requires seeking back and forth a lot, a bunch of seeks in the low millisecond range can add up to noticeable time pretty quickly. If you cut the seek time from, say, 3 milliseconds to 1 millisecond by better partition placement, that could be a worthwhile savings. At least that's the theory. I admit that I haven't done any tests of how much of an effect this is likely to have on real-world performance.

> I read a study that suggests that anything over 2 Gb (or 2.2 Gb) isn't really used for swapping very much. Hence I routinely only recommend 2 Gb. 

The system under consideration is a laptop, though, so it's entirely plausible that suspend-to-disk will be used; but that feature is only usable if the swap space is sufficient to hold the image of the system's RAM. Of course, not everybody uses suspend-to-disk, but unless disk space is very cramped, it's better to create more swap space than you'll need than not enough.

---

### Post by oldfred on 2010-09-11
I think we have seen issues with dynamic disks.

[http://support.microsoft.com/kb/314343](http://support.microsoft.com/kb/314343)
**WARNING**: After you convert a basic disk to a dynamic disk, local access           to the dynamic disk is limited to Windows 2000 and Windows XP Professional.           Additionally, after you convert a basic disk to a dynamic disk, the dynamic           volumes cannot be changed back to partitions. You must first delete all dynamic           volumes on the disk and then convert the dynamic disk back to a basic disk. If           you want to keep your data, you must first back up the data or move it to           another volume. [[IMG]http://support.microsoft.com/library/images/support/kbgraphics/public/en-us/uparrow.gif[/IMG]]("http://support.microsoft.com/kb/314343#top")

I do not know if this says it is included or excluded but but everyone I have tried to help with dynamic disks have had issues:
[http://en.wikipedia.org/wiki/Logical_Disk_Manager](http://en.wikipedia.org/wiki/Logical_Disk_Manager)
 The main disadvantage of dynamic disks in Microsoft Windows is that  they can only be recognized under certain operating systems, such as [Windows 2000]("http://en.wikipedia.org/wiki/Windows_2000") or later (excluding versions such as [Windows XP]("http://en.wikipedia.org/wiki/Windows_XP") Home Edition, and [Windows Vista]("http://en.wikipedia.org/wiki/Windows_Vista") Home Basic and Premium[[2]]("http://en.wikipedia.org/wiki/Logical_Disk_Manager#cite_note-1")), or the [Linux]("http://en.wikipedia.org/wiki/Linux") kernel starting with version 2.4.8.

---

### Post by virsto on 2010-09-11
Finally, I have succeeded to create a dual-boot (Win 7 with Ubuntu 10.04.1) on my HP Pavilion laptop. I will try to summarize what I believe is important in my solution but some of which is specific to my laptop.

1. First clean up your system (in Win 7):
    * Remove all unnecessary files 
    * Defragment the disk (C: in my case)
    * Do a chkdsk /r or equivalent (this took about 2 and 1/2 hours on my laptop)    
2. Make recovery DVDs (4 DVDs on my system)
3. Remove D: (Recovery) [Note, the recovery DVDs could be used to recover everything in this partition]

I then used the partition tool in Win 7 to finally obtain a 187 GB partition for Win 7 and another partition for Ubuntu that was greater than 300 GB ... Unfortunately, I have been unable to reproduce the exact steps that I performed; but, it did take several trial and error partitioning schemes. Just be patient and careful.

4. Boot-up into Win7 twice --- just to make sure that Win 7 "sees" the new partitioning of your disk.

5. I then Installed Ubuntu 10.04.1 from the CD that I burned from the download of **ubuntu-10.04.1-desktop-amd64.iso** (boot-up from this CD).
    * I installed into the largest free partition (when I was asked to setup the partitioning by Ubuntu)

And then after a few minutes Ubuntu was up and running.

Note, this still does not explain how I was able to install (a few months earlier) Ubuntu 10.04 when I thought there were 4 partitions; but, there must have been only 3. My best guess is that in the process of many recent failures and recoveries that a System partition was created and thus this fourth partition prevented the normal installation of Ubuntu 10.04.1 [Note, this comes from a suggestion by **srs564**]

Further, I  would like to thank all of those who added their postings to my problem --- I learned from them.

--Thanks
Have a good day!

---

### Post by perspectoff on 2010-09-12
> **oldfred said:**
> I think we have seen issues with dynamic disks.

[http://support.microsoft.com/kb/314343](http://support.microsoft.com/kb/314343)
**WARNING**: After you convert a basic disk to a dynamic disk, local access           to the dynamic disk is limited to Windows 2000 and Windows XP Professional.           Additionally, after you convert a basic disk to a dynamic disk, the dynamic           volumes cannot be changed back to partitions. You must first delete all dynamic           volumes on the disk and then convert the dynamic disk back to a basic disk. If           you want to keep your data, you must first back up the data or move it to           another volume. [[IMG]http://support.microsoft.com/library/images/support/kbgraphics/public/en-us/uparrow.gif[/IMG]]("http://support.microsoft.com/kb/314343#top")

I do not know if this says it is included or excluded but but everyone I have tried to help with dynamic disks have had issues:
[http://en.wikipedia.org/wiki/Logical_Disk_Manager](http://en.wikipedia.org/wiki/Logical_Disk_Manager)
 The main disadvantage of dynamic disks in Microsoft Windows is that  they can only be recognized under certain operating systems, such as [Windows 2000]("http://en.wikipedia.org/wiki/Windows_2000") or later (excluding versions such as [Windows XP]("http://en.wikipedia.org/wiki/Windows_XP") Home Edition, and [Windows Vista]("http://en.wikipedia.org/wiki/Windows_Vista") Home Basic and Premium[[2]]("http://en.wikipedia.org/wiki/Logical_Disk_Manager#cite_note-1")), or the [Linux]("http://en.wikipedia.org/wiki/Linux") kernel starting with version 2.4.8.

This thread has morphed in a very interesting direction (now that the original user actually was able to fix his problem.)

I am now interested to find out how well Linux accesses the Windows LDM disks, having never tried that (or even used the Windows LDM scheme, since I am nowadays primarily a Linux user).

> Nanosecond? I think not. I just checked the specs for a few drives at Newegg. They all had seek times in the 2.5-4 millisecond range. Of course, a single seek like that won't make much difference; but if you're doing something that requires seeking back and forth a lot, a bunch of seeks in the low millisecond range can add up to noticeable time pretty quickly. If you cut the seek time from, say, 3 milliseconds to 1 millisecond by better partition placement, that could be a worthwhile savings. At least that's the theory. I admit that I haven't done any tests of how much of an effect this is likely to have on real-world performance.

Ok. I concede the point. I read an interesting review this morning where a user placed his entire operating system (and swap) on a solid state drive, leaving a larger, slower (regular) hard drive only for data. He noted that because of the fast seek times of the solid state drive, everything he did was instantaneous, and his system (he was using the relatively slow Windows 7 OS) was orders of magnitude faster than before. He indicated that using the solid state drive in this fashion far outweighed changes in RAM, changes in the CPU, and just about every other change on his system.

In light of this article, I doubly concede your point about disk access time.

---

### Post by oldfred on 2010-09-12
Herman posted some interesting info on disk read times. USB, Hard Drive & SSD.

[http://ubuntuforums.org/showthread.php?t=1570986](http://ubuntuforums.org/showthread.php?t=1570986)

---

### Post by srs5694 on 2010-09-13
> **perspectoff said:**
> I am now interested to find out how well Linux accesses the Windows LDM disks, having never tried that (or even used the Windows LDM scheme, since I am nowadays primarily a Linux user).

I've never used the Windows LDM setup, myself. I have seen occasional posts here from people who have such setups, and the logical volumes they contain show up in /dev/mapper, just like Linux LVM volumes. I don't know offhand if there are any Linux tools for manipulating LDM volumes.

> Ok. I concede the point. I read an interesting review this morning where a user placed his entire operating system (and swap) on a solid state drive, leaving a larger, slower (regular) hard drive only for data. He noted that because of the fast seek times of the solid state drive, everything he did was instantaneous, and his system (he was using the relatively slow Windows 7 OS) was orders of magnitude faster than before. He indicated that using the solid state drive in this fashion far outweighed changes in RAM, changes in the CPU, and just about every other change on his system.

In light of this article, I doubly concede your point about disk access time.

Of course, an SSD is likely to have different throughput speeds, not just quicker seek times, so that'll play a role -- maybe a bigger role than the near-0 seek times of SSDs.

---

### Post by tsam19 on 2010-09-13
Hello All 

I could do with some advice too, if anyone can relate to the below info.

I'm new to the world of Unbuntu & i thought I'd give the operating  system a go.

I downloaded the latest version from the website - 10.0.4.1

I wanted a multiple operating platform on my macbook pro so I followed  these instructions:

[http://hydtechblog.com/2009/01/26/dual-triple-quad-boot-a-macbook-with-mac-os-x-ubuntu-linux-windows-xp-and-windows-vista/](http://hydtechblog.com/2009/01/26/dual-triple-quad-boot-a-macbook-with-mac-os-x-ubuntu-linux-windows-xp-and-windows-vista/)

I installed 3 operating systems ok.

Win 7
Win Xp
Mac Osx

But I followed the instructions for installing unbuntu & when the  install had finished & I ejected the disc, the Mac went to reboot  & there was a black page with 'Error messages I/O' all down the  page.

Turned off & on & mac went to the rEFIt boot menu:
Mac icon, Windows icon,Penguin icon was visible, but 4th Windows icon  had now disappeared??

I tried to boot up the Penguin icon - nothing happened except operating  system error?

So I thought about working backwards & removed the Linux partition  in Mac disk utility.

Booted up Windows XP - checked Admin tools,disc management - all 5  partitions are there & healthy.

Booted the Mac up & went to disk utility - deleted/reformatted the  Linux Swap space partition to see if the Windows 7 would boot up - but  it wouldn't.

It still doesn't appear on the rEFIt boot menu, but the partition is  still there & healthy according to Win XP disc management.

Anyone got any tips on how to sort this out?

What is the correct procedure for installing Ubuntu, does the partition  have to be formatted FAT or NTFS or HFS+

I don't want to start all over again, it took hours to get 3 installed  correctly.

The thread on 'quad' booting was pretty explanatory, although the  blogger was using an older version of Ubuntu, but i didn't think it  would be a problem.

I look forward to any help.

Thanks

---

### Post by oldfred on 2010-09-13
Do not know anything about Mac's and what complications that adds but windows will only have one bootable partition unless you created it separately. For windows to boot windows it moves the boot files from the second install into the first.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by srs5694 on 2010-09-13
> **tsam19 said:**
> I downloaded the latest version from the website - 10.0.4.1

I wanted a multiple operating platform on my macbook pro so I followed  these instructions:

[http://hydtechblog.com/2009/01/26/dual-triple-quad-boot-a-macbook-with-mac-os-x-ubuntu-linux-windows-xp-and-windows-vista/](http://hydtechblog.com/2009/01/26/dual-triple-quad-boot-a-macbook-with-mac-os-x-ubuntu-linux-windows-xp-and-windows-vista/)

I installed 3 operating systems ok.

Win 7
Win Xp
Mac Osx

But I followed the instructions for installing unbuntu & when the  install had finished & I ejected the disc, the Mac went to reboot  & there was a black page with 'Error messages I/O' all down the  page.

There's a good chance that there's a subtle issue with the [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) configuration on the hard disk. Hybrid MBRs are ugly, dangerous, and poorly understood -- a very bad combination. Unfortunately, they're a virtual necessity for getting OS X and Windows to coexist on Macs.

I recommend you boot your Ubuntu install disc, launch a text-mode terminal (shell prompt), type "sudo apt-get install gdisk", and then type the following two commands and post the output here, preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility:

```

sudo fdisk -lu /dev/sda
sudo gdisk -l /dev/sda

```

This will tell us how both your MBR partitions and your GPT partitions are configured. It's conceivable that modifying the hybrid MBR will enable the system to boot; however, it's also possible that you'll need to muck with the boot loader configuration. I'm afraid I'm not very familiar with rEFIt or how Intel-based Macs boot, so I can't help you much on that score.

---

### Post by srs5694 on 2010-09-13
> **oldfred said:**
> To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words

tsam19 is using a Mac, so the system almost certainly uses a GUID Partition Table (GPT) setup with a hybrid MBR. Such setups cannot safely use logical partitions, and it's imperative that the hybrid MBR *not* be manipulated with fdisk or other typical MBR-only tools; only GPT-aware tools (such as GNU Parted, GParted, or gdisk) should be used, and then a new hybrid MBR created to synchronize the two. (Note that in my previous post I asked for fdisk output, but that only uses fdisk to *examine* the MBR, not to modify it.)

I realize, oldfred, that you didn't suggest modifying the disk with fdisk or creating logical partitions. I just want to be sure that the use of GPT on this disk is well understood by everybody so that nobody suggests doing something that would be phenomenally dangerous in a future post.

---

### Post by perspectoff on 2010-09-14
For several years now, I have advocated having a boot partition with a master bootloader used only to chainload specific OS bootloaders.

In years of experience, hybrid MBR bootloaders (including Grub2 for Ubuntu Linux, the Windows bootloader, and the Mac bootloader) all generate nothing except endless misery.

I use Grub Legacy as my MBR bootloader. I place this in a 100 Mb partition of its own, and the MBR points to it for all eternity.

When Grub Legacy is loaded, all it does is present a menu of all the OSs on the hard drive. When the menu item for a particular OS is selected, Grub Legacy then merely chainloads the specific bootloader for the OS that is chosen (and which resides within the partition in which the OS is installed). The specific bootloader remains in the partition of that particular OS, and the default options are always to load that OS, so I never have to fiddle with any specific OS bootloaders at all.

So, the Mac OSX bootloader remains in the Mac OSX partition (which, I believe, indeed can be a logical partition) and only needs to work with that partition. The Windows 7 bootloader remains in the Windows partition and only needs to work with Windows. The Grub2 bootloader remains in the Ubuntu partition and only needs to work with that Ubuntu installation. 

All that Grub Legacy bootloader does is chainload the other bootloaders (depending on which OS is chosen from the Grub Legacy menu).

That is not the solution advocated by the referenced blog, which attempts to cobble together hybrid bootloader schemes. No wonder your system is fried.

My advice is at 

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

or

[http://kubuntuguide.org/Multiple_OS_Installation](http://kubuntuguide.org/Multiple_OS_Installation)

---

### Post by srs5694 on 2010-09-14
It's becoming clear that tsam19 really should have created a new thread, probably in the Apple section, rather than post his new problem to an existing thread. I believe that perspectoff is replying to the new issue tsam19 raises, but I'm not positive of that. I'll reply based on my assumption that perspectoff is replying to tsam19's problem. If I'm wrong, my apologies for further muddying the waters....

Macintoshes do not normally use MBR; Intel-based Macs use the [GUID Partition Table (GPT)](http://en.wikipedia.org/wiki/GUID_Partition_Table) partitioning system, at least for their boot disks. (Older PowerPC and Motorola-based Macs use yet another partitioning system.) Macs also don't use the same firmware as most x86 computers (BIOS); instead the use the [Extensible Firmware Interface (EFI).](http://en.wikipedia.org/wiki/Extensible_Firmware_Interface) These two facts completely change the way the computers boot and render most of what perspectoff has written irrelevant.

A [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) in the OS X context, is a weird merging of MBR and GPT; up to three GPT partitions are duplicated in the protective MBR that's a standard part of GPT. Hybrid MBRs are ugly, dangerous, and sadly the only way (AFAIK) to get OS X and Windows to coexist in a true dual-boot configuration on modern Macs. I'm not sure what perspectoff means by "hybrid MBR bootloaders," but from the context, I don't think it has anything to do with a hybrid MBR as the term is generally used in reference to modern Macs.

Because modern Macs use GPT, there's generally no such thing as a logical partition on Mac disks. (Macs can read MBR disks, so there *could* be a Mac with an MBR disk and logical partitions; but Macs don't generally use MBR disks as boot disks.) I've seen claims of Hackintoshes that can boot OS X from logical partitions, but real Macs certainly don't come configured that way, and I have no idea if you could get a real Mac to boot from an MBR disk, much less a logical partition on an MBR disk.

---

