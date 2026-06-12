---
title: "Upgrade and Grub mystery and misery"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by n0c0d3 on 2012-05-01
Hi all,

I tried to upgrade from Xubuntu 11.10 to 12.04. My past upgrade experiences led me to burn it to CD and upgrade from there, butthis time it was not successful. Far from that. I'll explain what I did, what happened and where I'm now:

I have a multiboot system (grub 2) with Win7 and Xubuntu on it. During running the upgrade CD I got an error and the upgrade was aborted. There was no information what the error was I was led to the Live-CD, from where I decided to give it another try. This time I got an error message that there is not enough space on the destination drive. As there was supposed to be 4.4 Gig required and I have between 8 and 9 Gig left (it's not much but it should have been enough), I don't know how serious I can take this error. I tried to boot in Xubuntu again, but this left me with a black screen. The upgrade already made too many changes for it to be able to boot I suppose.

But just to make sure the size was not the problem I decided to increase the size of this partition. The plan was to decrease the Win7 partition in size and give that to the Linux (ext4) partition with Gparted (v. 6.2-2), which I have on CD. But Gparted indicated there was something wrong with the Win7 partition, which is on sda3. The most important part of the sda3 warning message:

> Filesystem check failed. Totally 1 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was and will be made to NFTS by this software until it gets repaired.

Unable to read the contents of this filesystem! Because of this some operations will be unavailable.

The following is a list of software packages required for nfts file system support: nftsprogs.This is how my drive configuration looks like according to Gparted:

/dev/sda1      ntfs
/dev/sda2      ntfs
/dev/sda3      ntfs
/dev/sda4      extended
/dev/sda5      linux swap

Then I tried to boot in Windows which gave no problem at all, so I ran 'fdisk /f' (the scan disk option in the disk-properties with both options ticked) and rebooted twice. The first reboot I consider to be immediately after the disk was scanned (no errors were found) and a 2nd time. Just to make sure I wanted to give it a third boot, but this time I was too quick and inaccurate and made a mistake. In the grub-menu I started the Win7 recovery entry. As soon as the recovery screen finished loading I pressed the cancel-button and the computer rebooted. Now the disaster came to completion: I only get the grub rescue prompt:

error: no such partition
grub rescue>

when I do a 'ls' I get:
(hd0) (hd0,msdos5) (hd0,msdos3  (hd0,msdos2)  (hd0,msdos1)

I'm totally in the dark from here. I made a backup of my /home directory from the Linux partition to an external HD, so I won't loose very much when I'd have to re-install that in its entirety, but losing my Win7 install would be not funny at all.

I'd be very happy if the community could help me get back on track with getting back my grub-menu, Windows partition and hopefully also with the Xubuntu upgrade.

I'm currently working on an ancient computer. I've tried to burn a CD with Boot-repair which I read about on this forum, but to no avail. The CD's are not even recognized to be writable so I think the DVD-player has more or less past away. So if more information is necessary, please tell me how I can get it (what utils, screens, commands, menu's, etc). 


Thanks,
Bart

---

### Post by darkod on 2012-05-01
Boot with the 12.04 cd in live mode, and post the result of:
sudo fdisk -l (small L)

You mentioned three ntfs partitions and a linux swap partition, but not a linux partition. You should have at least one linux partition (the root) there. It might not be read correctly right now because of the failed upgrade. Lets see what fdisk says about the partitions.

---

### Post by n0c0d3 on 2012-05-01
Hi Darko,

Total horror, I forgot to note down on which 12.04 was burned, and when trying to find a CD to put Boot-repair on I made a mess of my pile of CD's. I found one with 10.04 on it so I'll use that for now. I'll try to find 12.04 in the mean time (hopefully I didn't mess that one up).

fdisk -l gave me:
> 
ubuntu@ubuntu:~/Desktop$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9bb2dcda

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12586896   27  Unknown
/dev/sda2   *        1568        1580      104422+   7  HPFS/NTFS
/dev/sda3            1581       34083   261079625    7  HPFS/NTFS
/dev/sda4           34084       38914    38797313    5  Extended
/dev/sda5           38710       38914     1637376   82  Linux swap / Solaris
ubuntu@ubuntu:~/Desktop$ 
I think the Extended partition is (or was?) the ext4 partition which has/had Xubuntu on it.


Thanks for your help,

Bart

---

### Post by darkod on 2012-05-01
The fdisk on the 10.04 cd works with cylinders. On a recent version it works with sectors. But that doesn't matter much, it helps for a first look.

You see, in cylinders your disk has 38913 total.

The extended partition has start/end of 38084/38914.
The swap partition, sda5, has start/end of 38710/38914.

So, your root partition is missing somewhere between cylinder 38084/38710.

Also, this might have happened because somehow one partition ended up outside the disk. If the total number of cylinders is 38913 how can the extended partition end at 38914? I think that's an error in the partition table.

To bring back your root partition you can use testdisk. You can use it from 10.04 live mode too. Just download it, unpack it where you want, and run it. Instructions how to recover partition are here:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

If you need help, run the deep search of testdisk and post a screenshot of the partitions found. It can usually detect older partitions that you don't want to recover, so you have to be careful which one you select for recovery.

And don't forget that live mode doesn't keep any downloads etc so if you reboot it you will have to download testdisk again to run it.

---

### Post by n0c0d3 on 2012-05-01
I can't find the 12.04 CD anymore. I'm afraid I lost that one.  But that's not the biggest problem right now. I can download and burn that even from a LiveCd as well I suppose. I use a USB thumb-drive as wireless plug 'n play network, so I can save  whatever I need there. I found a Xubuntu 11.10 CD and I'm working from that one right now.

I'm currently doing a deep scan with TestDisk because it seemingly couldn't find any files on my Windows partition. I didn't make a screenshot from the Quick Search results, they looked pretty much like what I posted above after he fdisk -l. I'll report back about the deep scan later, it seems to take quite some time and I should have been asleep already. If the scan doesn't finish soon (it doesn't look  like it will), I'll report back tomorrow.

But I have a question. What about Grub? Is that gong to point to my partitions again if they're found and (hopefully) restored?


Thanks for your help so far Darko, I really appreciate it.

Bart

---

### Post by n0c0d3 on 2012-05-02
I was wrong when I said I can burn CD's from the LiveCD. It's a laptop and only has one DVD-player and the 11.10 CD is in there already. I can access my Windows drive from the LiveCD thoguh, so it's contents is not lost (...yet, dependent on what's going to happen next).

The screenshot of the result of the quick search:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=217116&d=1335978406[/IMG]


There were some error messages right before it ended:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=217117&d=1335978406[/IMG]


When I select the Linux partition it says this:
> 
ext4 blocksize=4096 Large file Sparse superblock, 15 GB / 13 GiB
So the ext4 formatting seems not to be lost.
When I do file listings (press 'p') I get a listing on the [HD] partition (my Windows partition) I get a full file and directory listing. On the linuxpartition howver I get "No file found, filesystem may be damaged". The FAT12 partition also contain stuff, they mustbe part of the Windows recovery or something like that. I'm not sure. P'ing Linux Swap doesn't do a thing.


