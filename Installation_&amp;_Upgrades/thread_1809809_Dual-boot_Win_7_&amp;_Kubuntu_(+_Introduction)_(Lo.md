---
title: "Dual-boot Win 7 &amp; Kubuntu (+ Introduction) (Long Post)"
date: 2011-07-22
forum: Installation &amp; Upgrades
---

### Post by gigenieks on 2011-07-22
Hi all!!

I'm very excited to _really_ begin my journey in Linux world!
I just like open-source philosophy. [Why is it free]("http://www.ubuntu.com/ubuntu/why-is-it-free")
> 
It’s open source.
Our global community is made up of thousands of people who want to help build the best open-source operating system in the world. They share their time and skills to make sure that Ubuntu keeps getting better and better. 

Just wonderfull.


[SIZE="4"][CENTER][COLOR="Teal"]**Introduction**[/COLOR][/CENTER][/SIZE]
About week ago I started to think how exactly will I configure my PC system (which PC to use of two availabe & which Ubuntu flavour to use) before my studies in university starts.

Anyway I was collecting info in word document and my father's friend sit down with me and asked me some questions. 

Forward 2 days and he have installed Ubuntu 11.04 on his laptop. Very excited (had no problems, hehe) and everything is faster than used in Windows.

Now my father wants too to have Ubuntu. I thought:
"hmm.. his friend have Ubuntu 11.04, so why not to install Kubuntu to my father's PC and as for myself I will use Xubuntu (have quite old computer :( )." 
In that way I can explore all 3 flavors.



[CENTER][SIZE="4"][COLOR="DarkGreen"]**Father's Dual-boot setup**[/COLOR][/SIZE][/CENTER]

Why I'm not just installing Kubuntu over Win7 someone could ask?

Answers:
1. I need to lear these thing because I will study with september Information Technologies (spelling?). In my opinion, I should know how to do these things. 

2. If I'm not around and there is only Kubuntu (no used Windows) and something happens (error etc.) my family could easy just reboot in Windows and do that (while I'm figuring how to fix the issue..)


OK now some -->

[SIZE="3"]**_[COLOR="DarkRed"]technical specification[/COLOR]_**[/SIZE]

[LIST]
[*]**CPU** - [64bit] Intel Pentium D 820 2.8GHz 
[*]**RAM** - 2 x 512MB DDR2
[*]**Video Card** - ATI Radeon HD 2600XT 256MB (supports 1080p video playback) *(Googled this card is equivalent to GeForce 8600GT)*
[*]**HDD's** - 1 x Samsung SATA2 80GB 7200rpm *+ 2 x IDE (80 + 250GB)*
[*]**MB** - MSI MS-7275
[*]**Audio** - Realtek ALC880
[/LIST]

Some links about main hardware pieces:
[LIST]
[*][Intel Pentium D]("http://ark.intel.com/products/27512/Intel-Pentium-D-Processor-820-(2M-Cache-2_80-GHz-800-MHz-FSB)")
[*][ATI Radeon HD 2600 series overview]("http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-2000/hd-2600/Pages/ati-radeon-hd-2600-overview.aspx")
[*][My Motherboards manual (pdf)]("http://uk.ts.fujitsu.com/rl/servicesupport/techsupport/Boards/Motherboards/MSI/ms7275/Man_MS-7275_uk.pdf")
[/LIST]



Next thing that I searched in these forums was "32bit vs 64bit".
And I concluded this:
[In Ubuntu documentation:]("https://help.ubuntu.com/community/32bit_and_64bit")
> 
Whilst your processor probably already supports 64-bits, in order _to benefit_ from it you need a 64-bit operating system.

Unless you have specific reasons to choose 32-bit, [COLOR="DarkRed"]**we recommend 64-bit to utilize the full capacity of your hardware**[/COLOR].


[SIZE="3"][CENTER]Ubuntu Forums some good posts[/CENTER][/SIZE]

[32 or 64 bit Ubuntu 11.04, which one?]("http://ubuntuforums.org/showthread.php?t=1741951")

> **3Miro said:**
> 
My rule is, if you have [COLOR="Blue"]**at least 2GB of RAM**[/COLOR] and you don't run into any issues with drivers and flash, then use 64-bit. 
Otherwise, go for 32-bit.

> 
The advantage of 64-bit is that it [COLOR="DarkGreen"]**"generally" runs and loads faster**[/COLOR] and is backward-compatible with 32-bit programs, not vice-versa. 

