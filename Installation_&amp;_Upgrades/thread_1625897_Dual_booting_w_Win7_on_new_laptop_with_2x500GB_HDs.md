---
title: "Dual booting w/ Win7 on new laptop with 2x500GB HDs..."
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by sound of silver on 2010-11-19
Hello,

I've heard a lot of good things about Linux and Ubuntu from my college instructors, and I really want to give it a shot.

I just purchased a new laptop with two 500GB hard drives (there's actually like 465 GB available per drive).  I installed Windows 7 on the first drive last night.  There's currently 1 small System partition (200 MB) and the Win7 partition (465ish GB).  The second drive is completely unallocated.

I want to be able to dual boot Win7 and Ubuntu, but I'm just not sure of the best way to go about it.  I was thinking I could install Ubuntu in a partition on the first drive immediately after Win7, and use the second drive for Apps (probably mostly games) and Data (which could ideally be shared between Win7 and Ubuntu).

Or, I could leave Windows 7 alone on the first drive (and add apps to the OS partition), and install Ubuntu in a partition on the second drive, with a second partition for shared data.

I'm sure there's a million other possible schemes, and I'm hoping you all might have some advice or input.  I'm not particularly computer savvy (last night was the first time I've actually installed an OS - Win7 - believe it or not), and so I'm just not sure what is the best way to proceed.  

I should note that I already burned the Ubuntu 10.10 64 bit LiveCD.

I would really appreciate any help or input or advice!  Looking forward to trying out Ubuntu.

EDIT:

Some system specs, in case they affect the partitions you would recommend I use...

Pentium i7 740QM
Nvidia GTX 460M
8 GB RAM

---

### Post by sikander3786 on 2010-11-19
Hi. Welcome to Ubuntu and Forums :-)

The first thing I would suggest is to boot the Live CD and Try it without making any changes to your computer. Test all your hardware and know what you'll have after installation.

If you can afford to install your apps/games on the C: drive itself, I would suggest you to leave them there and create an extra shared partition (NTFS) to share data between Ubuntu and Windows.

Ubutnu basically needs at least 2 partitions.

1. / Ubuntu Root partition. Filesystem ext3/ext4, Mount Point /. Recommended size > 10 GB.

2. Swap partition. Recommend size = RAM X 2.

You can add a separate /home partition to hold all your settings/config if you ever need to reinstall Ubuntu.

x. /home. Filesystem ext3/ext4, Mount Point /home. Size unlimited.

But as you are going to create a shared data partition, you won't need to store your files in the /home directory and therefore 5 GB space will be more than enough.

It would be better to boot into your Ubuntu Live CD, do some testing and also post the output of this command from Applications > Accessories > Terminal.

```
sudo fdisk -lu
```

That will give us a better idea of your current partition setup.

And it is also worth mentioning that you can boot Ubuntu from a logical partition. Primary partition is not necessary as the case with Windows.

And regarding dual boot, if everything goes well, Ubuntu should pick up the Windows install automatically and add it to the Grub menu.

---

### Post by Quackers on 2010-11-19
Firstly I would boot from the Ubuntu Live cd and select "try ubuntu" rather than installing right away. That way you can make sure that all of your hardware works ok (ie graphics card, wireless card etc). When you are sure everything works you can then decide how to install.
My suggestion would be to shrink the W7 system (using Windows Disk Management) and leave the resulting space as unallocated. Then during installationI would choose the manual partitioning option and make a 12GB root (/) partition, a swap partition slightly larger than the amount of ram on the system (if you want to use hibernation) and then make a third partition with a /Home mount point for all your personal settings and files, which could use the remaining disc space.
This would leave your second hard drive clean for other purposes.

---

### Post by sound of silver on 2010-11-19
Thanks so much for the quick, informative replies!

I'm posting this from within Ubuntu, booted from the LiveCD.  Everything seems to be working well, although the screen resolution is capped at 800x600.  (I assume a Linux-version graphics card driver would remedy that.)

Anyway, here are the results of the command sikander asked me to run:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe0c5913d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   976771071   488282112    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbbc58b91

   Device Boot      Start         End      Blocks   Id  System
```

I definitely have an abundance of hard drive space.  However, at the moment I probably won't need too much space for Ubuntu - next term, I have a software development class in a Linux environment in which we'll run Ubuntu, but generally I think I would continue to use Windows for games, word processing and Visual Studio.  If Ubuntu is as good as everyone says it is, I'm sure I'll be looking for ways to get rid of Windows, but I imagine the transition will be gradual.

From what Quackers wrote, I'm now leaning toward installing both Win7 and Ubuntu on the first drive...

Would you recommend having a partition for shared data, or separate partitions for each OS?  

When I'm installing Ubuntu, does the installation create all the necessary partitions - swap, root, home - or do I need to do it manually during the installation process?  In what partition are applications/data/etc. installed?

EDIT:

Also, from what sikander is saying, my root partition should be ~10GB, and my swap should be ~16GB, given that I have 8GB RAM?

---

### Post by Quackers on 2010-11-19
I don't use shared data partitions, though many do, so I am unable to advise there.
16GB would be a HUGE swap partition!
With regard to graphics, and this could be important, if you go to the System menu and then Administration then Additional Drivers, it will tell you whether third party drivers are available for your graphics card. Try that and see if things improve.

---

### Post by sikander3786 on 2010-11-19
Yes 16GB Swap would be really Huge :-)

I'll say 4 GB swap will be more than enough. I myself am using 2 GB though and never got it used on my 3 GB RAM PC. However I don't hibernate it. And with your 8GB RAM, no question of needing a Swap partition unless you do something extra-ordinary ;-)

For hibernating, you definitely need swap. How much? I don't have a definite idea. 4 GB should be enough though.

As Quackers suggested, you can install both of the OS on any of your drives. On the Widows drive as well, by resizing it.

What are you planning to do? Are both the HDDs internal drives?

You'll have separate partitions for both OS definitely but those are install partitions. You definitely can have a shared data partition formatted NTFS to share the data between both of them. In fact, it is almost impossible to sync your data if you plan to place it separately in both the OS. I would recommend a shared data partition.

With installers prior to Ubuntu 10.10, you had a choice to choose the largest continuous free space (un-allocated space) and Ubuntu will do the rest for you. It'd create all the related partitions and set it up.

But with 10.10, this has changed a bit and you need to do some manual partitioning. In fact I have not used the 10.10 installer yet so am unable to advise on that. However manual partitioning scheme will be the same as in my post above.

---

### Post by oldfred on 2010-11-19
Each of us has different opinions on partitioning and it varies by how you use the system. Even my own "best" partitioning has changed as I have used Ubuntu more and windows less.

I prefer each drive having a system and each boot loader in the MBR of that drive. That way if ever a drive fails, you can change boot order in BIOS and boot the other. You still need good backups and liveCDs/USBs for repairs but it adds one more way to boot.

There also is another issue with win7. Some apps in win7 do not follow convention and use the same space as grub2. Grub2 is larger than the windows boot loader and needs a little more space to boot. When system does not boot everyone blames grub2 when it is really windows software. 

If you have grub2 on the second drive and windows on the first drive you will never see the conflict over boot drive space.

I only had / (root) and swap with a small NTFS shared partition for data like firefox profile & thunderbird profiles. Then whichever system I booted I had the same bookmarks & email. Now I have a large /data partition with most of my data in that, but I still have not moved my profiles from the NTFS partition. I am only in XP about an hour or two a week.

---

### Post by sound of silver on 2010-11-19
**Quackers**: I installed the recommended graphics driver, but it asked for a reboot, and when I rebooted it was as though I hadn't installed the driver.  I assume this is because I'm using the LiveCD.  I checked the Nvidia website, and there are 64-bit Linux drivers for my card, so I think I'll be okay when I install.

**sikander**:  So, I guess I'm not quite sure what is the purpose of each partition.  Correct me if I'm wrong:

/ is for the OS installation
/swap is for virtual memory
/home is for everything else - programs, data, etc.

If I've got it right, I'm thinking the best thing would be to have / and /swap as primary partitions, and /home as extended, and then I can divide it up later if I want to...

(By the way: this whole partition thing is new to me, just been reading lots of stuff online over the past few days, so correct me if I sound like I don't know what I'm talking about!)

Both of the hard drives are internal.  As for what I plan to do with the computer - well, up until now I've always used Windows, and so I don't even know what Ubuntu is capable of!  I'm in a software engineering program at college, and a few of my classmates and instructors are big Linux proponents, and so I'm excited to try it out.  Plus, I've got a Linux systems development course next term where we're working from within Ubuntu.

If I was just using Windows, I'd be working in Visual Studio, and playing games - just picked up Starcraft 2 - plus general purpose stuff like word processors and internet browsing.  I won't really be using the computer for any specialized purpose.

**oldfred:**  Thanks for the response!  I'm a total newbie... Let's see if I've got it right: 

From what I've read, grub is the software responsible for allowing you to boot into either Windows or Ubuntu?  If I install Ubuntu and grub2 to the second hard drive, grub will still "see" Windows and allow me to boot into either OS?  And by installing to the second HD, I'll avoid potential conflicts between the Windows bootloader and grub2?  

If this is the case, I will definitely install to the second internal HD...

Is your /data partition a separate partition from /home?  As you can see from my response to sikander, I'm still trying to work out the partitions that Linux needs and what can go in each one.  Is your /data partition essentially just a HD partition, formatted for ext4, where you keep data/apps?  (Equivalent to partitioning a drive for data in Windows?)

Thanks everyone for your help and patience so far!

---

### Post by Quackers on 2010-11-19
Your synopsis for the 3 Linux partitions is correct.
Linux will work on extended partitions, so primary's aren't required. That's a Windows thing.
Question
Does your laptop allow the choice of which hard drive to boot from? This could have a say in what is installed where.

---

### Post by sikander3786 on 2010-11-19
You'll not be able to test the graphics drivers from a Live CD. Nvidia cards are supported in Linux better than any other (ATI/Intel) and that should not be a problem. Yet make sure you install the drivers from Repositories i.e, System > Administration > Additional Drivers and not from the manufacturer website. (You'll avoid a few problems that way, get updates when they are available, won't need to install the drivers at every kernel upgrade and also it is simple)

/ is for the base OS install. Swap for virtual memory of course but /home is intended for personal files and application/program settings, not the programs themselves. They get installed to the / partition only.

You can have / as your only primary partition and both Swap and /home as a logical partition. You can go either way though. No problem.

Grub should see Windows from the other drive as well and list it for dual boot. During the installer, you'll get a choice for location of Grub on the bottom of manual partitioning page. Make sure you'r going to install it to the proper HDD.

Yes the /data partition is separate from /home as we mentioned earlier, it is formatted NTFS for access in both Ubuntu and Windows. And you can't have /home on an NTFS partition. That is the bottom-line.

**Oldfred** will surely enlighten you further regarding the last 2 queries.

---

### Post by Quackers on 2010-11-19
When I boot from the live cd it always shows an updated video driver as available. Can't you install that? I've never tried it. I feel cheated :-)

---

### Post by sound of silver on 2010-11-19
> **Quackers said:**
> Your synopsis for the 3 Linux partitions is correct.
Linux will work on extended partitions, so primary's aren't required. That's a Windows thing.
Question
Does your laptop allow the choice of which hard drive to boot from? This could have a say in what is installed where.

Yes, it does.  Currently I have the settings in BIOS changed to boot first from the CD drive.

**sikander**: Thank you for the clarification :)  Since programs themselves are generally saved in the / , would it make sense to make that a large partition?  In my Windows experience, I've found that applications take up quite a bit of space...

---

### Post by oldfred on 2010-11-19
I cannot disagree with anything. 

I did create a separate /home when I converted from just root & swap. But then decided I might want to try other systems or have separate partitions for new version(s) of Ubuntu so I moved all my data to /data. Then my /home became less than 1GB of mostly hidden files & folders that are the settings. I then decided just to keep /home as part of root, back it up and copy all or parts of it into each new install of Ubuntu if I wanted to.

If not sure you do not have to full use drive initially. I still have a little unallocated on my 640GB drive. You should create at least one or two primary partitions before using the extended to hold the logical partitions. Some system BIOS will only let you boot if a boot flag is on a primary partition. Grub does not use boot flag but windows does.

---

### Post by Quackers on 2010-11-19
Programs are only installed to the root (/) partition if no seperate /home partition is used - otherwise they will go in /home.
So, the choices are your own to make :-) Enjoy!

---

### Post by sikander3786 on 2010-11-19
> Since programs themselves are generally saved in the / , would it make sense to make that a large partition? In my Windows experience, I've found that applications take up quite a bit of space...

I have a 50 GB / partition for Ubuntu Maverick and this is what I am using with most of daily needed applications.

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              49G  3.9G   42G   9% /

```

So, I think 20 GB is more than enough for that. As you've plenty of space and want to be on the safer side, I'd just recommend 30 - 50 GB however I guess you'll not be able to fill that ever :-)

Unless you want to download all the software available in the Repositories, 30 GB is enough for all my needed software.

> When I boot from the live cd it always shows an updated video driver as available. Can't you install that? I've never tried it. I feel cheated

Yes you'r cheated :lolflag:

---

### Post by oldfred on 2010-11-19
I found this in my notes. You do not have to reboot but just restart to use nvidia drivers in the LiveCD. Never actually done it.

to test, install Nvidia driver while in the liveCD environment. Do not restart entire system but gdm.
press ctrl+alt+f1.
sudo service gdm restart

---

### Post by Quackers on 2010-11-19
Aha! Not cheated any more. Thank heavens for oldfred's notes :-)

---

### Post by oldfred on 2010-11-19
Oldfred screwed his notes up the other day (deleting link blew away folder with all my notes). Of course I was just about to do another backup, as I am one of those that is do as I say not as I do, and do not back up as often as I should.

A combination of testdisk, and tolling for posts by oldfred has recovered most of the missing data.:)