I get this after the Deeper Search:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=217118&d=1335978406[/IMG]


And I get some warning messages here as well:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=217119&d=1335978406[/IMG]

The OS-partitions (NTFS and Linux) are marked with a 'D', so they seem to be deleted.

The last line is again with the [HD] (the name of my Windows partition) selected. When I select the consecutive Linux partition it says this:
> 
ext4 blocksize=4096 Large file Sparse superblock, 15 GB / 13 GiB

ext4 blocksize=4096 Large file Sparse superblock Recover, 38 GB / 35 GiB

ext4 blocksize=4096 Large file Sparse superblock Recover, 20 GB / 19 GiB
When I press 'p' on the first and last (15 and 20 Gig) Linux partition I get no directory listing ("No file found, filesystem may be damaged"), but when do that on the 38 Gig entry I (as far as I can see) get my previous Xubuntu install. So I suppose this is the one that needs to be recovered, but I'm unsure how I should proceed. Should I mark the HD and 38 Gig Linux partitions as primary and logic?

The 38 Gig Linux partition with the files don't seem to be either primary or logic according to this explanation: [http://www.cgsecurity.org/wiki/Partition_recognition_primary_and_logical](http://www.cgsecurity.org/wiki/Partition_recognition_primary_and_logical) . I can change them to Primary or Logic with the left/right arrow keys, but I'm really unsure what to do.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=217120&d=1335978406[/IMG]

After the deep scan I can choose one particular entry and press 'enter' to continue.  the [write] option, which will I presume write the partition structure to disk (the partitioning table). But the partitions marked as deleted are not there. I think they will be there when I change their status or type. But as I don't know what partitions to change to what I hope you (or someone else) can guide me through the rest of the process.

Thanks in advance.
Bart

---

### Post by darkod on 2012-05-02
None of the pictures show inside the post. They might be too big in total.

Attach only one screenshot, of the deep search result, and use the Manage Attachments button when you are creating the post, beneath the window where you type the message.

Yes, you will need to change the D to either *, P or L depending. I think your xubuntu partition should be logical because that is according to the cylinders result of fdisk you posted originally.

The windows would need to be changed to P or * depending what partition is bootable (if you have the small bootable partition for win7).

Only after you have all partitions listed, select to write the table. Never before!!!

Post the screenshot and lets see.

---

### Post by n0c0d3 on 2012-05-02
Yes, the pictures came out somewhat different than I expected. I was hoping for thumbnails, but they were shown full sized. I can see them though. I typed the post and uploaded the pictures as attachments, but when I pushed the preview button my geriatric PC got a hick-up and crashed. After resuscitation I linked to the pictures from my attachments in my profile. So far the ramblings...

The pic you asked for is attached. I hope it will show normally this time.

Bart

---

### Post by darkod on 2012-05-02
OK, first of all, you can change the letter specifying the partition characteristics (the first letter in front of each partition in the list) for more than one partition at once. Use the up/down arrows to move from one partition to the next, and the left/right to change the letter.

But before you make the final choice, select one by one the partitions System Reserved, HD, PQSERVICE, and the Linux partition with size of 74317824 sectors. Use the 'P' as you already tried and verify that all of those partitions can be opened and the files read.

If that works out, you are on a good road.

Next, from the list of partitions, move one by one and set the correct letters. It seems they should be:
PQSERVICE, letter P for primary
System Reserved, letter * for primary bootable
HD, P
Linux (size 74317824 sectors), L for logical
Linux swap, L

All the others partitions should continue having the letter D for deleted.
When you have that setup configured, press Enter to continue to the next screen.

Now it should show only the above 5 partitions. Go to write to write that partition table. After that start closing testdisk by selecting Back, or Quit, or whatever the options are on each screen.

That should be it.

---

### Post by n0c0d3 on 2012-05-02
I just made the changes, but didn't 'write' them to the partition table yet. All necessary partition were there, but the Linux partition changed from 'L' to 'Extended' or something like that. I pressed 'quit' and now I have to do the deep search all over again.

But is this right that the L disappears in front of the Linux partition?

Bart

---

### Post by darkod on 2012-05-02
It shouldn't. The extended partition is the container holding all logical partitions. That's why the logical have to be sequential, you can't have one at front of the disk and another at the back.

The extended should contain both linux and linux swap partitions since we are marking both of them as L. Don't worry because you can't see extended partition in the list, it is usually created around the logicals. In many tools it's not shown separately.

---

### Post by n0c0d3 on 2012-05-02
So it's not right for it to change (just to make sure, I'm talking about the screen with the 'write' option in it). I'm sure I marked it as logic, the swap was still 'L' if I remember well.

I'm going to give it anther try (the scan is now at 55%), but if it's the same again I have to press quit again and have to start the scan all over again. Any ideas what to do if it changes to Extended again?

Bart


Edit:

I finished another scan, the same happens when I change the Linux partition to Logical. I've made some screenshots, one after I made the changes right before I pressed enter to continue and one to show what it changes into in the screen which allows me to write the changes to disk. You can see them in the attachments. Last time I pressed quit before I could really investigate it thinking I could return to that screen again. But it seems there are two Linux set up partitions in one extended partition. One 'E' (extended LBA) which contains the actual Linux partition and the Swap partition which are both logical partitions. From what you wrote before I suppose this is actually what is needed, two Linux partitions in the Extended 'container'. 

Is this right and can I write this configurations to the partition table?

Btw, the FAT12 partitions also contain files. Not many, but I have no clue what they are for. Should they be deleted anyway? And is it really okay to set the [system reserved] to primary boot, and not [HD]? I have no clue what I'm talking about, but it just seems strange ;)

---

### Post by n0c0d3 on 2012-05-03
Could you, Darkod, or someone else, please tell me if what's in the last screenshot in my previous post is the right configuration to write to the partition table to try to rescue my HD (dual boot with Grub, Win7 and [X]Ubuntu)?

I'm really unsure about the situation and I really would like someone who knows a thing or two about it to tell me it looks okay, so I can go for the [write] option.

Thanks,

Bart

---

### Post by oldfred on 2012-05-03
It looks reasonable. 

Without some math I cannot be sure it matches your post #3 sizes as testdisk uses CHS where fdisk used sectors. But that is all testdisk is showing.

If the restore of the Windows 7 partition is not exactly as it was originally it will need repairs. Always best to resize Windows 7 using its own partition tools and even then it runs chkdsk on reboot. But  the Windows NTFS partitions have to have partition info inside the PBR - partition boot sector or  first sector of the partition that matches the size of the partition (or the same info as partition table).

---

### Post by n0c0d3 on 2012-05-03
Well, I went for it, but when I reboot I still run into the grub rescue prompt immediately after reboot (I tried several times): "error: unknown filesystem".

I booting the LiveCD again and I'll run another scan to see what it says. I'll report back with the results when it's finished. I hope someone knows what to do next then...


Thanks for the advice anyway,
Bart

PS. I just rebooted. I still have access to my Windows partition from the desktop , but now I also have SYSTEM RESERVED, 38 GB File System and PQSERVICE there. That's pretty odd I'd say, because I've never seen those before on my desktop. I'll start the testdisk scan again now.