The disadvantage is that it typically eats up a little more RAM to accomplish this.

But if you had plenty of un-utilized RAM in 32-bit, then 64-bit will be faster, [COLOR="Blue"]**even with only 1GB on RAM**[/COLOR]. 



[32-bit or 64-bit for my Netbook (2GB of RAM)?]("http://ubuntuforums.org/showthread.php?t=1741684")

[QUOTE=3Miro]
[COLOR="Blue"]**2GB is the minimum**[/COLOR] in my opinion for you **to not notice** the extra RAM usage [COLOR="DarkRed"]**and gain some speedup from the CPU**[/COLOR].
[/QUOTE]
[QUOTE=Paqman]
[COLOR="Sienna"]**If your machine is capable of running 64-bit then use it.**[/COLOR] 

[COLOR="Blue"]**2GB of RAM is plenty for Ubuntu**[/COLOR], the marginally larger memory footprint of 64-bit won't be noticed at all.
[/QUOTE]
[QUOTE=oldos2er]
[COLOR="Blue"]**64-bit works great with 2GB RAM.**[/COLOR]
[/QUOTE]


[What if 32bit system is installed on 64 bit machine?]("http://ubuntuforums.org/showthread.php?t=1676315")

> 
32 vs 64bit determines how much data the CPU can handle from RAM.

64bit operating systems can **[COLOR="DarkGreen"]perform some tasks quicker[/COLOR]**, if the program was compiled in 64bit--which often isn't the case. 

[QUOTE=cascade9]
[COLOR="Sienna"]**If people have a 64bit capapble CPU, why give away the speed increase of 64bit?**[/COLOR]

If you are one of those unlucky people with something that wont run on 64bit (VERY rare now) I can understand it, but for most people 64bit is a better way to go IMO.
[/QUOTE]


[32 vs 64bits?]("http://ubuntuforums.org/showthread.php?t=1729465")
[QUOTE=3rdalbum]
But really, these are very weak reasons to recommend 32-bit over 64-bit. 

[COLOR="Sienna"]**If you have a 64-bit capable computer, then just use 64-bit.**[/COLOR]
[/QUOTE]
[QUOTE=NightwishFan]
[COLOR="Sienna"]**I say if you have a 64-bit processor use a 64-bit OS.**[/COLOR] 
[/QUOTE]
[QUOTE=NightwishFan]
If you have [COLOR="Blue"]**under 1GB I would not use 64-bit**[/COLOR] unless you plan on using a lightweight desktop.

The rule of thumb is, if you have free RAM you have enough ram though.
[/QUOTE]


[Should I change to 64-bit Ubuntu?]("http://ubuntuforums.org/showthread.php?t=1790527")

[QUOTE=sanderd17]
If you have more than 3GB of RAM, 64-bit has a real advantage. 
If you have [COLOR="Blue"]**3GB or less**[/COLOR], [COLOR="DarkGreen"]**64-bit has a very slight (not noticeable) advantage.**[/COLOR]
[/QUOTE]
[QUOTE=Paqman]
„Is there a real advantage to using 64-bit Ubuntu?”
Yes, any computationally intensive tasks will run significantly faster. Everything else will run at the same speed as 32-bit, [COLOR="DarkGreen"]**or marginally faster.**[/COLOR]

[COLOR="Sienna"]**If you've got a 64-bit machine, use 64-bit.**[/COLOR]

Having said that, [COLOR="DarkGreen"]**the difference is not big**[/COLOR]. 
You could use either and it wouldn't make much difference if you're not doing any video re-encoding or the like. 
[COLOR="Sienna"]**But why throttle the machine down if it's capable of more?**[/COLOR]
[/QUOTE]


[32 or 64-bit version?]("http://ubuntuforums.org/showthread.php?t=1806450&highlight=64bit")

[QUOTE=ikt]
A few years ago it was a pain to make some commonly used programs (flash and java to name a few) work in the 64 bit version. Nowadays these types of problems are more and more rare and the workaround for them are easier to find.

I would base your decision on how much RAM your system has.