---

### Post by Quackers on 2010-11-19
Things will blow away where you are! 
Never happened to me that, never, honest :^o
Glad you got most of it back :-)

---

### Post by sound of silver on 2010-11-19
You guys have been amazing!  I can tell there's a really great community backing Ubuntu :D

I've decided on this partitioning scheme.  Let me know what you think.

Disk 1 (465 GB)

System: 100MB (Primary, NTFS)
C: 165 GB (Primary, NTFS, Win7+Apps)
D: 300 GB (Primary, NTFS, Data)

Disk 2 (465 GB)

/swap: 15 GB (Primary, ext4)
/: 30GB (Primary, ext4, Ubuntu+Apps)
/home: 120 GB (Logical, ext4, Data)
/data: 300 GB (Primary, NTFS, Data)

In this scheme I would use /data as a shared data partition.  Drive D on the first hard disk could function as temporary backup, or just remain empty in the case that I want to expand the Win7 partition.

The other question I have for you (and this is a Windows specific question so I would totally understand if you don't know the answer or if this isn't the right place to ask), but I was thinking of creating a Page File partition at the beginning of the second HD, before the swap partition, to hold the Windows paging file (how Windows handles virtual memory).  Would you recommend NOT putting such a partition on the drive with Ubuntu, or is it harmless?  (I would make either / or /swap a logical partition along with /home.)

