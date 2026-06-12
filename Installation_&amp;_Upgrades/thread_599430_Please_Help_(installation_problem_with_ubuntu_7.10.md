---
title: "Please Help (installation problem with ubuntu 7.10 and ubuntu 7.04)"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by mayur416 on 2007-11-01
I am a absolute new comer to the world of Linux:). Heard a lot about Ubuntu 7.10 and wanted to experience its magic..Downloaded it from a mirror ,burnt it to a cd and began to run.. The live cd part was running perfectly and when I tried to install it on to my hard disk ..the seven steps for installation work normally and during installation the system absolutely freezes:confused:( at 15% ...shows a message detecting file systems)...from then on no progress at all.. Even i tried to install Ubuntu 7.04 so that it can be upgraded to 7.10...But it also froze the system...

---

### Post by Pumalite on 2007-11-01
Try Alternate cd. Do md5sum on iso, burn at 4x. Post your specs. You might need a lighter Desktop.

---

### Post by mayur416 on 2007-11-01
Even checked the md5 sum it is perfect...Ubuntu 5.10 installed perfectly...But gotta a problem with 7.04 and 7.10


System configuration:

Compaq presario s4030 desktop;
40 gb ide hard drive;
intel pentium 4 processor 1.9 G Hz,
1gb+12b mb ram;
GeForce Nvidia 256 mb graphics card;
Sony DVD-R/RW;

---

### Post by mayur416 on 2007-11-01
I Downloaded it and burnt it at 4x speed... Even used a different mirror to download but the result was the same...Just Eager to use Ubuntu 7.10 ..please help me out:confused:

---

### Post by Pumalite on 2007-11-01
Your hardware is fine. But if you have troubles with the Live CD, then go with the Alternate one.

---

### Post by mayur416 on 2007-11-01
After failing to install Ubuntu 7.04 and 7.10 ...I tried my luck..just tried to install Fedora 7 but the outcome was same....A frozen system:confused:... Had a copy of Ubuntu 5.10...It installed in a whisker and absolutely no problem during the installation...It is running perfectl:)y

---

### Post by mayur416 on 2007-11-01
ok buddy will try to download an alternate cd... Will try to install it ...Hope to become one of the privileged user...:KS

---

### Post by mayur416 on 2007-11-01
Wanna desperately use Ubuntu 7.10...Please let me know if there might be any problem with my hardware...Or if there are any other methods of installation...

---

### Post by Harpoon on 2007-11-01
If you are failing at "detecting file sytems," it makes me wonder if (a) you have any extra devices - - like usb disks, mmc cards, and such plugged into the laptop.  If so, try to install after disconnecting everything you don't need; and (b) what, if anything, you have on that 40gb hard disk - - windows, .....  The latter should not cause problems, but then, again, neither should the former.  But one never knows.

Good luck (I am trying to help a friend with a whole different set of install issues without success for a couple of weeks already).  Hope your efforts bear fruit more quickly.

---

### Post by mayur416 on 2007-11-01
Even i was trying install Ubuntu7.10 from last one week..but dint succeed till now...Was booting through a live cd and using ubuntu 7.10...

---

### Post by mayur416 on 2007-11-01
Can a hardware in my system prevent me from installing Ubuntu7.10 ?I am not able to make out what the problem is and why am i not able to install Ubuntu?

---

### Post by Harpoon on 2007-11-01
I understand your situation, but are you trying with the laptop without stuff plugged in (especially anything that holds data), and what else do you have on the hard drive.  If, for example, you are setting it up to dual boot with windows, and you didn't shut down cleanly the last time you used it, all sorts of bad things can pop up.  If you do have windows, reboot into that, run checkdsk(?) and let it fix any errors.  Sometimes it takes two reboots into windows to clear this type of problem.

---

### Post by perixx on 2007-11-01
Right, 

the HDD might be damaged in some way... maybe also the master boot sector? You could try 'fixboot' and 'fixmbr' in your Windows recovery-boot-console after booting from the Win-CD - and run scandisk, as told before.

You might check your HDD with Gparted partition manager  from your live-CD before installing. If you can do without the old Windows-installation you could do: 

a) a complete re-partitioning with that tool, with 1 primary partition (boot-flagged) for your old 'new' Windows, 20gig (install first!) and 1 extended partition (say 20gig), that you'll want to place 2 'ext3'-partitions (/ partition (root) - 9gig and /home partiton (for your personal settings) - 10gig), plus 1 'swap' partition (1gig) into.

refer to this link for the /home partition
[http://ubuntuforums.org/showthread.php?t=575671](http://ubuntuforums.org/showthread.php?t=575671)


b) resize your current Windows partition 

****Note:**** I wrote this text below for some other forum post originally, but since that one was closed due to Trolling, I'll post it now - hopefully it's of help to you. You may find it a little extensive but helpful anyway:


*************************************************************

Well, I'm pretty new to Linux too - though I consider myself a rather expereienced Windows user. Since I'm a child of the DOS-age, I'm used to typing text commands and the likes and trying to think 'around the cornder' at times.