PS2:
The Quich Search results are in! 
All partition are marked with a 'D' (Deleted) and the FAT12 are still there as well. I can all access them. Starting the Deeper Search now...

---

### Post by mips on 2012-05-03
What happens if you boot from the Windows 7 DVD slect the repair option and fix your MBR, think the command is fixmbr.

I doubt any of your partitions or data is lost but the more you fiddle with it the greater the chance of stuffing it up. Try the FIXMBR option from a windows dvd as it will overwrite grub and you can then start over again.

---

### Post by oldfred on 2012-05-03
Windows does not show those partitions. 

Most new Windows systems have 4 partitions. Windows uses a hidden 100MB boot/repair & the main c: drive. Then the vendor does not give you a install DVD, but just stores an image of your hard drive on the hard drive and most vendors seem to just use another partition for vendor misc utilities. Then all 4 partitions are used. Microsoft loves it as it is difficult to install anything else and the vendor is happy as his help desk only knows their system so they have fewer users calling with issues they cannot deal with.

If you did not make the set of DVD's from the Vendor you should as if hard drive fails you have no way to restore system. But you also should do full backups of Windows and any data in Linux you want.

---

### Post by n0c0d3 on 2012-05-03
I do have the Win7 recovery DVD's. I've not used them for a long time, so I can only hope they're not somehow damaged. But as oldfred says, Windows doesn't see any partitions that are not MS supported so I doubt a Win-recovery will do what I need it to do.

---

### Post by mips on 2012-05-03
> **n0c0d3 said:**
> I do have the Win7 recovery DVD's. I've not used them for a long time, so I can only hope they're not somehow damaged. But as oldfred says, Windows doesn't see any partitions that are not MS supported so I doubt a Win-recovery will do what I need it to do.

It does not have to see any of the non-ms supported partitions, you just want to restore your MBR for starters. Any remaining problems after that you can then deal with one by one if there are any. If you have bad linux partitions you could always remove them and reinstall as your main concern seems to be accessing your windows install right now.

---

### Post by n0c0d3 on 2012-05-03
> **mips said:**
> It does not have to see any of the non-ms supported partitions, you just want to restore your MBR for starters. Any remaining problems after that you can then deal with one by one if there are any. If you have bad linux partitions you could always remove them and reinstall as your main concern seems to be accessing your windows install right now.
That's true, Windows is my main concern. But first I want to explore other options, if I can preserve my Linux partitions I see no reason not to try that first. I had fine-tuned my Xubuntu to my appreciation for over two years as well, so to start from scratch is not my first option, even though I think it may very well end up there.

But when I restore the MBR with a Win7 recovery DVD, will it not destroy GRUB as well, leaving me more or less where I am now? Or will it create a new MBR so when I boot I directly boot Windows?

---

### Post by n0c0d3 on 2012-05-03
After the deeper scan was finished it seems the changes were not written to the partition table as needed. I attached a screenshot of this. System Reserved is still primary and PQService is still primary bootable, while they should be switched around.

I just gave it another go with the same recommended settings, rebooted, and again I end up on the grub rescue prompt.

Any ideas left where to go from here? Or should I just give it a try with the main Windows partition "HD" (where all my stuff is) as a primary bootable partition? I could also try to install Xubuntu 11.10 from the LiveCD which I'm working on now to see if that will create a bootrecord and restores Grub to both Windows and Linux. If it recognizes there is already a (X)Ubuntu partition, does that ask me to upgrade or repair it, as the last version I had was 11.10?

---

### Post by oldfred on 2012-05-03
It does not look like you recovered you Linux partition.

You can use gparted or Disk Utility to change boot flag, but boot flag is only used by Windows if Windows is booting from MBR. Grub does not use boot flag and chainloads directly to the Windows PBR - partition boot record. Windows in the MBR is really just finding the partition with the boot flag and chainloading to that PBR to find more boot code.

You may have to reinstall grub2's bootloader anyway.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by mips on 2012-05-03
> **n0c0d3 said:**
> 
But when I restore the MBR with a Win7 recovery DVD, will it not destroy GRUB as well, leaving me more or less where I am now? 

Or will it create a new MBR so when I boot I directly boot Windows?

Yes it will destroy GRUB.

Yes it will install the Windows boot loader allowing you to boot into Windows.
Once you got this going and verified that Windows is fine you can use a livecd to chroot into you're / partition and reinstall Grub again in the hopes that things work out. If this does not work out then you can start faffing around with your linux partition. You could also try booting the the linux partition from a external GRUB.

Leave testdisk for now as it will find just about any partition ever created on that HDD, if you tell it to start recovering partition you can seriously screw things up, been there done that, so exercise extreme caution. Those first two partitions are usually hidden manufacturer partitions you don't normally see.

---

### Post by darkod on 2012-05-03
First of all, don't worry about the grub rescue prompt. The main goal is to have all partitions available and correct.
In the first (and second as it seems) testdisk scan not only that the linux (xubuntu) partition was marked as Deleted, but also your win7 partition (HD).
Basically the system partitions for both OSs. The goal is to have them back.

Fixing any bootloader later is piece of cake. So let it give you the grub rescue all it wants, work from live mode temporarily and after finishing with testdisk see what other tools like fdisk and parted show, which partitions are there and which missing.
sudo fdisk -l
sudo parted /dev/sda unit s print

If the table was written correctly I have no idea how would it show those partitions as D again. :(

---

### Post by mips on 2012-05-03
This is gonna end in disaster. Can't watch, leaving now.

---

### Post by oldfred on 2012-05-03
@mips
We always love the optimist.;)

Glass is always half full, never half empty.

---

### Post by n0c0d3 on 2012-05-03
> **oldfred said:**
> It does not look like you recovered you Linux partition.

You can use gparted or Disk Utility to change boot flag, but boot flag is only used by Windows if Windows is booting from MBR. Grub does not use boot flag and chainloads directly to the Windows PBR - partition boot record. Windows in the MBR is really just finding the partition with the boot flag and chainloading to that PBR to find more boot code.

You may have to reinstall grub2's bootloader anyway.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
I'm creating a backup of my Windows install to an external harddrive at the moment, so I'll be trying to get Grub back as described when that's finished because I can't do any rebooting now anyway (it may take a couple of hours for the backup to finish I think). So I think I better leave the hard-core stuff for tomorrow.

Is there a particular order in I should follow, I mean the first link first or doesn't it really matter? I haven't read it yet, so I'll heave to dig through it all first.

And btw, would Repair Disk do any good? I may be able to burn it somewhere else next weekend or next week, or would that be a useless exercise?

Bart

---

### Post by darkod on 2012-05-03
Yes, a repair disc, or rescue cd or what ever it's called exactly would actually do a better job. But try to create it on a computer which has the same (or very close) win7, like 32bit or 64bit, Home, Pro, etc. Not sure if you can use it if the version is very different.