---

### Post by Quackers on 2010-11-19
With 8GB of ram I wouldn't envisage a great need for a new page file. Windows will create a page file of whatever size it needs, normally.
Also, if you don't intend to use hibernation a swap file of 1GB will be plenty. If you do intend using hibernation I don't know what size to advise.

---

### Post by sound of silver on 2010-11-19
> **Quackers said:**
> With 8GB of ram I wouldn't envisage a great need for a new page file. Windows will create a page file of whatever size it needs, normally.
Also, if you don't intend to use hibernation a swap file of 1GB will be plenty. If you do intend using hibernation I don't know what size to advise.

You're right, I've just been doing so much reading over the past few days and I think I'm just making things more complicated for myself.  I think based on my usage a a separate page file partition is unnecessary.

By the way, I ran that command from the previous page and I'm now running in glorious 1920x1080!  Can't wait to get everything installed and set up.  

Would you guys recommend setting up partitions beforehand through Windows/Ubuntu LiveCD, or will I be able to do everything during the installation?

---

### Post by Quackers on 2010-11-19
If you need to resize, create any partitions on the Windows disc I would recommend you use the Windows Disk Management console (Start > right-click Computer and select Manage > Disk Management) as this is much quicker and safer than others. Also reboot after making changes to make sure Windows is still good.
If the second hard drive has partitions you can delete them and re-create them with the installer.
Also, be clear which disc you are in when changing partition structures. It is easy to change the wrong disc! Ask me how I know that :-)

