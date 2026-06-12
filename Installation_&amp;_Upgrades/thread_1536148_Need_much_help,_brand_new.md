---
title: "Need much help, brand new"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by acolyte_to_jippity on 2010-07-21
Ok, so i've try out linux and start learning about it.

I bought a book to teach me about it (linux for dummies), but my particular case isn't in the installation section. See, i'm planning on putting Linux (either ubuntu or fedora, not sure which. hell if i understand GRUB right, it can be both) onto my portable hard drive (formatted as NTFS). What i need to know, is 
A) can i install them to seperate partitions on the drive, even if it's NTFS, 
B) can i then place data accessable to both linux and windows (my main laptop hard drive will remain vista), and 
C) if i enable GRUB, will the computer default to the windows bootloader whenever the USB drive isn't connected?

i plan to set my BIOS boot order to (primary) USB/connected external drive, and (secondary) c: (tertiary) CD drive.

Thanks for any help!

---

### Post by cj.surrusco on 2010-07-21
> **acolyte_to_jippity said:**
> Ok, so i've try out linux and start learning about it.

I bought a book to teach me about it (linux for dummies), but my particular case isn't in the installation section. See, i'm planning on putting Linux (either ubuntu or fedora, not sure which. hell if i understand GRUB right, it can be both) onto my portable hard drive (formatted as NTFS). What i need to know, is 
A) can i install them to seperate partitions on the drive, even if it's NTFS, 
B) can i then place data accessable to both linux and windows (my main laptop hard drive will remain vista), and 
C) if i enable GRUB, will the computer default to the windows bootloader whenever the USB drive isn't connected?

i plan to set my BIOS boot order to (primary) USB/connected external drive, and (secondary) c: (tertiary) CD drive.

Thanks for any help!

You should be able to do all of these things. What you want to do is resize the NTFS partition and leave space for the two Linux distros (look up HOW-TOs on dual booting Linux OSs).

Install each of the distros, I would install Ubuntu second.

You can store files on the NTFS partition on the external drive, and you will be able to access them from all three OSs. 

The Windows bootloader will remain with Vista on the internal drive and Grub will be on the External drive. As long as you set it in your BIOS, you will be able to boot into Windows automatically when there is no external drive attached. 

You will probably have more questions if this is your first time doing something like this, but that was the outline of you have to do.

---

### Post by acolyte_to_jippity on 2010-07-21
ok, if i didn't have my one friend in gmail chat, i'd have  no clue about most of that.

he suggest i remove the harddrive from my laptop before connecting the portable, installing ( while partitionaing 2 sections to ext3) ubuntu.  this keeps GRUB totally on the portable, and won't interfere w/ loading the computer w/out the portable plugged in.  BUT, as long as the portable's in when i start up, GRUB will come up, and i can then procede to load windows through it.

anything special i must do for GRUB to link to the windows install?

---

### Post by linux18 on 2010-07-21
> **acolyte_to_jippity said:**
> ok, if i didn't have my one friend in gmail chat, i'd have  no clue about most of that.

he suggest i remove the harddrive from my laptop before connecting the portable, installing ( while partitionaing 2 sections to ext3) ubuntu.  this keeps GRUB totally on the portable, and won't interfere w/ loading the computer w/out the portable plugged in.  BUT, as long as the portable's in when i start up, GRUB will come up, and i can then procede to load windows through it.

anything special i must do for GRUB to link to the windows install?
If you install linux to the external drive that you mentioned theres nothing you need to do as far as partitioning or grub on the ntfs laptop drive. How big are the drives both laptop and external?

---

### Post by acolyte_to_jippity on 2010-07-21
> **linux18 said:**
> If you install linux to the external drive that you mentioned theres nothing you need to do as far as partitioning or grub on the ntfs laptop drive. How big are the drives both laptop and external?

the laptop drive's nearing capacity.  i really don't want to install to it.

the portable has about 50gb of stuff on it, and about 408 gb free.  all NTFS though, like i said

---

### Post by _Kaze_ on 2010-07-21
So you just need to defrag your external and repartition. Windows 7 has a partitioning tool you can use, or you can a random one on the internet somewhere. Once you repartition, install is very simple, you just boot from the install cd and choose the repartitioned space from the drop down list when it asks you which drive you want to install to (you would want to choose the space that is empty ). Grub is automatically installed. Although, I'm not sure if you would need to make a swap space,which would require you making another smaller partition.