You have to be careful with recovery DVDs. In most cases, their task is to wipe all your hdd (losing you all data and partitions), and create the factory image (including all bloathware that came with it and that you might have removed). I'm not sure if a recovery DVD can allow you to only restore the bootloader. In fact, in some cases people that have only started their recovery partition found that the partition table was started to be changed right away.

Unless you make a full backup of your xubuntu after your windows backup finishes, using a recovery DVD might blow it away.

---

### Post by n0c0d3 on 2012-05-03
> **darkod said:**
> First of all, don't worry about the grub rescue prompt. The main goal is to have all partitions available and correct.
In the first (and second as it seems) testdisk scan not only that the linux (xubuntu) partition was marked as Deleted, but also your win7 partition (HD).
Basically the system partitions for both OSs. The goal is to have them back.

Fixing any bootloader later is piece of cake. So let it give you the grub rescue all it wants, work from live mode temporarily and after finishing with testdisk see what other tools like fdisk and parted show, which partitions are there and which missing.
sudo fdisk -l
sudo parted /dev/sda unit s print

If the table was written correctly I have no idea how would it show those partitions as D again. :(
We'll see where it ends. I really appreciate your help, but when the hardware doesn't cooperate there's nothing much we can do. I have no clue why the partition tables are not updated as they should be. There's nothing much I can do wrong in a screen with only two options...

I made screenshots of the fdisk and parted results. In the fdisk at the bottom is my external HD which is connected, you can ignore that drive. All those numbers don't mean much to me, so hopefully you can see if they're configured right.

Thanks again,
Bart

---

### Post by n0c0d3 on 2012-05-03
> **mips said:**
> This is gonna end in disaster. Can't watch, leaving now.
Disastser is a little over the top I think :-p No one is going to die andas long as the hardware is not fubar, a clean install will do the trick. It's just take a long time to get back to where I was before, that's not fun, but no disaster.

---

### Post by n0c0d3 on 2012-05-03
> **darkod said:**
> Yes, a repair disc, or rescue cd or what ever it's called exactly would actually do a better job. But try to create it on a computer which has the same (or very close) win7, like 32bit or 64bit, Home, Pro, etc. Not sure if you can use it if the version is very different.

You have to be careful with recovery DVDs. In most cases, their task is to wipe all your hdd (losing you all data and partitions), and create the factory image (including all bloathware that came with it and that you might have removed). I'm not sure if a recovery DVD can allow you to only restore the bootloader. In fact, in some cases people that have only started their recovery partition found that the partition table was started to be changed right away.

Unless you make a full backup of your xubuntu after your windows backup finishes, using a recovery DVD might blow it away.
I meant this boot-repair: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) It downloads as an iso so it not system dependent. I would only need to find a place where I can burn it, when I have the time and other people have the time and such...
I just read (I think in one of the pages oldfred linked to) it can also run from a LiveCD, but the only thing I've been able to find is that it can run as LiveUSB. But I still need to read those pages to better grasp what they're actually doing.

I've made a full backup of my profile directory in /home of my last Xubuntu install. And I don't think it's wise to just  copy and replace everything after a new install. My external drive is NTFS and I once understood that copying from ext to NTFS and back again would change permissions and cause security hazards. So I don't think it's wise thing to do.

---

### Post by oldfred on 2012-05-03
If you just copied /home to NTFS then is is not so difficult to reset permissions & ownership, but system is a lot different as it is not the same everywhere. It would have been better to use Linux formats or a compressed format like the old school tar.

Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

Ubuntu /home is permissive:
[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access)
.dmrc errors- drs305
[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)
.ICEauthority errors
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)
chmod 755 /home/username
sudo chown $USER:$USER /home/username/.ICEauthority
sudo chmod 644 /home/username/.ICEauthority
sudo chmod 644 $HOME/.ICEauthority

---

### Post by VMC on 2012-05-03
> **oldfred said:**
> If you just copied /home to NTFS then is is not so difficult to reset permissions & ownership, but system is a lot different as it is not the same everywhere. It would have been better to use Linux formats or a compressed format like the old school tar.

...

Exactly. NTFS removes the needed premissions. During the testing of 12.04 I use this tar script from my ~deb folder to backup my ~home
folder

```
tar cfpvz ~vmc/debs/tarzan.tgz --exclude=home/vmc/debs --exclude=home/vmc/.local/share/Trash --exclude=home/vmc/.thumbnails ~vmc
```

---

### Post by n0c0d3 on 2012-05-03
Interesting posts about the backups and scripts. Something to bookmark for sure!

Bur for me it's too late. I've tried to find my (former) Xubuntu partition so I can copy it all, but I've not found it yet (didn't try everything I could though) and even then the upgrade may have changed a lot already. So I think it's of not much use to backup it all. It's just for my personal stuff, some settings and config files and such.
I'm still copying my Windows stuff. It hung somewhere along the way and it's going to take much longer than I anticipated...

---

### Post by mips on 2012-05-04
> **n0c0d3 said:**
> 
I'm still copying my Windows stuff. It hung somewhere along the way and it's going to take much longer than I anticipated...

Are you copying or imaging the partitions? Imaging would be much faster and will give you an exact duplicate of the partition(s).
You can use dd (or if it picks up a error and halt use GNU ddrescue) and image to a file. These image files can be mounted and worked on. I would image the windows partitions and then image the entire drive. You can then work on the drive image to try and recover your / partition. Much safer and way more convenient.

---

### Post by darkod on 2012-05-04
> **mips said:**
> Are you copying or imaging the partitions? Imaging would be much faster and will give you an exact duplicate of the partition(s).
You can use dd (or if it picks up a error and halt use GNU ddrescue) and image to a file. These image files can be mounted and worked on. I would image the windows partitions and then image the entire drive. You can then work on the drive image to try and recover your / partition. Much safer and way more convenient.

What I don't like with dd is that it copies all sectors including the empty ones (or I might be wrong). Especially with disk sizes these days, you can easily have a 1TB partition used only 15-20%. Why wait hours to copy the empty sectors too.

You can use something like FS Archiver for example, or another tool that saves only the data regardless how big the partition is.

---

### Post by n0c0d3 on 2012-05-04
Hi again

I make all my backups by hand (i.e. copy&paste). I think I'm done with it now, but hey, one never knows what one forgets... I've never heard of dd or anything like that. I don't need an image of the entire drive I think.

but I've been able to burn 3 CD's. Xubuntu 10.04, both desktop and alternative and boot-repair-disk ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) ). I've written on them what they contain this time, so it not very likely I'm going to ruin them this time ;)

When I do an 'fdisk -l' in 12.04 I get no response. There seems to be an option in between the fdisk command and the list operator in the latest version. Because you guys know much better what you want than I do I'll post what I get in fdisk -h, so if you can give me the right command I'll post the reults again.
> 
xubuntu@xubuntu:~$ fdisk -h
Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>             sector size (512, 1024, 2048 or 4096)
 -c[=<mode>]           compatible mode: 'dos' or 'nondos' (default)
 -h                    print this help text
 -u[=<unit>]           display units: 'cylinders' or 'sectors' (default)
 -v                    print program version
 -C <number>           specify the number of cylinders
 -H <number>           specify the number of heads
 -S <number>           specify the number of sectors per track