---

### Post by sound of silver on 2010-11-19
> **Quackers said:**
> If you need to resize, create any partitions on the Windows disc I would recommend you use the Windows Disk Management console (Start > right-click Computer and select Manage > Disk Management) as this is much quicker and safer than others. Also reboot after making changes to make sure Windows is still good.
If the second hard drive has partitions you can delete them and re-create them with the installer.
Also, be clear which disc you are in when changing partition structures. It is easy to change the wrong disc! Ask me how I know that :-)

LOL, I can guess how you know :P

Well, wish me luck!  Heading back to Windows to set up my partitions, and then I'm gonna install!

I'll be back to tell you how it went down!

---

### Post by wilee-nilee on 2010-11-19
Awesome help here, the only thing I can see missing here is that grub must be pointed at the HD installed to, I may have missed it if mentioned.;)

Edit: as I looked closer this is mentioned; OP you know how to do this I assume, if not all the great help here will guide you if needed.

---

### Post by monticellifernando on 2010-11-19
Whow! I whish I had this help in 2001 when tryed to installa liux for the first time :-)

My humble contribution for sound of silver:

About partition and sizes:
- 30 GB for / is ok for Ubuntu since usually there is no need od download tons of source code to compile :-)
- A swap of twice the ram is I think the right choice for a laptop when you will use hibernation (at least once in a while)