---

### Post by linux18 on 2010-07-21
> **acolyte_to_jippity said:**
> the laptop drive's nearing capacity.  i really don't want to install to it.

the portable has about 50gb of stuff on it, and about 408 gb free.  all NTFS though, like i said
okay, double defrag your external and shrink it's partition ( to 60 -80 GB maybe ) always remember to resize from left to right. you can use the ubuntu live cd to resize partitions then after applying the change format the newly created free space as EXT4.

---

### Post by acolyte_to_jippity on 2010-07-21
> **_Kaze_ said:**
> So you just need to defrag your external and repartition. Windows 7 has a partitioning tool you can use, or you can a random one on the internet somewhere. Once you repartition, install is very simple, you just boot from the install cd and choose the repartitioned space from the drop down list when it asks you which drive you want to install to (you would want to choose the space that is empty ). Grub is automatically installed. Although, I'm not sure if you would need to make a swap space,which would require you making another smaller partition.

first off, vista.  and could i make the partition useing the ubuntu installer?  skip a step you know?  

[QUOTE=linux18]okay, double defrag your external and shrink it's partition ( to 60 -80 GB maybe ) always remember to resize from left to right. you can use the ubuntu live cd to resize partitions then after applying the change format the newly created free space as EXT4.[/QUOTE]

o.O  what?  imagine that i am an idiot when it comes to things like this.  put me behind a c++ or a java IDE (netbeans and codeblocks FTW) and i can fake my way through.  but double-defrag?  and shrinking the partitions?

---

### Post by cj.surrusco on 2010-07-22
> **acolyte_to_jippity said:**
> first off, vista.  and could i make the partition useing the ubuntu installer?  skip a step you know?  

Yeah you can do that, but you have to resize the NTFS partition before install anyway.

> **acolyte_to_jippity said:**
> o.O  what?  imagine that i am an idiot when it comes to things like this.  put me behind a c++ or a java IDE (netbeans and codeblocks FTW) and i can fake my way through.  but double-defrag?  and shrinking the partitions?

I think by a double-defrag he means to simply defragment the drive twice. And shrinking the partition moves the NTFS partition over so that there is room for the Linux file systems. You can do that with a tool called Easus Partition Master, which is my preferred partitioner for Windows, and it's free.

---

### Post by acolyte_to_jippity on 2010-07-22
> **cj.surrusco said:**
> Yeah you can do that, but you have to resize the NTFS partition before install anyway.
 
 
 
I think by a double-defrag he means to simply defragment the drive twice. And shrinking the partition moves the NTFS partition over so that there is room for the Linux file systems. You can do that with a tool called Easus Partition Master, which is my preferred partitioner for Windows, and it's free.
 
 
cool, thanks.  i'm going to try installing it tionight.  just need to back up my external, and burn the .iso.
 
will i need to reformat the external,. or can i keep the data that's on there intact?

---

### Post by Nick_Jinn on 2010-07-22
> **_Kaze_ said:**
> So you just need to defrag your external and repartition. Windows 7 has a partitioning tool you can use, or you can a random one on the internet somewhere. Once you repartition, install is very simple, you just boot from the install cd and choose the repartitioned space from the drop down list when it asks you which drive you want to install to (you would want to choose the space that is empty ). Grub is automatically installed. Although, I'm not sure if you would need to make a swap space,which would require you making another smaller partition.


Or he can use gparted from live disk before the installation starts.

---

### Post by acolyte_to_jippity on 2010-07-22
> **Nick_Jinn said:**
> Or he can use gparted from live disk before the installation starts.
 
the book mentioned that i can partition during the istallation

---

### Post by Nick_Jinn on 2010-07-22
Its easier than you think. Just plop in the disk. Installation is dummy proof.....if you go manual though, use the 15gb partition for /root, and also create a partition for /home or else it will all go only to the /root partition.

Its not at all hard to get started.

You may end up needing help getting it to work with some of your hardware though....or maybe not.

---

### Post by acolyte_to_jippity on 2010-07-22
> **Nick_Jinn said:**
> Its easier than you think. Just plop in the disk. Installation is dummy proof.....if you go manual though, use the 15gb partition for /root, and also create a partition for /home or else it will all go only to the /root partition.
 
Its not at all hard to get started.
 
You may end up needing help getting it to work with some of your hardware though....or maybe not.
 