If you have [COLOR="blue"]**more than 4 GB of RAM**[/COLOR], I would choose the 64 bit version so that you can fully utilize your ram. [COLOR="DarkGreen"]**Otherwise, the performance differences between the two are negligible for the normal user **[/COLOR]
(as long as you are not an engineer using an expensive CAD or rendering program, etc.) 
and you could use the 32 bit version without ever noticing a difference.
[/QUOTE]
[QUOTE=ikt]
[COLOR="Sienna"]**if your cpu supports 64 bit then use it!**[/COLOR]
[/QUOTE]
[QUOTE=uRock]
I have [COLOR="Blue"]**2 GB RAM**[/COLOR] and I use the 64bit Ubuntu without any issues. It is fast and makes me smile.
[/QUOTE]
> 
The 64-bit version [COLOR="DarkGreen"]**will run slightly faster for some applications**[/COLOR] and will probably allow you to use slightly more of your memory.

[QUOTE=wolfen69]
RAM is there to be used, not saved for a rainy day. I think it's funny that people get computers with 4gb+ of memory, then try and use as little as possible. <scratches head>
[/QUOTE]


[What are the advantages of 64 bit OS?]("http://ubuntuforums.org/showthread.php?t=1802919&page=2")

[QUOTE=wolfen69]
I find 64bit [COLOR="DarkGreen"]**to be slightly faster**[/COLOR] and more memory efficient. 
[COLOR="Sienna"]**If I have a 64bit cpu, I use a 64bit OS.**[/COLOR] [COLOR="Blue"](provided I have enough memory)[/COLOR]
[/QUOTE]
[QUOTE=Autor]
My system has a 2 gb memory.
[/QUOTE]
> 
More than plenty in fact, for me, i cannot install a 32 bit OS knowing my cpu supports 64. So no 64 bit version = no install


[COLOR="DarkRed"]**_I concluded 3 things:_**[/COLOR]
[LIST=1]
[*]If you have 64bit CPU, you should use 64bit OS to utilize full power of your processor. [COLOR="Sienna"]**(see sienna color)**[/COLOR]
[*]64bit OS "generally" is slight faster (not really noticable) [COLOR="DarkGreen"]**(see dark green color)**[/COLOR]
[*]RAM [COLOR="Blue"]**(see blue color)**[/COLOR]:
[LIST]
[*]1GB - minimum (?)
[*]2GB - excellent for "average user"
[*]3GB or more - only good if you use computing demanding task (for example video / photo editing) othervise it is "mostly unused RAM")
[/LIST]
[/LIST]

My main concerns is about RAM. In 2 aspects:
[LIST=1]
[*]In my opinion it is this PC's bottleneck (compare to CPU & Video Card)
[*]1GB probably is not enough (+512 / 1024MB should give like excellent performance from hardware capabilites standpoint)
[/LIST]

When I booted from Live CD Kubuntu used like ~400-450MB of RAM. (though I should mention this)