- Proposal: If you are not planning to make any change maybe you can just make all four partitions primary. Otherwise, I'd rather put /data in an extended partition than /home, but this is just my instinct.
- If the disk is empty, I think it is easier to make the partitions when the ubuntu installer asks for it. You have to select "manual" or something like that. 

About resizing:
Why not using gparted (available in the ubuntu live cd)? I've been using it since 2005 with no problems at all with ntfs!. 

Good luck and welcome :-)

---

### Post by sound of silver on 2010-11-19
Thanks for all the input guys! 

I'm actually a little stumped at the moment, and I'm having a hard time finding info online...

I'm wondering where I should install the boot loader... It gives me the options of the first and second hard disks in the installation menu under manual partitioning.  Windows 7 is installed to the first hard disk, and Ubuntu will be installed to the second.

---

### Post by sound of silver on 2010-11-19
> **wilee-nilee said:**
> Awesome help here, the only thing I can see missing here is that grub must be pointed at the HD installed to, I may have missed it if mentioned.;)

Edit: as I looked closer this is mentioned; OP you know how to do this I assume, if not all the great help here will guide you if needed.


Actually, I think this is the issue currently stumping me!  Do you have any advice on how to handle this?  (See also my preceding post...)

---

### Post by wilee-nilee on 2010-11-19
> **sound of silver said:**
> Actually, I think this is the issue currently stumping me!  Do you have any advice on how to handle this?  (See also my preceding post...)