ok, so i make a handful of partitions on the external, a 15-20 gb (i have the room) for just plain /
another bunch (how much) for /home (and what does that do?
and a small one (how much) for /swap
 
the book mentioned i want to make something as big as my RAM, but it's a 32-bit version of linux and i got 4 gb of RAM.

---

### Post by Nick_Jinn on 2010-07-22
I would just make 1 / partition and 1 larger /home partition and one large shared NTFS partition (With Gparted, not the intaller). You can create / and /home with the installer, but use Gparted for the shared NTFS partition.

You dont need to worry about /boot or any of the others. It will be installed automatically.


You dont even really NEED to seperate /home and /. Its just there so you can reinstall the operating system without losing your files.

---

### Post by acolyte_to_jippity on 2010-07-22
> **Nick_Jinn said:**
> I would just make 1 / partition and 1 larger /home partition and one large shared NTFS partition (With Gparted, not the intaller). You can create / and /home with the installer, but use Gparted for the shared NTFS partition.
 
You dont need to worry about /boot or any of the others. It will be installed automatically.
 
 
You dont even really NEED to seperate /home and /. Its just there so you can reinstall the operating system without losing your files.
 
what about something for /swap?
 
and what size should these be?  i have about 100 gb to work with, since i want to keep about 300 for the NTFS data section

---

### Post by Nick_Jinn on 2010-07-22
Double your RAM is a good number for Swap.

---

### Post by acolyte_to_jippity on 2010-07-22
> **Nick_Jinn said:**
> Double your RAM is a good number for Swap.
 
so since this is 32-bit linux, i make a 4gb partition and in the installer i assign /swap to it?

---

### Post by Nick_Jinn on 2010-07-22
> **acolyte_to_jippity said:**
> so since this is 32-bit linux, i make a 4gb partition and in the installer i assign /swap to it?

Actually, 32bit linux can detect 3.25gb of ram. However, what you actually have may vary.

You only NEED 2gb or so, maybe less. Double your existing ram is a good number though.

---

### Post by acolyte_to_jippity on 2010-07-22
> **Nick_Jinn said:**
> Actually, 32bit linux can detect 3.25gb of ram. However, what you actually have may vary.
 
You only NEED 2gb or so, maybe less. Double your existing ram is a good number though.
 i have 4 gb, so even if ubuntu'll only detect 3.25 og it, i should still allocate the full 8gb?

---

### Post by _Kaze_ on 2010-07-22
Well vista doesn't like the repartition tool on the ubuntu disc. I recall I had problems once with it. I think it corrupted the drive or made it where I couldn't boot. That might be different now.

---

### Post by acolyte_to_jippity on 2010-07-22
> **_Kaze_ said:**
> Well vista doesn't like the repartition tool on the ubuntu disc. I recall I had problems once with it. I think it corrupted the drive or made it where I couldn't boot. That might be different now.
 
even if i don't have vista installed to my external?  remember i'll be working w/ a freshly formatted portable hard drive, not the one in the laptop (which shouldn't be touched at all by the install, right?)

---

### Post by cj.surrusco on 2010-07-22
> **acolyte_to_jippity said:**
> even if i don't have vista installed to my external?  remember i'll be working w/ a freshly formatted portable hard drive, not the one in the laptop (which shouldn't be touched at all by the install, right?)

You shouldn't need to backup the partition on the external drive, but it would be a good idea since resizes sometimes can corrupt a working file system. In fact, just a couple of weeks ago, I lost over 300GB of data due to a resize error with an ext3 file system.

---

### Post by acolyte_to_jippity on 2010-07-22
> **cj.surrusco said:**
> You shouldn't need to backup the partition on the external drive, but it would be a good idea since resizes sometimes can corrupt a working file system. In fact, just a couple of weeks ago, I lost over 300GB of data due to a resize error with an ext3 file system.
 
o.O
 
:hug:
 
and once again, there is no partition on the external.  it's just a flat-out, from the box style portable hard drive.  i have 50gb worth of .iso's on there, but it's all one big drive.  i'd have to use that software someone mentioned to make the partitions.
 
so i make a 15 gb one, a 40 gb one, and let the installer take care of making the other partitions.

---

### Post by -kg- on 2010-07-22
> ...there is no partition on the external. it's just a flat-out, from the box style portable hard drive. i have 50gb worth of .iso's on there, but it's all one big drive.

Yes, there is a partition on the external...one large one that covers the entire drive.  You have 50GB of .iso's on there?  You can't have anything on a drive unless there's a partition and it's formatted.  Most hard drives these days come pre-partitioned.  Back in the day, you had to do it yourself, with a tool that came on a floppy.

There is a method you can use to install Ubuntu to that drive without changing the MBR (Master Boot Record) on your internal drive.  First, you will need to shrink the partition that exists on your external.  <Edit> I'm assuming here that your computer is not super-old and is able to boot from a USB device.  I have a computer that won't, and since it's a laptop and its CD drive went out, I can't load Linux on it.

I would suggest you back up the data on your external before starting.  As was said before, any partitioning operation is more or less dangerous, and you could lose your data.  If you have it backed up to another location, then nothing is lost.  Read at the link in my signature block for a good tutorial on partitioning operations.

Once you shrink the existing partition, then pop in the Live CD.  If you're going to put two distros on it, then determine which OS you want to have control the GRUB bootloader.  It has been suggested that it be Ubuntu, and I concur.  Fedora (***still!***) has Legacy GRUB, and it (***still!***) hasn't been patched to handle the ext4 filesystem.  The 10.04 installer defaults to ext4, and if you give control of the bootloader to Fedora, it won't detect Ubuntu's GRUB in it's ext4 partition.

Now you seemed to be a little confused about what ext4, etc., was.  Ext2/3/4 is a file system, just like NTFS or FAT16/32 are for Windows.  That is what the format of the partitions you are creating for Linux are.  While Linux will detect, read, and write Windows file formats, it will not run from one.  Minimally, your /boot and /root directories will need to be on an ext2/3/4 (or ReisFS, but let's not confuse you at this point) in order for Linux to operate.  The only circumstances under which you can install Ubuntu on an NTFS or FAT32 partition is with WUBI, where basically it is installed like a Windows program.

Anyway, if I remember correctly, both Fedora and (I know that) Ubuntu has a way to install GRUB to a non-default location.  The default location is in the MBR of the first (internal) drive installed into the computer (sda).  If there is only one drive in your computer, your external drive will be sdb.  In Ubuntu (and in Fedora, if memory serves me correctly), on the last screen of the installation process is a button marked "Advanced" (bottom right in Ubuntu).

Clicking on the "Advanced" button takes you to a screen where you can specify where to install the GRUB bootloader.  You don't want to install GRUB to sda, since that is where your Windows bootloader resides.  It will work if you install it there, but if you remove the external drive your computer will be unbootable, since the rest of GRUB resides in the partition of the installation that puts it there...in this case, the one on your external drive.

You will want to install GRUB in the MBR of the external drive.  To do this, you want to click on the "Advanced" button and specify "sdb", or whatever the drive specification of your external drive is.  That is for the installation that you want to control the GRUB bootloader.  You can do that with both installations as long as you install the one you want to control the bootloader (Ubuntu, for sure!) last.

If you install it first, it's still easy enough.  When you install Fedora, just specify that the GRUB bootloader be installed in Fedora's root partition.  That will be "sdb5," "sdb6," or whatever it is when you install it.  the MBR of the drive will be just the letters, like "sdb".  The partitions will always be specified by the drive letters followed by a number, like "sdb5."

If you install Fedora 2nd, after installation you will have to reboot into Lucid, go into the terminal, and run:

```
sudo update-grub
```

from the command line.  This will detect the Fedora GRUB and cause it to be included in the GRUB boot menu.

Again, I would install Fedora first and specify "sdb" (or whatever it is...with one drive in your computer it will be sdb, but if you have two drives it will be sdc) to install the GRUB bootloader.  Then, when you install Ubuntu, specify the same thing, and Ubuntu's bootloader will replace Fedora's and autodetect Fedora, giving you both selections in the menu.

As far as a separate / and /home partition, you can do what you want.  If you want a separate /home partition you will have to go the Manual Partitioning route, as default will give you only a /(root) and a swap partition.  In addition, it will complicate multiple installs, as the automatic route will use all the free space available, and you'll have to shrink it to make the subsequent installation.

If you decide to go the separate partitions route, 15GB is fine for both "/" partitions.  That's what I always use, and unless you're planning something funky with a lot of installations, or massive processing, that's fine.  "/home" is mostly where you keep your data.  If you anticipate having a lot of data under Linux (which can also be on an NTFS or FAT32 partition), then you'll need more room in your /home partition.  I have mine around 20 GB, but you can make it more if you wish.

Swap space is a much debated matter.  If you anticipate "Hibernating" your computer, you will need *at least* the size of your installed RAM (and preferably more...around 1.5 X RAM), since a "snapshot" of RAM is stored in Swap so that the computer is in the same state when you bring it out of hibernation.

If not, you can decrease this size.  4 GB of RAM is quite an amount.  I have 2 GB and almost never use Swap at all.  When I do, it's a very low level.  Oh, and:

> [I][COLOR="RoyalBlue"]Nick_Jinn:
Actually, 32bit linux can detect 3.25gb of ram.[/COLOR][/I]

Actually, it can, using the PAE kernel.  I personally would make the Swap space 6 GB, unless you don't anticipate using Hibernate.  Then 4GB or even less would be sufficient.

Taking all the above into account, shrink the existing partition on your external drive to the size you want it to be and, taking the remaining free space, subtract the 15GB a piece for the two root partitions, whatever size swap partition you think you'll need (you'll only need one swap partition.  Both installations will share it.

Then either divide the space equally for the /home partitions for each installation or, if you anticipate needing more space for one than for the other, divide it accordingly.  You can either create the partitions separately using both installer's partitioning tools, or create the partitions beforehand using GParted, either off the Live CD or the GParted Live CD (mentioned in the tutorial in my signature block).  Then all you have to do is go into Manual Partitioning in the Installers and mark the desired partitions with their mount points.

I know all this sounds complicated, but it really isn't that hard.  Just post here if you run into any problems and I (or someone) will walk you through the problem points.  The only thing you need to make sure of is that you ensure that GRUB gets installed on sdb (or whatever) rather than sda (the default).

---

### Post by acolyte_to_jippity on 2010-07-22
ummm, you mentioned Lucid.

i'm not installing lucid (Ubuntu 10.04 LTS (Lucid Lynx)), i'm installing Jaunty (Ubuntu 9.04 (Jaunty Jackalope))

whatever.  backup of external's almost complete.  i'm installing after this.  wish me luck

---

### Post by acolyte_to_jippity on 2010-07-22
ok, so it installed fine.  it's running off my portable HD fine.  
 
...
 
it looks like a mac...
 
damn...
 
anyway, when i go to thelittle "log out" thing ont the desktop, it appears to take me to a command prompt.  what do i do from there?

---

### Post by -kg- on 2010-07-23
Oh mercy...I had to go play in pool league... :p

When you log out, you are taken to what looks like a command prompt.  This is the screen from which you would log back in as another user, if you had one set up.  You should be able to log back in to Ubuntu from that screen (or shut down, I think).

If you just want to shut down or reboot, you would choose "Shutdown" from the same menu.  It will present you with choices including Shutdown, Reboot, or Log Out.  That's if I remember Jaunty's menu correctly.  Lucid has an entry for each from that icon.  Can you post a screen shot or two of what you're looking at?  I don't have Jaunty installed on any of my machines anymore.  Not even Karmic.

Jaunty is good, and it is almost the same thing as Lucid.  There are a few changes and a few additions.  Also, Lucid is the current LTS (Long Term Support) release.

---

### Post by acolyte_to_jippity on 2010-07-23
only 2 issues so far
 
1) GRUB can't boot windows, but i can just restart w/out external plugged in
2) Windows no longer recognises the portable as being formatted at all
 
 
that second thing might be fixed w/ a reformat and reinstall of linux. maybe i made the final partition wrong, but i believe i made it a fat32...and i selected do not use because i didn't want linux to use it.
 
at the moment, my 2 biggest concerns are the above.  hell, even the grub/windows thing is fairly minor compared to the other one.  I need that hard drive to have any space not occupied by linux be NTFS format, and i need to be able to access it easily from vista.

---

### Post by -kg- on 2010-07-27
A long time between posts.  I have too many irons in the fire.  Hopefully, you've already figured it out, but in case you haven't...

> **acolyte_to_jippity said:**
> only 2 issues so far
 
1) GRUB can't boot windows, but i can just restart w/out external plugged in
2) Windows no longer recognises the portable as being formatted at all
 
 
that second thing might be fixed w/ a reformat and reinstall of linux. maybe i made the final partition wrong, but i believe i made it a fat32...and i selected do not use because i didn't want linux to use it.
 