BUT there is 1 problem:
in this motherboard is only 2 slots for RAM and they both ar occupied with 512MB sticks. No more place.
So if we are going to get 2GB those 2 x 512 would need to sell and buy 2 x 1GB RAM. Some $ expenses. (however he mentioned something about buying 1gb RAM (just 1 not 2)

I guess my question is, how much performance would we gain if we compare 1 - 1.5 - 2 GB of RAM?
[COLOR="Navy"]**What do you advise in RAM matter?**[/COLOR]


[SIZE="4"]**[CENTER]Pre-Installation[/CENTER]**[/SIZE]


[CENTER][SIZE="3"]**Step 1**[/SIZE][/CENTER] [check Hardware Compatibility]("https://help.ubuntu.com/10.04/switching/C/preparing-hardware.html")
> 
_The easiest way_ to check whether your hardware is compatible with Ubuntu is to make use of the Ubuntu Desktop CD, described in the section called “Trying-out Ubuntu”. 

So I burned Live CD image and tried it. Everything seemed fine. Printer was recognised (HP Deskjet). Could access internet. KDE interface was smooth with effects (compiz, cube..).

**By the way, didn't Kubuntu supposed to offer driver for ATI video card?** (propriety or something else?)

Forget to test audio & video... will later.


[CENTER][SIZE="3"]**Step 2**[/SIZE][/CENTER][Organize Files]("https://help.ubuntu.com/10.04/switching/C/preparing-organizing-files.html")

About Hard drives:
[LIST]
[*]SATA2 80GB (7200rpm) -- 1 partion (Win 7)
[*]IDE 80GB -- 1 partion
[*]IDE 250GB -- 1 partion
[/LIST]

So I removed or moved unnecessary files etc. Now I there is free 56GB. I want Kubuntu to use those 50GB.

[Preparing to install]("https://help.ubuntu.com/10.04/switching/C/first-steps.html")

[Partitioning your disks]("https://help.ubuntu.com/10.04/switching/C/installing-partitioning.html")
> 
There are a couple of extra steps involved partitioning for dual boot.

[LIST=1]
[*]**Resizing existing the Windows partition.**
[*]Creating the swap partition.
[*]Creating the root partition.
[/LIST]

[Kubuntu Guide!]("http://www.kubuntuguide.info/index.php/Natty")
> 
A default Windows installation usually occupies the **entire hard drive**, so the main Windows partition needs to be shrunk, creating free space for the Ubuntu partitions. 

After shrinking a Windows partition, you should reboot once into Windows prior to installing Ubuntu or further manipulating the partitions. 

This allows the Windows system to automatically rescan the newly-resized partition (using chkdsk in XP or other utilities in more recent versions of Windows) and write changes to its own bootup files. 
(If you forget to do this, you may later have to repair the Windows partition bootup files manually using the Windows Recovery Console.)


**Using Shrink Volume on Vista and Windows 7**

> 
**Make sure you heed the warnings that** you should change the size of Windows Vista and Windows 7 partitions from within Windows only (using Settings -> Control Panel -> Administrative Tools -> Computer Management -> Storage -> Disk Management -> Shrink Volume), or using specific Windows tools made exclusively for this purpose.

Unlike Windows XP (and earlier Windows versions), Vista and Windows 7 does not allow you to move the MFT (Master File Table) that controls the NTFS file structure.

Inexplicably, Microsoft locates this near the middle (or end) of the partition, somewhat limiting the ability to resize (shrink) the partition completely. 

You will be able to gain some hard drive from the "Shrink Volume" command (under Settings -> Control Panel -> Administrative Tools -> Computer Management -> Storage -> Disk Management), but not all of of the hard drive.

I knew of no partition software that could move the MFT to a different place on the hard drive safely, but this tutorial suggested that Perfect Disk worked for this purpose.


So, yes Win 7 is installed on SATA HDD and has 1 partion (using entire hard drive) --> I need to resize partion.

They recommend to use Win 7 built-in Disc Management. Tried defregmentation did help to gain some space, but not enough.

So I tried Perfect Disc program ([according to this tutorial]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")) and I am stuck (I couldnt get more than 37GB.

Why?
I didnt have some unmovable MFT files, instead I got metadata (files?)
Anyway see pictures in attachments!

Weird because Perfect Disc should move those metadata in midle of partion!
[Boot time defrag and system files]("http://blog.raxco.com/blog/all-things-perfectdisk-and-defrag/boot-time-defrag-and-system-files")
> 
One way PerfectDisk stands out is its _ability to defragment all system files_ ([COLOR="DarkRed"]**including all NTFS metadata**[/COLOR]). 
System files is the designation that PerfectDisk uses to identify important files that the operating system uses at runtime to operate your PC. 

Depending on whether or not the drive is a system drive, or some other drive that PerfectDisk can’t lock, **offline file defragmentation** may or may not run on the drive(s). 
As long as PerfectDisk can lock a drive for exclusive access at runtime, it will defragment system files immediately.


Tried few times off-line defregmentation. Nothing changed.
Tried all 3 types of defregmentation:
[LIST]
[*]SMARTPlacement
[*]Consolidate Free Space
[*]Defrag only
[/LIST]
In all kinds of sequence. Nothing! There is just some metadata files in middle of partion and I dont know how to move them...
I am confused.

**[COLOR="DarkRed"]So, guys, how can I fix this?[/COLOR]**
Any ideas?
(there MUST be a way!)


And I'm not only with this issue: 

[NTFS Metadata - it's part of your drive]("http://perfectdiskblog.typepad.com/perfectdisk_blog/2007/01/ntfs_metadata_i.html")
Comment:

> 
Well, PerfectDisk 11 **does not defrag the NTFS metadata for me**. Even though the target disk is offline. 

Specifically, the $bitmap and the $logfile are left in the middle of the disk...


As well as here: [Working Around Windows Vista’s "Shrink Volume" Inadequacy Problems]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")
[QUOTE=sumit singh]
METADATA- 30% ( poor), with 134 excess fragments.. which perfect disk is not able to defragment.

In the drive map of “ C “ I can see that **there are ‘ excluded” sections in the middle** and at the end of the drive
[/QUOTE]
[QUOTE=srini]
Tried the whole deal exactly as specified in this article, including the use of PerfectDisk. 

**One metadata file just refuses to move, which is causing the shrink volume to continue to utilize less than half of the free space.**

Anyone know how to move metadata files? I tried doing it offline, reboot, etc.
[/QUOTE]
[QUOTE=IKO]
Even following the procedure and using Perfect Disk on and offline there was always that **unmovable metadata file in the middle of my partition.**
[/QUOTE]
> 
**A block of Metadata could not been moved by PerfectDisk.** MFT was not initially in the way.




Last question - this post is getting really long (=hard to read :( ) -

Is it possible to install 2 interface languages (English & Latvian).
That is, if I'm not near and family needs help, much more usefull would be to have english not Latvian lol. 


So, is it possible? 
And is there an easy way to change interface language? Like before Log in.
(If need I can rephrase last question ;) )

---

### Post by mastablasta on 2011-07-22
RAM usage and needs depend on what you are doing with maschine. if you plan to use virtualisation you need more ram. also it depends on your graphcis card. if graphics card is good then less ram can also do but generally the more the better.
 
i use 1.3GB on Kubuntu and plenty effects turned on. haven't noticed any issues or lack of RAM so far.

---

### Post by gigenieks on 2011-07-23
Okey lets continue -->

[Unable to resize partition for dual boot]("http://ubuntuforums.org/showthread.php?t=1799530")
[QUOTE="oldfred]
Do you have good windows backup? And a windows repairCD. You will need to have a repair CD or liveCd for every system you install.

Windows 7 repair USB
[http://www.intowindows.com/how-to-re...tion-dvd-disc/](http://www.intowindows.com/how-to-re...tion-dvd-disc/)
[/QUOTE]

Using above link I did make successfully bootable USB flash, but here what happens -->
[[IMG]http://i1200.photobucket.com/albums/bb335/cleverman89/Win%207%20USB%20repair%20issue/th_IMAG0094.jpg[/IMG]](http://s1200.photobucket.com/albums/bb335/cleverman89/Win%207%20USB%20repair%20issue/?action=view&current=IMAG0094.jpg)

It doesn't show my Windows 7 partion (which is on SATA hard drive)!

[[IMG]http://i1200.photobucket.com/albums/bb335/cleverman89/Win%207%20USB%20repair%20issue/th_IMAG0095.jpg[/IMG]](http://s1200.photobucket.com/albums/bb335/cleverman89/Win%207%20USB%20repair%20issue/?action=view&current=IMAG0095.jpg)
[[IMG]http://i1200.photobucket.com/albums/bb335/cleverman89/Win%207%20USB%20repair%20issue/th_IMAG0096.jpg[/IMG]](http://s1200.photobucket.com/albums/bb335/cleverman89/Win%207%20USB%20repair%20issue/?action=view&current=IMAG0096.jpg)
[[IMG]http://i1200.photobucket.com/albums/bb335/cleverman89/Win%207%20USB%20repair%20issue/th_IMAG0097.jpg[/IMG]](http://s1200.photobucket.com/albums/bb335/cleverman89/Win%207%20USB%20repair%20issue/?action=view&current=IMAG0097.jpg)
[[IMG]http://i1200.photobucket.com/albums/bb335/cleverman89/Win%207%20USB%20repair%20issue/th_IMAG0098.jpg[/IMG]](http://s1200.photobucket.com/albums/bb335/cleverman89/Win%207%20USB%20repair%20issue/?action=view&current=IMAG0098.jpg)


How can I fix this? Are those SATA drivers in some of those folders or I need to get SATA drivers elsewhere?


Second issue kinda unrelated - BIOS & hardware -:

[[IMG]http://i1200.photobucket.com/albums/bb335/cleverman89/Win%207%20USB%20repair%20issue/th_IMAG0101.jpg[/IMG]](http://s1200.photobucket.com/albums/bb335/cleverman89/Win%207%20USB%20repair%20issue/?action=view&current=IMAG0101.jpg)
[[IMG]http://i1200.photobucket.com/albums/bb335/cleverman89/Win%207%20USB%20repair%20issue/th_IMAG0100.jpg[/IMG]](http://s1200.photobucket.com/albums/bb335/cleverman89/Win%207%20USB%20repair%20issue/?action=view&current=IMAG0100.jpg)

Is it normal to have empy screen of Advanced Chipset Features in BIOS?

---

### Post by Mark Phelps on 2011-07-23
So, WHAT is your post really about?  

If you're trying to get detailed help for Win7, you should really be going to a Win7 forum.  Recommend sevenforums.com -- as they have forum sections and tutorials that deal with installation and repair issues.

One of your screen shots showed it asking for drivers.  The Repair CD does not contain drivers; instead, it only contains the minimal files needed to regenerate the Win7 boot loader files.  It expects to see a Win7 INSTALL DVD for drivers (or, driver CD).  A Repair CD can NOT be used to install or reinstall Win7.

As to System Restore, why select that if not needed?  All it does is replace the current version of OS files with older files.  If Win7 is working OK, this will do you no good.

As to  32-vs 64-bit, with only 1GB of memory, 64-bit is going to do you no good.  Recommend 32-bit, even if you upgrade to 2GB of memory.

---

### Post by gigenieks on 2011-07-23
> **Mark Phelps]
So, WHAT is your post really about?
[/QUOTE]
Hmm.. 
First, it is an _introduction_ of myself to Ubuntu Forums community.

Secondly, I want to be sure, that everything goes **smooth** - without unnecessary problems! (Everything = making dual-boot system said:**
> I have issue with Windows. I can't load it.[/COLOR]
First thought was "something is wrong with Windows NTFS filesystem; need to do CHKDSK from Recovery"

So, I inserted my USB W7 repair flash. 
Btw your post **helped a lot**

[QUOTE=Marke Phelps]
The Repair CD does not contain drivers; instead, it only contains the minimal files needed to regenerate the Win7 boot loader files.

Here is the wierd thing --->

I tried that USB before I installed Kubuntu. And somehow it "saw" Windows :shock: I could do everything I wanted:
[LIST]
[*]Startup repair
[*]System restore
[*]cmd
[*]etc
[/LIST]

I noticed also this: in some mysterious way (even when USB was not inserted to computer) when I had some issue with my Windows (for example, suddenly lost power in house); precisely startup, Windows presented[this screen]("http://www.checkcomputersetup.com/files/windows_7/repair_windows_7_launch_startup/failed_start_windows_7_black screen.PNG")

I would do "Launch startup repair" and it would fix things. But now it was working the way it used.. It was working _like I was booting from my USB flash_.
Really wierd...
[COLOR="Purple"]Can someone explain?[/COLOR] :confused:

Instead I got this:

[[IMG]http://i1200.photobucket.com/albums/bb335/cleverman89/Win%207%20USB%20repair%20issue/th_IMAG0094.jpg[/IMG]](http://s1200.photobucket.com/albums/bb335/cleverman89/Win%207%20USB%20repair%20issue/?action=view&current=IMAG0094.jpg)

Grrr... ](*,)
Rebooted. 
**What now?**

"Ahh.. lets try _Safe Mode_ - it loaded! Nice! So, I tried to load in "normal" mode. 
Get to this:
[IMG]http://newverhost.com/wordpress/wp-content/uploads/2009/06/windows7_beta_boot_screen.png[/IMG]

and it _restarted_ == BSOD.  F8 > "Disable automatic restart on system failure"  Enter.
When I tried again to load in "normal" mode. It got blue screen.. If I remember correctly they were _suggesting_ to do **chkdsk**
(thats why I got USB repair flash in the first place!! It just doesn't work)

Btw error code is 
```
0x0000007B
```
Haven't googled it yet.

My guess is that this all could be fixed if I could do --->
CHKDSK /R /F
It would check Windows NTFS filesystem and fix errors etc...
But I can't! :!:

As far as I know I have 3 options --->

[LIST=1]
[*]download SATA drivers and copy them to USB flash. (but my motherboard is quite old and don't (or I can't find) have any support page where I could download SATA drivers
[*]Make bootable USB Win 7 installation (with Recovery utilities) in Kubuntu with Kubuntu tools
[*]Do something similar to "chkdsk" in Kubuntu (maybe will fix)
[/LIST]

I think that 3. option probably wouldn't fix issue (because it is not Windows tool as is chkdsk) would like to do 1. but **can't** find MB support page or chipset of my mb), as for 2. it is probably the best solution - [COLOR="Navy"]**but how I do this (make bootable Win7 installation on USB) in Kubuntu??**[/COLOR] :confused:

If need more info just ask.
Need to fix windows!

---