Easy to be stumped here that is why I mentioned it. You want grub to be installed to the master boot record of the HD your installing to. If your installing Maverick it is right on the same page as the install partitioning section. In earlier versions of Ubuntu grub placement is on the last screen of the install gui setup and is a advanced button.

So lets call your Ubuntu HD sdb here you would just point the grub at sdb, no numbers as these would be actual partitions, we just want it in the MBR.

The good thing here though is that even if you put grub in the windows HD MBR not the actual partitions this can be easily fixed. loading the mbr=first 512Mib of the HD is quite easy once you know the drill.;)

---

### Post by sound of silver on 2010-11-19
> **wilee-nilee said:**
> Easy to be stumped here that is why I mentioned it. You want grub to be installed to the master boot record of the HD your installing to. If your installing Maverick it is right on the same page as the install partitioning section. In earlier versions of Ubuntu grub placement is on the last screen of the install gui setup and is a advanced button.

So lets call your Ubuntu HD sdb here you would just point the grub at sdb, no numbers as these would be actual partitions, we just want it in the MBR.

The good thing here though is that even if you put grub in the windows HD MBR not the actual partitions this can be easily fixed. loading the mbr=first 512Mib of the HD is quite easy once you know the drill.;)

Thanks so much!  Really appreciate all the tips. 

My first HD is listed in the Ubuntu installation as sda.  This is the hard drive with Windows.  The second hard drive is sdb.  This will have Ubuntu.  So I'll install the boot loader (grub?) to sdb.

Ooookay, here I go!

---

### Post by wilee-nilee on 2010-11-19
> **sound of silver said:**
> Thanks so much!  Really appreciate all the tips. 

My first HD is listed in the Ubuntu installation as sda.  This is the hard drive with Windows.  The second hard drive is sdb.  This will have Ubuntu.  So I'll install the boot loader (grub?) to sdb.

Ooookay, here I go!

You will be okay I think, leaving me out; you have some of the best in this area, subscribed or at least commented in the thread.;)

---

### Post by Quackers on 2010-11-20
If you install grub to just sdb (as recommended) you will need to change the bios to boot the second hard drive before the first hard drive. Otherwise it will only boot Windows 7 direct. With the second hard drive booting first you will get the choice of OSes via the grub menu.

---

### Post by sound of silver on 2010-11-20
> **Quackers said:**
> If you install grub to just sdb (as recommended) you will need to change the bios to boot the second hard drive before the first hard drive. Otherwise it will only boot Windows 7 direct. With the second hard drive booting first you will get the choice of OSes via the grub menu.

Hmm.  I've got Ubuntu installed and both my hard drives are formatted correctly.  The GRUB and Ubuntu are installed on the second hard drive.  However, the computer boots right into Windows without the GRUB screen coming up.

I went into BIOS to change the boot priority, but I don't even see the second hard drive listed as an option...  It only gives me two options, and right now it boots first from the DVD ROM drive, then from the first hard drive.

Not sure how to fix that...

---

### Post by Quackers on 2010-11-20
That's why I asked you in post #9 if you had that option :-) My twin drive laptop is the same - no option to chose the second drive to boot from. The way I got around this is to install grub on sda as well.
Give me 5 minutes to remember how I did it :-)

---

### Post by sikander3786 on 2010-11-20
There should be a separate menu for Hard disk priority. Move your intended HDD top of the list there.

---

### Post by sound of silver on 2010-11-20
> **sikander3786 said:**
> There should be a separate menu for Hard disk priority. Move your intended HDD top of the list there.