at the moment, my 2 biggest concerns are the above.  hell, even the grub/windows thing is fairly minor compared to the other one.  I need that hard drive to have any space not occupied by linux be NTFS format, and i need to be able to access it easily from vista.

OK, for the first issue, as long as you're able to unplug the external and boot normally into Windows, then like you said, it isn't a big issue.  Just unplug the external, boot into Windows, then plug the external back in and you should have access to the partition(s) formatted to a Windows format (that you don't have?).

The second problem surprises me, though.  I just launched GParted from my installation and started to create a partition on my external in free space.  NTFS was one of the selections I had to format it to.  I didn't follow through with the create, but since I was able to select it, I assume that it was a legitimate FS format.  It might be that the one under Jaunty won't, but I would think that it would.

Thing is, Windows should detect even a FAT32 partition, unless they changed it in Windows 7.  Let me see...yep, according to the [Windows 7 Forum]("http://windows7forums.com/windows-7-discussion/3038-test-windows-7-fat32-no-go-you-need-ntfs.html"):

> just tested trying to install W7 on a FAT disk -- no-go it appears it will only install on NTFS although [COLOR="Red"]it can read / write FAT32 disks (and FAT 16 if you still have them --maybe some SD cards etc)[/COLOR].

So even if you did create a FAT32 partition, Windows 7 should still read it.  I know Vista does.

Just to make sure, do one of two things...either open a terminal and run the command...

```
sudo fdisk -l
```

...or, if you're a more "graphical" person, install GParted from the repos (it's not installed by default...you can also run it from the Live CD) and look at the partitions on your external drive.  Make sure that the partition you wanted for Windows is actually there.  I suspect that, for some reason, it isn't, otherwise Windows would detect and use it just like it detected and used the original partition.