I made a report with Boot-Repair. I've run it twice, the first time without any of the options checked that I thought would make any changes to grub, but 'm not really sure it really didn't change anything. This is the report that gets automatically posted:
[http://paste.ubuntu.com/967138]("http://paste.ubuntu.com/967138/")
I also had my external drive and thumb drive still plugged in.

The second time I removed the USB-drives and choose the simple option to just check the system. This report was made: 
[http://paste.ubuntu.com/967149]("http://paste.ubuntu.com/967149/")
What's clear is that something is wrong with the size of the Windows (sda3) partition.

I also just finished a deep testdisk scan again. The results are in the attachment below, but they're not encouraging. Immediately after the scan I get the message the drive is not right sized. You can see that in the first screenshot. The second screenshot shows the screen that comes after the first one, but this one look similar to what I've had before. All partitions are still there, they seem to be of the same size as before and they're still marked as deleted.

What I didn't do before was running the executable as root, but it never gave any problems or warnings. This time the hard drive didn't show up when I was not root. Maybe I had to have been root before to actually make changes to the partition table. The difference is that I now extracted testdisk to the desktop and before I used the default download folder. I don't know if that changes executable permissions, or that 11.10 vs. 12.04 makes the difference. Maybe now the changes will be written to the partition table when I try.

Okay guys, I'll let you shine your light on the matter before I make any decisions and if you have any idea what to do, please let me know.

Thanks,
Bart

Btw, that second drive in the first screenshot of the testdisk deeper scan of 1400GB looks like my external HD, but it's not even plugged in during this entire scan session. Strange...

---

### Post by mips on 2012-05-04
> **n0c0d3 said:**
> 
When I do an 'fdisk -l' in 12.04 I get no response. 

You need to use **sudo** or you will get no response, **sudo fdisk -l**

---

### Post by n0c0d3 on 2012-05-04
> **mips said:**
> You need to use **sudo** or you will get no response, **sudo fdisk -l**
LOL. You make me scream. Okay, I make myself scream :)

Another screenshot of the sudo fdisk then. Why not...

---

### Post by darkod on 2012-05-04
Yeah, you need sudo for both fdisk and testdisk. The testdisk instructions did say sudo I think.

Right now the result of fdisk looks good. Can you open all the partitions from live mode and see the data inside?

As far as the bootloader is concerned, I can immediately see that it is looking for its files in sda6 which is not correct. It should be sda5. But that is easily fixed, forget about it right now. The following question is more important: According to the latest results you have ubuntu 11.04 on sda5, and not xubuntu. Does that sound correct to you? Are we looking for xubuntu or ubuntu?

This is more important than the bootloader right now, you will fix grub2 later.

---

### Post by n0c0d3 on 2012-05-04
Yes, I get icons of PQService, HD, System Reserved and the 38 GB (Linux) partitions on my desktop and I can all access them and see the files. No problem there.

And before I tried to upgrade I had Xubuntu 11.10 installed, I'm 100% sure of that. This 11.04 version in that report is very strange indeed. I've got no clue how that can appear there.
(The "X" of Xubuntu doesn't really matter I think, that's got really nothing much to do with the OS as far as I know, Xubuntu == Ubuntu, it only has  another desktop.)

And should I try to write to the partition table again from testdisk? Now I'm at least sure to be logged in as root, or do you think it may screw it all up even more?

---

### Post by darkod on 2012-05-04
Hmm, the kernels on sda5 are from version 11.10, weird that the script reports it as 11.04. Maybe it's confused because of the recovery procedure. Also, the grub.cfg on sda5 is not correct any more since it was on sda6 during install.

If you can read the data from the partitions, I would say don't use testdisk again.

I would chroot and purge grub2, then reinstall it so that it can recreate it's config files from scratch. I am not sure if simply recreating them will be enough, I would rather purge it all. If you agree, the procedure from live mode is:
Mount your 11.10 root and chroot into it:
```
sudo mount /dev/sda5 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Purge grub2 and reinstall, recreate files and install on MBR again:
```
apt-get remove --purge grub-pc grub-common
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/sda
```

Exit chroot and unmount all:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Restart and see how it goes. I hope you wouldn't need to touch anything else like initramfs, etc, after you recovered the partition. Lets see with only grub2 reinstall.

---

### Post by n0c0d3 on 2012-05-04
I doesn't seem to go well. The first block of commands (the mounting part) is going well. I get problems with the 'Purge' block, also when I put 'sudo' in from of the line: "unable to resolve host xubuntu". I thought it might have something to do with not being logged in as root again, so I 'sudo-su'ed', then I get the same xubuntu-host error again. I rebooted, because I thought it might have something to do with all the partitions already being mounted, but then again no go.
The first block goes fine, but after the first command in your second block, after having logged in as root (and the previously mentioned xubuntu error) I get:
> 
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
I checked, but the 'lock' file is there, so it might have something to do with the xubuntu-error and not having the right permission? I'm logged in as root in the terminal screen though.

---

### Post by darkod on 2012-05-04
Sounds like you don't have internet in live mode.

As far as root is concerned, the chroot is transferring you "inside" your installation with root permissions. That's why the second block has no sudo in front, not needed.

---

### Post by n0c0d3 on 2012-05-04
> **darkod said:**
> Sounds like you don't have internet in live mode.

As far as root is concerned, the chroot is transferring you "inside" your installation with root permissions. That's why the second block has no sudo in front, not needed.
I can use the browser without any problems, I copy&paste your commands right into the terminal from it, so I don't think internet access is the problem...

Edit:
And I just tried the Update Manager. I get 50 updates available within a couple of seconds (didn't install anything of course).

---

### Post by n0c0d3 on 2012-05-05
I entered a somehwat fatalistic mood so I just tried all the commands from darkods previous posts despite any errors I got. I rebooted and there was grub again, but only with entries of the 3.0.0-19 (and recovery) kernel, previous Linux versions and memory tests. Windows was missing. Trying to boot the linux kernel end in an error: "init: unreadahead main process (298) terminated with status 5".  I suppose this is somputerlingo for "I hate you and you're all gonna die!) ;-)

Now I'm in this mood I might as well try to write the testdisk corrections to the partition tabel for that last time.

In case that doesn't work out I'm think it might be better to just dunk the Win7 recovery CD into the tray and start with an entirely fresh system (hoping these CD are still in working order). Unless someone still has an idea to get the windows partitions back on track of course.

Any advice left?

Thanks,
Bart

---

### Post by oldfred on 2012-05-05
If you can partially boot I do not think testdisk will help on anything.

Your reinstall of grub, updates the grub menu, but I do not think it runs the os-prober to find other installs until you boot, so not seeing the Windows install is ok.

After you boot you run this and it should then find Windows install if it is ok.

sudo update-grub

Can you boot to command line from recovery mode? Or is error before that.

---

### Post by n0c0d3 on 2012-05-05
> **oldfred said:**
> If you can partially boot I do not think testdisk will help on anything.

Your reinstall of grub, updates the grub menu, but I do not think it runs the os-prober to find other installs until you boot, so not seeing the Windows install is ok.

After you boot you run this and it should then find Windows install if it is ok.

sudo update-grub

Can you boot to command line from recovery mode? Or is error before that.
I just tried to boot into recovery mode, but it's hanging already for a couple of minutes on the same error. I get two extra lines, about adding swap on /dev/sda6 and a remount error of sda5 or something like that. Then it's all eerily silent... So no cammand prompt in recovery. I'm booting the LiveCD now.

Edit:
I consider the Linux install to be lost. Windows seems to be on a partition that's not of the right size. I think the main question is how to correct this.

---

### Post by darkod on 2012-05-05
I think you might have recovered a wrong partition. But you said only that partition was displaying files with P in testdisk.

I think the system is too much messed up whether sda5 or sda6 is root and swap (and vice-versa).

In live mode, mount sda5 and lets see what fstab says. Also post the UUIDs of all partitions with blkid:
sudo mount /dev/sda5 /mnt
cat /mnt/etc/fstab
sudo blkid

As I said above, this is far from standard grub recovery and I am not familiar with tools like initramfs, etc, if something else needs to be run after recovering the partition.

---

### Post by n0c0d3 on 2012-05-05
> **darkod said:**
> I think you might have recovered a wrong partition. But you said only that partition was displaying files with P in testdisk.

I think the system is too much messed up whether sda5 or sda6 is root and swap (and vice-versa).

In live mode, mount sda5 and lets see what fstab says. Also post the UUIDs of all partitions with blkid:
sudo mount /dev/sda5 /mnt
cat /mnt/etc/fstab
sudo blkid

As I said above, this is far from standard grub recovery and I am not familiar with tools like initramfs, etc, if something else needs to be run after recovering the partition.
I can only remember that the middle linux partition (the big one) was accessible. But I might be somehow wrong about that. But you seem to be right that swap is on sda5 right now. Which is strange because every thing else I do shows that swap is on sda6 (fdisk and gparted). I'm totally confused now.

But couldn't I try to 'check and repair' the windows partition (sda3) from gparted?

Btw, I attached a screenshot of the outcome of the commands you just gave.

---

### Post by darkod on 2012-05-05
Root and swap were "switched" during the install, but since fstab works with UUIDs, it should be OK. But I'm not experienced enough to know if there is another place where there might be a conflict because root is sda5 now as opposed to sda6 during the install.

I wouldn't try and check and repair of windows system partitions. By the way, why would it need repair, you said all data is accessible, right?

---

### Post by n0c0d3 on 2012-05-05
> **darkod said:**
> Root and swap were "switched" during the install, but since fstab works with UUIDs, it should be OK. But I'm not experienced enough to know if there is another place where there might be a conflict because root is sda5 now as opposed to sda6 during the install.

I wouldn't try and check and repair of windows system partitions. By the way, why would it need repair, you said all data is accessible, right?

Let's not even consider my experience, You're trying to help me the best you can. I really appreciate that.

And the Win partition is accessible, but it seems there is something wrong with the size or something like that. GParted gives the message on sda3 that's in the (yet another) screenshot I attached to this message.

---

### Post by oldfred on 2012-05-05
As the error message says you need to run chkdsk from Windows.

The NTFS partition boot sector has to have to partition info inside it that matches the partition. Sometimes just chkdsk is needed and sometimes chkdks & fixboot are required to repair the NTFS partition boot sector.

Always run chkdsk and run again until there are no errors, that may be all that is required


[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by n0c0d3 on 2012-05-05
I read that. As I said in the very first post with which i opened this thread running chkdsk is in fact where the whole misery started. It's obvious I can't run it from HD anymore, but maybe I could run it from a windows recovery disk to give it another try.I have the recovery disks that came with the laptop and a Neosmart Win7 recovery disk which seems to have recovery tools, but I've never used it before, so I'll have to wait and see. I could give that a go first.

---

### Post by darkod on 2012-05-05
Use the Neosmart. The manufacturer discs might start some factory restore process.

You should be able to run it from the Neosmart after you open the command prompt.

---

### Post by n0c0d3 on 2012-05-05
When I use the Neosmart CD I can get into the command line, but when I try to do a chkdsk /f I get the message "Cannot lock current drive. Windows cannot run disk checking on this volume because it is write protected."

There's another option in the recovery screen "Startup Repair". The Diagnostic screen is pretty large and I can't copy it or make screenshot, but there seem to be no errors.

There are other options: 'System Restore', 'System Image recovery', 'Windows Memory Diagnostics' and of course the command Prompt.

But I think if chkdsk could do anything it doesn't do anything to grub, so I couldn't then yet boot Windows for the changes to take effect. Or could that somehow be resolved?

Edit:

But if I could restore the windows partition with the official recovery CD's, I might loose grub and Linux, but not Windows. Grub could then probably be reinstalled, and it will anyway when I install Xubuntu again. But then my current Windows installation will not be lost. Or am I thinking wrong somewhere?

---

### Post by darkod on 2012-05-05
Shouldn't it be something like: chkdsk c: /f

Maybe it's trying to look in a wrong place without the c:.

---

### Post by n0c0d3 on 2012-05-05
I guess you're right. That's what the page oldfred linked to says as well. I overlooked that earlier. I didn't do that either when I did the chkdsk which gave me the troubles in the first place, because I just copied what's in the GParted warning screen.. I'll give it a go and see what happens.
But that still wouldn't solve the grub problem I guess. If I need to reboot for the changes to take effect and the windows partition is not in grub, then I'm encountering some circular problem isn't it?

---

### Post by oldfred on 2012-05-05
Ubuntu/Linux will not mount a NTFS partition that needs chkdsk to prevent further damage that chkdsk may not then be able to fix. So as long as it needs chkdsk Ubuntu/grub will not see it. Once fixed then it should mount it, find the Windows boot files and add it to the menu with the sudo update-grub command.

---

### Post by n0c0d3 on 2012-05-05
> **oldfred said:**
> Ubuntu/Linux will not mount a NTFS partition that needs chkdsk to prevent further damage that chkdsk may not then be able to fix. So as long as it needs chkdsk Ubuntu/grub will not see it. Once fixed then it should mount it, find the Windows boot files and add it to the menu with the sudo update-grub command.
I can enter the Windows drive from the LiveCD though.
I tried chkdsk c: /f, but it seems to check a different drive than intended. It only seems to have 104422 KB disk space and 28 fils in 55 indexes and finds no errors. I've been trying to find a command to list all drives. I found 'fsutil fsinfo drives', but that command is not recognized. fdisk is not part of that command line package either.

I think I better try to see what the original recovery cd has to offer, unless you have better ideas.

---

### Post by n0c0d3 on 2012-05-05
Update:

I found a command to list the drives: 'wmic logicaldisk get name'. But I later noticed that in the start screen of the recovery cd the drive is also mentioned. It turned out to be 'e:'.

I ran 'chkdsk e: /f'. There seemd to be 81 reparse records processed and somewhere it said that "CHKDSK discovered free space marked as allocated in the Windows bitmap", immediately followed by "Windows made corrections to the file system". But later it said to have failed to transfer logged messages to the event log with status 50. But I don't know if that's of any importance.

I rebooted, but there was no entry of Windows in the grub menu. In GParted (run from the LiveCD) there's no more warning for the Windows drive (sda3), or any other warning. 

But the drives are not automatically mounted anymore in /media. when I click the icons on the desktop. I mounted the Windows partition (sda3) manually and it's still accessible. 
I just rebooted and there's still no entry for Windows in grub. GParted is again not giving any errors or warnings and I can boot all drives (windows, Linux, etc.) from the desktop of the LiveCD again.

So it seems one major hurdle has been taken. Any ideas where to go from here?

---

### Post by darkod on 2012-05-05
Don't worry about the /media mounts. In fact, I would disable any auto mounts you might have had configured until the system is fully operational.

Since sda3 sounds fixed, boot ubuntu and try the sudo update-grub as suggested. See if that picks it up.

---

### Post by n0c0d3 on 2012-05-05
> **darkod said:**
> Don't worry about the /media mounts. In fact, I would disable any auto mounts you might have had configured until the system is fully operational.

Since sda3 sounds fixed, boot ubuntu and try the sudo update-grub as suggested. See if that picks it up.
The other partitions don't mount automatically, they only mount when I double click the icons.

I still can't boot into Xubuntu from grub, not in recovery mode either, I still get the same error as I mentioned earlier. So no command line to enter anything except for this LiveCD. Or do you mean the '3 block' instructions in one of your previous posts? Should I give those another try?

---

### Post by darkod on 2012-05-05
> **n0c0d3 said:**
> The other partitions don't mount automatically, they only mount when I double click the icons.

I still can't boot into Xubuntu from grub, not in recovery mode either, I still get the same error as I mentioned earlier. So no command line to enter anything except for this LiveCD. Or do you mean the '3 block' instructions in one of your previous posts? Should I give those another try?

No, I didn't mean that. This thread has become so long I forgot you still can't boot xubuntu from the hdd.

At this moment I am running out of fresh ideas. We need to consider the option that a wrong partition is recovered maybe. But the other two linux partitions found by testdisk had much smaller sizes than this one.

Do you remember how big your root is expected to be? Does this partition you recovered sound correct in size?

---

### Post by n0c0d3 on 2012-05-05
Actually I don;t remember how large the linux partition was. I resized (increased) it a couple of times before my last try, always without real  problems. I remeber having to boot Windows 1 or 2 times after that before it came up normally, but that seemed to be normal for what I read.

Still from day one of the current problem there has only been one linux partition with files in it, and that's the one that was set as logical in testdisk, I'm very very sure of that. But in the end the other partitions didn't disappear, even though they were marked as deleted.

I could still try to set other linux partitions as logical. I think my previous Xubuntu install is beyond repair anyway, so what's there to lose? Would that be an idea? Maybe it's interesting to see what testdisk has to say now anyway.

But that's be for tomorrow anyway. I'm too sleepy now to wait for a deep scan to finish. I'll download and start it and see tomorrow.I'll let you know what it says.

---

### Post by n0c0d3 on 2012-05-06
Okay, the deepscan is finished so i thought to give an update. And I made some screenshots again, just because I can ;) The first one, after the deeper search, is not different than before and just as weird. The hard drive seems to be too small? There are no other drives plugged in and I've not been in the bios since I set the boot order to boot from the DVD drive over half a week ago, if not more. And I didn't change any jumpers on my HDD either of course.

The second though, is very different from the previous scan (this one: [http://ubuntuforums.org/attachment.php?attachmentid=217288&d=1336160132](http://ubuntuforums.org/attachment.php?attachmentid=217288&d=1336160132) ). The latest screenshot is the second one attached below. 

The linux-swap and the FAT12 partitions have disappeared!! Most others are still marked as deleted (not all though), but the numbers are still the same and I can still access them all with 'p'., but the 2nd Linux partition (74317824 sectors and 38 GB) is the only one with my files in it and the other two Linux partitions (first and third in the list) tell me "No file found, filesystem may be damaged" when I 'p' them.

It may be again obvious that I don't have a clue what's going on.

---

### Post by westie457 on 2012-05-06
Hi just some thoughts and ideas on your situation.

Are you able to boot into Windows at all?

As far as the other partitions go it might be a good idea to try 'fixparts' available here. [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Personally I would wait for 'darkod' or 'oldfred' to offer an opinion on this however there is no harm in you reading up on it.

If either of them agree about 'fixparts' things should fall into place and we can get you up and running again. Hopefully without having to reinstall.

---

### Post by darkod on 2012-05-06
Aside from the fact that it doesn't show the swap partition at all, how can the linux partition be D?

You have it recovered already and working, even though xubuntu can't boot fully. But from live mode you can access the data on that partition and all.

It should be L in testdisk at least.

That message about the disk too small is an error I think. It correctly says your disk is 320GB. But it seems there are traces of some error in the partition table somewhere (it might be a deleted partition so no big deal), which is much larger than the disk. So it says, disk too small.

Look at the first attachment, it says partition that can't be recovered, look at their size. 1720GB which is of course too big for your 320GB hdd.

I like the fixparts idea. But one thing first. Quit testdisk without writing (changing) any tables and try the parted print again, just to check if the windows (HD) and linux partitions are reported there.

Then open the disk with fixparts, take a look at its print also, and whether the partitions match. If they look OK, do a write in fixparts too. Sometimes overwriting the table with the same table can fix some smallish errors. But only write it if the partitions reported by fixparts correspond to what you have.

---

### Post by n0c0d3 on 2012-05-06
Thanks darkod and westie457,

In my previous post I forgot to mention I already noticed the swap partition was still there in GParted. Here's what Parted 'minus G' has to tell about it:

> 
xubuntu@xubuntu:~/Desktop$ sudo parted /dev/sda unit s print
Model: ATA WDC WD3200BEVT-2 (scsi)
Disk /dev/sda: 625142448s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system                    Flags
 1      63s                  25173854s     25173792s     primary   ntfs
 2      25173855s      25382699s         208845s     primary   ntfs               boot
 3      25382700s    547543394s   522160695s     primary   ntfs
 4      547545088s  625141759s     77596672s     extended                      lba
 5      547547136s  621864959s     74317824s     logical   ext4
 6      621867008s  625141759s       3274752s     logical   linux-swap(v1)
As far as my limited knowledge goes it looks fine to me, but I think it's better not to trust my opinion on this.

I installed sfdisk, it tells me to create a backup of the partion table with this command: sfdisk -d /dev/sda > parts.txt. There was a waning though:
> 
xubuntu@xubuntu:~/Desktop$ sudo sfdisk -d /dev/sda > parts.txt
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
xubuntu@xubuntu:~/Desktop$ 
The contents of the file is something similar to what Parted produced, so I guess that's okay then.


For the sake of completeness, here's what I did so far:
> 
root@xubuntu:/home/xubuntu/Desktop# fixparts /dev/sda
FixParts 0.8.4

Loading MBR data from /dev/sda

MBR command (? for help): ?
a    toggle the active/boot flag
c    recompute all CHS values
l    set partition as logical
o    omit partition
p    print the MBR partition table
q    quit without saving changes
r    set partition as primary
s    sort MBR partitions
t    change partition type code
w    write the MBR partition table to disk and exit

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 625142448 sectors (298.1 GiB)
MBR disk identifier: 0x9BB2DCDA
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1                                  63      25173854    primary                  Y         0x07
   2             *        25173855      25382699    primary                  Y         0x07
   3                       25382700    547543394   primary                  Y         0x07
   5                     547547136    621864959   logical         Y                     0x83
   6                     621867008    625141759   logical         Y                     0x82

MBR command (? for help): 

I think it's odd testdisk shows sda3 through 6 as deleted while parted and FixParts say they're either primary or logical. Further it actually looks fine to me.

So this is where I am right now. I think it's better not to make any decisions or changes myself (I wouldn't even know what to change) and that it's better to let you guys shine your light on it and advice me what's best to do.

Thanks,
Bart

Btw, the tables looked nice and orderly when I pasted them. Now they look very messy, I'm sorry for that. That's why I like screenshots better... If you would like me to post screenshots, just let me know and I'll post them.

---

### Post by darkod on 2012-05-06
Since you made a backup of the partition table, and fixparts shows all 5 partitions present, at the fixparts prompt I would use 'w' to write the table again.

Doesn't matter that you didn't change anything and the written table will be the same as the old one, sometimes overwriting it might solve an issue (hopefully :) ). Since we are not sure where the problem is (or even if there is a major problem), lets try that.

After this, I am more and more sure that if (x)ubuntu doesn't boot, it's something within the installation and not a problem with the partitions. The partitions look good now both in parted and fixparts. And fdisk.

---

### Post by n0c0d3 on 2012-05-06
That's there's a problem with the Xubuntu install is obvious. The upgrade hung half way. That Windows doesn't boot is of greater concern.
Btw, I'm in the middle of a reboot to see what grub has to say and what the previous Xububntu install does., which seems to hang.But i always like to wait for a couple of minutes. Nothing seems to happen anymore, not even an error message. Windows is still not present.

I'll reboot in the LiveCd again and write the changes to the partition table and see what happens then....

---

### Post by darkod on 2012-05-06
Since xubuntu can't boot so you can run update-grub, you have no chance to try add windows to the boot menu.

But if xubuntu still continues to fail, you can temporarily install lilo mbr which should boot windows directly. Lets see how this latest attempt goes, and then you can install lilo mbr.

---

### Post by n0c0d3 on 2012-05-06
Not completely unexpected, but after writing the table to disk and rebooting nothing happened.normal the LiveCD asks me to eject the CD, but this time it just ejected it and seemed to hang with a black screen. I decided to 'pull the plug' myself. Grub hadn't changed. No windows partition... I tried to boot Xubuntu from HDD, but the now so familiar error appeared again.

Booting the LiveD again, awaiting instructions ;)

---

### Post by n0c0d3 on 2012-05-06
> **darkod said:**
> Since xubuntu can't boot so you can run update-grub, you have no chance to try add windows to the boot menu.

But if xubuntu still continues to fail, you can temporarily install lilo mbr which should boot windows directly. Lets see how this latest attempt goes, and then you can install lilo mbr.
We seemed to have crossed each other.

I was thinking, since I have access to the previous Xubuntu install, I can make changes to grub files manually. A prerequisiste is that I, and of course you have to tell me, where I should change what.

I wouldn't know how to install lilo. I'll look into it. But first coffee! ;)

---

### Post by darkod on 2012-05-06
From live mode:
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

That will write a generic mbr, similar to the windows bootloader. Note that there will be some warnings that you need to additionally configure lilo and it won't work, but ignore all that. You are just writing the mbr part with it, not trying to use it as main bootloader. Just execute the above commands and ignore its messages.

After you restart windows should load directly. Or at least try to.

---

### Post by n0c0d3 on 2012-05-06
Wooow!!! Windows boots up again! You're my hero darkod!

It was the first time in my life I felt joy when hearing that welcoming tune when logging in ;) I'm never going to touch this laptop ever again, i'm afraid I might do harm to it ;) Okay, just kidding...

But now what? Should I run chkdsk c:/f again or something like that? Or should I now try to install/upgrade Xubuntu 12.04 again? Any ideas?

---

### Post by darkod on 2012-05-06
Yeah, you can try chkdsk but if it boots fine it looks fine. The chkdsk is only for the windows partition.

But having mentioned that, it might be a good idea to run fsck on the linux partition. It has to be from live mode, even if it could boot (and it can't).

So, when ever you feel like it, boot into live mode and without mounting sda5 anywhere, do:
sudo fsck /dev/sda5

See if it says it's clean or not.

---

### Post by n0c0d3 on 2012-05-06
> **darkod said:**
> Yeah, you can try chkdsk but if it boots fine it looks fine. The chkdsk is only for the windows partition.

But having mentioned that, it might be a good idea to run fsck on the linux partition. It has to be from live mode, even if it could boot (and it can't).

So, when ever you feel like it, boot into live mode and without mounting sda5 anywhere, do:
sudo fsck /dev/sda5

See if it says it's clean or not.
Yep, it says it's lean.

Also did a chkdsk /f in Windows. I was just away for half a minute and it was already rebooting on it's own when I came back, but as far as I know there were no errors.

So what do you think. Should I try a clean install of Xubuntu 12.04, or do you think there's still a possibility to recover or update my previous install? I don't know how the upgrader woks, if it still an see the previous install if lilo is in the way or something like that. I just have no clue how it all works and what an be tried...

---

### Post by darkod on 2012-05-06
I really have no more ideas about recovering the existing xubuntu.

If you decide for a clean install, don't worry about the lilo mbr. It will be overwritten with grub2 on the MBR anyway. Simply do your install using the same partitions and select to put the bootloader on /dev/sda. That's it.

If you don't use the manual partitioning, don't forget that by default the auto methods won't install over your xubuntu. It's better to delete the partitions first. In fact, that might be a better idea since we are not sure if there is anything messed up with the linux partitions right now.

Just delete both linux and linux swap, and then the extended. Then install into that space either with the auto methods, or manually.

---

### Post by n0c0d3 on 2012-05-06
Well darkod, I just installed the new Xubuntu next to Windows. I deleted all Linux related partitions, decreased the win-partition in size (which was my initial plan!), then did another chkdsk /f on c:, everything seemed okay and installed Xubuntu. Everything seems to be up and running again even windows still boots flawlessly :)

Now I'm going to to have to spend a lot of my free time to get Xubuntu a bit like I had it over the next weeks. But that's all in the game I suppose, but fortunately I have much of my stuff backed up.

So I suppose this thread ends here. I've started to grow attached to it, but I promise I won't cry ;) 

So I wish to say thanks to you, oldfred and others who have been trying to help me out the past week. I really appreciate it and without you I'd have lost Windows as well. I'm going to mark this thread solved.


Thanks guys! 

Bart

Btw, I just see this thread had over 1000 views! It must be a good feeling to see other people suffering :)

---