Thanks, I actually just figured it out.  There was an option called Hard Drive BBS Priorities.  In that menu, both of my hard drives were listed, with my first HD as first priority and my second as second priority.  I switched the order, and went back to the previous menu.  Now, in the boot priority options, I have CD drive as first priority and the second hard drive as second priority.  The first drive is now off the list.  

I saved and exited BIOS.  the GRUB screen popped up, I loaded into Ubuntu, and here I am!

I'm gonna restart and load into Windows and make sure everything is working properly, and then I'm off to bed.  Thanks for everyone who contributed to this thread.  Definitely couldn't have done it without all this help.  Feels good to be a new member of this community :)

---

### Post by Quackers on 2010-11-20
If there is no option to boot the second drive please boot from the live cd and then go to the site below and download the boot script to your DESKTOP then open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will produce a results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Quackers on 2010-11-20
Ah ok, I see you've replied with good news :-) Very nice, enjoy!

---

### Post by sikander3786 on 2010-11-20
> 
I saved and exited BIOS. the GRUB screen popped up, I loaded into Ubuntu, and here I am!

Glad to hear you got there. You are Welcome for the compliments :-)

Just one question at the last, does your Grub menu list Windows and are you able to boot Windows successfully?

---

### Post by sound of silver on 2010-11-20
> **sikander3786 said:**
> Glad to hear you got there. You are Welcome for the compliments :-)

Just one question at the last, does your Grub menu list Windows and are you able to boot Windows successfully?

That's correct, everything seems to be working perfectly!

---

### Post by Quackers on 2010-11-20
We like happy endings :-)

---

### Post by sikander3786 on 2010-11-20
> **sound of silver said:**
> That's correct, everything seems to be working perfectly!
Glad to know.

Thanks to Quackers, Oldfred and wilee-nilee for all there comments and help :-)

You can mark this thread Solved using [COLOR="Red"]**Thread Tools**[/COLOR] near the top of this page.

Happy Ubuntu-ing! And Good Luck!

---

### Post by sound of silver on 2010-11-20
> **sikander3786 said:**
> Glad to know.

Thanks to Quackers, Oldfred and wilee-nilee for all there comments and help :-)

You can mark this thread Solved using [COLOR=Red]**Thread Tools**[/COLOR] near the top of this page.

Happy Ubuntu-ing! And Good Luck!

I have marked it solved.

Thanks again, and I'll see you around!

---

### Post by sound of silver on 2010-11-20
> **sikander3786 said:**
> Glad to know.

Thanks to Quackers, Oldfred and wilee-nilee for all there comments and help :smile:

You can mark this thread Solved using [COLOR=Red]**Thread Tools**[/COLOR] near the top of this page.

Happy Ubuntu-ing! And Good Luck!

I have marked it solved.

Thanks again, and I'll see you around!

---

### Post by 0_irishboy_0 on 2010-12-13
Hey everyone :)


I just felt the need to really complement everybody here in the ubuntu community.  I am a completely, totally new ubuntu user, and I was lucky enough to purchase a laptop with identical specs as the OP's.  Within a matter of 45 minutes I was able to have ubuntu completely up and running, something that certainly wouldn't have happened without this forum.


I ended up setting up my computer exactly as was recommended to the OP (1 Windows HD, 1 ubuntu, /, /swap, /home, and / data partitions, all primary.)I ended up setting up my computer exactly as was recommended to the OP  (1 Windows HD, 1 ubuntu, /, /swap, /home, and / data partitions, all  primary).  So far everything has been working flawlessly.  Some programs are a tad slow when loading, but I'm sure it's nothing I won't be able  to figure out.


I just wanted to thank everyone who contributed to this thread.  You have made me a satisfied 1st time ubuntu user :)

---

### Post by Quackers on 2010-12-13
You're welcome :-)
Just a side note. If you have /, /home, /data and swap partitions and they are all primary, you are at the limit on that disc for primary partitions! Don't create any more partitions on that disc without deleting a primary and replacing it with an extended partition :-)

---