My experience with Linux so far: if you make it plain and easy, meaning a system with only Linux, you can't go wrong, setup's simply too simple :)

BUT: if you want to make special and tricky things, you'll have to perform special and tricky procedures at times. And that requires that you put some effort in digging up the necessary information by yourself and having some patience. 

I cannot speak for Vista-users, since that's a step M$ is gonna do without me :P It's just another (big) step away from basic self-determination rights, may it be more comfortable or not (though I'd suppose XP is better in this respect and in terms of performance -- btw., did you know that XP has support till 2014, longer than Vista? Should tell you everything. Maybe you better get that 'downgrade' from M$ ASAP, before it's too late - unless you really drool over DirectX 10 :-]


Anyway, in general, if you plan to make a dual-boot system, then it's always the best idea to have a clean setup of Windows first, BUT leaving enough space for the second OS on the HD!!! Otherwise you have the trouble of shrinking and tweaking your Windows partition first.
 
Besides, if you insist, BEFORE you do any shrinking:

1) disable the hibernation mode, 
2) turn off the prefetching and super prefetching in your registry, 
3) restart Windows and delete pagefile.sys and hiberfile.sys, if still there, 
4) defrag your partition (best with Windows' tool and 'pagedefrag' afterwards!!! 
This is needed, because Windows tends to spread it's data all over the HD (especially prefetching), thus making the space for resizing usually rather limited. Those are 'non-movable' data areas in your system that possibly cannot be moved by a resizing tool. If you don't believe it, look at the graphical bar in Windows' defragmentation tool. Also, Windows' virtual memory (about 1,5-2 times the size of your physical RAM) can be placed anywhere on your HD, AFAIK.
5) BACK UP YOUR PERSONAL DATA.

These are some reasons, why it's a LOT easier to have your HD partitioned BEFORE you install ANY OS.


 :-] :mrgreen: Still there? Ready? Good!

Well, if you STILL REALLY want to give Linux a try in a dual-boot setup, I suggest you do so by the steps below, but keep in mind, that every distro is maybe similar to others but unique - so there can't be any 'unified' setup procedure, with every point-and-click explained, for every distro has it's own GUI appearance!! So, from some point on, you'll have to start thinking 'out-of-the-box' and look around a bit. I have recreated most of the info below from my experience & memory -- so please add a little fuzzy logic ever so often :]



********************* START ***************************

1) BACK UP ALL YOUR PERSONAL DATA on your Vista Partition to a CD-ROM or memory stick and PRINT THIS GUIDE for your installation procedure. (!!!)

2) provided, that you've read their 'licence agreements', download: 
'BurnCDCC' -> 
[ftp://terabyteunlimited.com/burncdcc.zip](ftp://terabyteunlimited.com/burncdcc.zip) 
+ 
'Systemrescue CD' -> [http://downloads.sourceforge.net/systemrescuecd/systemrescuecd-x86-0.4.0.iso?modtime=1191443042&big_mirror=1](http://downloads.sourceforge.net/systemrescuecd/systemrescuecd-x86-0.4.0.iso?modtime=1191443042&big_mirror=1) 
+
your desired Linux-.ISO-image (e.g. Mint or Xubuntu) -> look at
[http://www.tuxfiles.org/linuxlinks/distro.html](http://www.tuxfiles.org/linuxlinks/distro.html) or
[http://www.linuxlinks.com/Distributions/Mini_Distributions/](http://www.linuxlinks.com/Distributions/Mini_Distributions/)
:^D - second's only a joke! 

----------------------------------------------------------------------------------------------------------------------
*****? ? ? ?*****
- 'BurnCDCC' is a simple-as-bread ISO-burning freeware that runs without installation (if THIS doesn't start in Wu$$ta, then you'll have to find another tool to burn your image yourself), 

- 'Systemresuce CD' is a Linux-Live CD with a lot of useful System-tools and very good hardware and filesystems-support; you'll only need 'Gparted' for re-partitioning your HD, though.

- You might like PuppyOS eventually... (I've used it for more than a year for surfing by now - includes the graphical partitioning too Gparted and has many cool Live-CD-features; can also be installed on HD; super-simple to use ('cos u're always ROOT, but many changes in appearance, look & feel ever so much)

- Or, of course, Ubuntu -> ('Mint' is based on Ubuntu and has superior multimedia support - maybe the one for you!!) *cough*

- Open Suse / Suse Linux is very sophisticated and maybe has the best hardware-vendor support but is too overstuffed and commercial for my taste...

- Heard that Mandriva is rather cool and simple also, haven't tested it myself, though.

By the way, it's always a good idea to get the .md5 files along with your downloads and verify them their integrity like this -> [http://www.etree.org/md5com.html](http://www.etree.org/md5com.html))
*****? ? ? ?*****
----------------------------------------------------------------------------------------------------------------------

2) run BurnCDCC, provide the proggy with the location of your sysrescue-ISO file and MARK the option 'SAO'! Insert a blank CD-ROM or CD-RW (it can also wipe CD-RW's!) and burn away (don't be confused by the drive-ejecting before the burning starts, that's OK, just acknowledge if asked for)!

4) Repeat the step with your Linux-Distro ISO-file.
 
5) Having the CD's ready, restart your system, with the sysrescue-CD in your drive. 
If your CD doesn't boot, restart again and enter BIOS, most probably by pressing DEL shortly after the first readings on your display. Find your way to the bootup sequence  / boot order option, where you put your CD/DVD drive on first place and your HD on second place. Save and restart.

6) You'll enter the sysrecue-CD's bootup-screen with a text based menu; just wait till it keeps booting. After booting has finished, type 'Gparted' and press enter; this runs the graphical partition manager. Select the HD you like to partition - if you have more than one drive - 'hda' is your 'primary master' drive, e.g. so far 'C:' under Windows. You'll get a graphical overview of your HD's partitions - in your case there should only be 'hda1', if you sticked to Vista without changing it's partition size so far. What you need to do now is the following:

7) rightclick your Vista's partition and delete it -- remember, YOU'LL GONNA LOSE ALL YOUR DATA THERE, SO BACK IT UP FIRST! (!!!!)
*** :arrow: You could also ONLY RESIZE it here, just by rightclick / resize and dragging the partition's bar to the size that fits you, of course, and spare yourself installing Vista newly, but PLEASE - whatever you do, BACK UP your data before.

8) Now you can either create a a new NTFS-partition of about half the HD's size (or more/or less, depending on how you use your Vista) and/or create an 'EXT3' partition in the remaining free space via 
- rightclick / new / entering size in MB / selecting filesystem - 
minus a value of about double the size of your physical RAM - 
you'll want to create a 'SWAP' partition for Linux in there. E.g.: 2048 MB RAM -> 4096 MB SWAP-partition. 