I ran across one other issue...the Windows 7 partitioner (and presumably the one in Vista) will not create a FAT32 partition over 32 GB in size.  I ***"think"***  it will read one, but I'm not sure, since I do very little under Vista anymore, and have not checked to see if I could access the FAT32 partition I made on it (at 465 GB...it's a TB drive).

I'll boot into Vista ( #-o ) and report back...

Yep, Vista has complete access to the 465GB FAT32 partition on my external, so that shouldn't be your problem.  The only thing I can see is that somehow the partition either didn't get created, wasn't formatted, or was somehow deleted in the installation process.  You need to check that it's still present and formatted correctly using one of the methods above.

The following is the output on my external drive from the "fdisk -l" command:

```
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           2      121601   976752000    f  W95 Ext'd (LBA)
/dev/sdc5               2       60801   488375968+   b  W95 FAT32
/dev/sdc6          101173      121569   163838871   83  Linux
/dev/sdc7           60802       67341    52532518+   7  HPFS/NTFS

Partition table entries are not in disk order
```

From the first line, you see that I have the entire drive in an Extended partition.  I then have 3 logical partitions, one of which is FAT32, one of which is Linux (ext3 in this case, though the command doesn't show it), and the last one is NTFS.

However, GParted will show all of this as you can see from this screenshot from one of the pages at the link in my signature block:

[IMG]http://i718.photobucket.com/albums/ww185/ubun4uc/ExtPartDemo.png[/IMG]

In the above screenshot I hadn't actually created the partitions on the hard drive.  That's why they're listed as "New Partition #X".  If I had actually created them, the Extended Partition would have been sdc(2-4) and the Logical partitions would have been sdc5 through sdc12, in the order of their creation (order of creation is used in partition numbering schemes, which is why, at the bottom of the "fdisk -l" output, it says "Partition table entries are not in disk order").

Anyway, hopefully you have these issues resolved, but if not, I hope this helps.

---

### Post by acolyte_to_jippity on 2010-07-27
well, what i'm going to do is reformat in vista, to clean the disk.  then, knowing i have a vista-useable partition (of the entire disk size) i'll download gparted (i assume it'll run on windows) and make the 4 partitions (/, /home, one for swap, and the big one).
 
i'll make sure to setr the big one as ntfs, and then i'll reinstall linux to the portable, having it reformat and assign the 3 other partitions to what it needs.
 
if this works as i expect it to, it shouldn't touch the ntfs partition at all, and just install to the 3 linux ones.  then i'll be able to use the big ntfs one in vista.  i madeanother thread about this since i've kinda gone past the original install-question (with quite alot of help from you btw, thx!)
 
new thread located [here]("http://ubuntuforums.org/showthread.php?t=1540053")

---