***** A SIDE NOTE HERE: you might want to create another partition with the FAT32 file  format right after the one for Vista and adjust the other partitions' size a bit for that purpose. The advantages are: 

* Linux and Windows both have native FAT32 support, thus making it perfect for local inter-OS filesharing.
* You can also change your Window's virtual memory location and hibernation-file's destination to this partition, sparing your Windows-system a lot of fragmentation trouble (yet performance - FAT32 is also faster than NTFS) and being able to back up your entire Windows partition with gigabytes of useless data simply cut off (e.g. ~3GB XP backup instead of up to 9GB at 2GB physical RAM)! 
* Finally, you have a partition to share files on via Network, if you like, without concerning about accessibility limitations; of course, this also means that everybody can access your memory dumps of Windows, if placed there - so you maybe have to decide for either purpose.
==> :!:UNFORTUNATELY, this might complicate things slightly, if Gparted only supports 3 primary partitions - depending on the version (and we already needed 3 for Vista, Linux and Swap). If creating the fourth 'primary' swap partition doesn't work out, you'll have delete Linux' partition again and create a primary partition after Vista's and FAT32, with the size including both Linux AND Swap. You then create 2 'extended partitions' for them INSIDE the primary one (rightclick 'unallocated space'). It works basically the same way, like doing a primary partition - just split up the space for Linux and Swap accordingly ******

  
9) Should you really decide to wipe Vista's partition and create new NTFS one for it, don't forget to flag it as 'boot' again after partitioning is finished ('via rightclick / manage flags'). 
Besides, I recommend you to use 'fast NTFS formatting' should you come across such an option somewhere in your installation procedure - unless you want to wait an hour or more to finishing it. 
Lastly, set SWAP to -> rightclick - 'swapon'. 

10) Finally, if you've set everything to your needs, click the blue checkmark overheads and acknowledge (EVERYTHING you changed so far is APPLIED ONLY THEN!).  

11) Now you can restart and re-install Vista first (and/or optionally redirect it's virtual memory- and hibernation-files to the FAT32 partition ), or directly install from the Linux-CD - depending on if you have wiped or just resized your Vista system:

- Install/leave Vista on your primary boot partition, in your case hda1 / 'C:'

- Install Linux (Ubuntu); just remember to make a 'manual' installation, selecting your prepared partitions for the Linux-system on hda2 (or hda3, if you have set up hda2 as FAT32 before); set the mountpoint to " / " (root) and use hda3 (respectively hda4) as swap. Install the grub boot-manager into the MBR - it will be your bootloader for both Vista and Linux and should automatically add Vista to the boot menu.


******************** Finish **********************

Should you not like my guide, here's one you might have seen before... (pretty easy one).

[http://www.psychocats.net/ubuntu/installing#partitioning](http://www.psychocats.net/ubuntu/installing#partitioning)


P.S.
Keep in mind, that Linux is still being developed (which OS isn't) and is growing better and better. If you like having more choices and control over what you can do with your PC, what you pay for software - didn't see Ubuntu for 130 bucks around so far ^^ - or which kind of data you provide to and get from the world, you should definitely stay tuned, it might be well worth the effort - 
M$ is gallopping off straight into the other direction... which train do you want to sit on?

):P


greetz

perixx

---

