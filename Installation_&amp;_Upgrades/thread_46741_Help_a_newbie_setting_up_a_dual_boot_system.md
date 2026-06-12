---
title: "Help a newbie setting up a dual boot system"
date: 2005-07-05
forum: Installation &amp; Upgrades
---

### Post by tank45 on 2005-07-05
I've been wanting to use Linux for the longest time and I want to try to get a dual boot system going on my Toshiba Satellite A10/15. Ubuntu seems to be recommended a lot from all my research.  If I could just get a step by step or something that would be great. Obviously I need to create a partition and other stuff i'm just real newb when it comes to this type of thing I really want to get a dual boot system going so any help would be appreciated.

Tank

(hopefully this is the right board to post this is >_<)

---

### Post by ano1 on 2005-07-06
Hello,

You are correct that you will need to create partitions. When I have done this in the past I created two: one for M$ and one for Linux. If you are using XP the Installer has a partitioning tool. I have done dual boots with other Linux OS(s), not Ubuntu, but from what I have read the process is the same. But if anyone wants to correct me feel free to do so.

Your 1st step should be installing Windows. The installer should give you the option of creating partitions. One thing to keep in mind is the format of the windows partition. If you use NTFS Linux will be able to read but not write to that partition. The decision basically depends on if you want to share and edit files between the two OS(s).

Next comes the install of Ubuntu. Install it on your 2nd partition. From what I have read the installer should do the rest of the setup automatically for you. What this means is that it should detect the Windows installation and setup the Linux boot loader so that it gives you the option of booting to Windows or to Linux. Every time you boot up your system you will have menu with the option of booting to Windows or Ubuntu.

I hope this helps you. Sorry if this is not as detailed as you might need. The community here is knowledgable (most more than  I) and freindly so I am sure if you have further questions we will be able to answer them for you. Best of luck.

---

### Post by tank45 on 2005-07-06
right now im using the live cd right now and im pretty impressed with this and it's all free it just seems so weird cant you from the ubuntu installer create a partition?

From what your telling me it sounds like you should be doing all of this as if your wanting to do a clean install of windows?

---

### Post by ano1 on 2005-07-06
[QUOTE=tank45]right now im using the live cd right now and im pretty impressed with this and it's all free it just seems so weird cant you from the ubuntu installer create a partition?

From what your telling me it sounds like you should be doing all of this as if your wanting to do a clean install of windows?[/QUOTE]

I think you should be able to partition from the ubuntu installer, but am not positive. The reason I discussed doing this from a clean install is because I personally don't know a safe way to resize a present partition, so that you can create another partition on the same drive. Anyone else have some imput here? Good luck.

---

### Post by not_yet on 2005-07-06
hello tank45,

I'll just throw my 2 cents in here.........

Yes the Ubuntu installer can partition your drive :) 

having said that, please remember that this is a "black art"  ;-)  ;-) 

before you do anything, back up your data if its important to you

look here for a pictorial on the install process [http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=1](http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=1)

good luck

---

### Post by Darkscot on 2005-07-06
[QUOTE=tank45]I've been wanting to use Linux for the longest time and I want to try to get a dual boot system going on my Toshiba Satellite A10/15. Ubuntu seems to be recommended a lot from all my research.  If I could just get a step by step or something that would be great. Obviously I need to create a partition and other stuff i'm just real newb when it comes to this type of thing I really want to get a dual boot system going so any help would be appreciated.

Tank

(hopefully this is the right board to post this is >_<)[/QUOTE]

There are two, no three, things you should do BEFORE you install Unbuntu.
1. Backup you data!
2. Run a Scandisk in Windows to check for an errors on your drive.
3. Defrag your drive.  This is very important as Ubuntu will be taking a section of your hard drive and you don't want it to take a section with data on it.  Some distros (like Mandrake) warn you if your drive is too fragmented but i don't know if Ubuntu does.  
4. Backup your data again just to make sure.

I have installed Ubuntu on two PC's, one with Windows ME and one XP.  Both went without a hitch but the sction of the instal that partitions your drive is not very intuitive (IMHO).  So read up about this before you come to it so you know the correct answers.  

One final warning.  The default option when installing is to format your whole hard drive.  YOu DO NOT want to select that.

---

### Post by Karl S. on 2005-07-07
Okay, here's another newbie. I've been using Ubuntu on my desktop for a couple of weeks. Somehow I managed to use Partition Magic to set up a partition and install Ubuntu, creating a dual boot situation, all without erasing any data accidentally.

But I did that pretty much through guesswork.

I managed to requisition a new IBM thinkpad the other day and I want to do the same thing with it. I've been having a lot of trouble with the desktop -- chiefly with installing Windows over Ubuntu in qemu -- because of, I think, hardware problems. There shouldn't be any problems with the laptop.

But I don't want to guess this time. For one, I just don't have the time to spend an hour trying to figure this stuff out again. The Ubuntu installer, I'm sorry to say, sort of sucks for someone like me who doesn't know anything about computers.

Right now, I'm at the section where I'm trying to install Ubuntu on one partition. I don't know what to do. Here are the settings:

At the Partition Disks section of the Ubuntu install:

IDE1 master (hda) - 40 GB
#1 primary 29.5 GB ntfs
#5 logical 10.5 GB ext2

I want to install Ubuntu in the 10.5 GB partition. What should it be set to (i.e., how should it be used? ext2? ext3? reiserFS? I have no idea what any of this means), should it be formatted? mount points? etc. 
Should I got back out to partition magic and get rid of the 10.5 GB partition and just let Ubuntu set it up? Should I go back into partition magic and set up a 502MB Linux swap before the primary partition? It's a new laptop, so there's no data on it yet that I don't have backed up on my external hd, but I'd rather not screw up the windows section, since I finally got all the apps I need installed.

The help section for this point, which is the only point really in the install where users have to make decisions, needs to be much clearer!

---

### Post by trivialpackets on 2005-07-07
[QUOTE=Karl S.]Okay, here's another newbie. I've been using Ubuntu on my desktop for a couple of weeks. Somehow I managed to use Partition Magic to set up a partition and install Ubuntu, creating a dual boot situation, all without erasing any data accidentally.

But I did that pretty much through guesswork.

I managed to requisition a new IBM thinkpad the other day and I want to do the same thing with it. I've been having a lot of trouble with the desktop -- chiefly with installing Windows over Ubuntu in qemu -- because of, I think, hardware problems. There shouldn't be any problems with the laptop.

But I don't want to guess this time. For one, I just don't have the time to spend an hour trying to figure this stuff out again. The Ubuntu installer, I'm sorry to say, sort of sucks for someone like me who doesn't know anything about computers.

Right now, I'm at the section where I'm trying to install Ubuntu on one partition. I don't know what to do. Here are the settings:

At the Partition Disks section of the Ubuntu install:

IDE1 master (hda) - 40 GB
#1 primary 29.5 GB ntfs
#5 logical 10.5 GB ext2

I want to install Ubuntu in the 10.5 GB partition. What should it be set to (i.e., how should it be used? ext2? ext3? reiserFS? I have no idea what any of this means), should it be formatted? mount points? etc. 
Should I got back out to partition magic and get rid of the 10.5 GB partition and just let Ubuntu set it up? Should I go back into partition magic and set up a 502MB Linux swap before the primary partition? It's a new laptop, so there's no data on it yet that I don't have backed up on my external hd, but I'd rather not screw up the windows section, since I finally got all the apps I need installed.

The help section for this point, which is the only point really in the install where users have to make decisions, needs to be much clearer![/QUOTE]
 You'll want a swap most likely, so that may be a necessary step.  As to the others, the choice between ext2 ext3 and reiser is up to you, I've had all three working fine and am currently with reiser, but ext3 was fine as well.  Format yes, Mount point:  =   /    should be fine.  IN fact, just use ubuntu to resize the partition of your 10.5, make a swap in there and do the same.  SHould be fine.

---

### Post by Karl S. on 2005-07-07
[QUOTE=eric.proctor]You'll want a swap most likely, so that may be a necessary step.  As to the others, the choice between ext2 ext3 and reiser is up to you, I've had all three working fine and am currently with reiser, but ext3 was fine as well.  Format yes, Mount point:  =   /    should be fine.  IN fact, just use ubuntu to resize the partition of your 10.5, make a swap in there and do the same.  SHould be fine.[/QUOTE]

I'm sorry but I don't understand. I really don't know anything about computers.

I need to know:

a) should I got back into Partition Magic and set up a Linux Swap (maybe)
b) having done that, maybe, now, maybe, with three partitions, what do I do once I get to the Partition section of the Ubuntu Install to install Ubuntu on the 10G section, leaving the Windows partition intact and using the swap for whatever it's meant to be used for?

The screenshots of the Ubuntu install are useless on this point, by the way, since they show only the option of formatting the entire hard drive.

---

### Post by trivialpackets on 2005-07-07
[QUOTE=Karl S.]I'm sorry but I don't understand. I really don't know anything about computers.

I need to know:

a) should I got back into Partition Magic and set up a Linux Swap (maybe)
b) having done that, maybe, now, maybe, with three partitions, what do I do once I get to the Partition section of the Ubuntu Install to install Ubuntu on the 10G section, leaving the Windows partition intact and using the swap for whatever it's meant to be used for?

The screenshots of the Ubuntu install are useless on this point, by the way, since they show only the option of formatting the entire hard drive.[/QUOTE]

I don't think there's a need for that.  As I recall from setting up, Ubuntu should allow you to create the swap.  You can go through, delete the 10.5 gb partition.  Set up two in the place of where that one was.  You have to size out the partitions using sectors I believe, so you may have to experiement to get the swap space that you want.  So at this point, youll have 3 partitions, Windows and two other partitions, we'll say of type ext3 for the 10 gb partition and swap for the .5 gb partition.  The swap space is used as an extension of RAM I believe, which will help the performance of your system.  Good idea.  On the 10 gb partition, set it to format as ext3.  Mount Point set to:  "/" (without the quotes) And I unfortunatly don't recall the other questions you may have regarding this.  I believe you'll just click on the save changes and go ahead and repartition this drive.  No need to mess with the windows partition at all, and it should be safe to save grub to MBR when it asks.

---

### Post by Karl S. on 2005-07-07
[QUOTE=eric.proctor]I don't think there's a need for that.  As I recall from setting up, Ubuntu should allow you to create the swap.  You can go through, delete the 10.5 gb partition.  Set up two in the place of where that one was.  You have to size out the partitions using sectors I believe, so you may have to experiement to get the swap space that you want.  So at this point, youll have 3 partitions, Windows and two other partitions, we'll say of type ext3 for the 10 gb partition and swap for the .5 gb partition.  The swap space is used as an extension of RAM I believe, which will help the performance of your system.  Good idea.  On the 10 gb partition, set it to format as ext3.  Mount Point set to:  "/" (without the quotes) And I unfortunatly don't recall the other questions you may have regarding this.  I believe you'll just click on the save changes and go ahead and repartition this drive.  No need to mess with the windows partition at all, and it should be safe to save grub to MBR when it asks.[/QUOTE]

I'm sorry but this still doesn't make any sense to me.

"I don't think there's a need for that."

What's the reference for the "that"? Using Partition Magic? Using Partition Magic to delete the 10G partition? Using Partition Magic to set up the swap?

"You can go through, delete the 10.5 gb partition."

Go through what? The Ubuntu installation process? Partition Magic? Something else?

"Set up two in the place of where that one was."

Using Partition Magic? Using the Ubuntu Install? Two what? Partitions?

"You have to size out the partitions using sectors I believe, so you may have to experiement to get the swap space that you want."

No idea what this means. All I know is that I have 10.5G set aside for Ubuntu on my deskttop, 502 MB for the swap space, and 29G reserved for Windows, and it works just fine. 

"Mount Point set to:  "/" (without the quotes)"

Okay, I think I understand. Set the 'mount point' to "/" (no quotes) in the 10G partition (i.e., the one where I want Ubuntu). This partition with the / mount point can be set to Ext3, but it could be set to something else and still work. But Ext3 is preferable for my purposes. Is this right?

"I believe you'll just click on the save changes and go ahead and repartition this drive"

In Partition Magic, it's 'click' on ok and then the machine reboots and sets up the partitions. In the Ubuntu Install, there's no clicking. There's hitting ENTER and sometimes hitting ESC to go back. I'm still not sure if I'm working in Windows with Partition Magic or if I'm doing all this DURING the Ubuntu Install, having beforehand gone into windows and merged the previously set up 10G partition with the whole HD.

"No need to mess with the windows partition at all"

Do you mean insofar as I'm not installing Ubuntu in the Windows partition? Do I ensure that by marking Ext3 in some way with the 'mount point'??

"..and it should be safe to save grub to MBR when it asks."

Don't know what the acronym means. Remember: I don't know anything about computers.



--

I could probably figure this out on my own now, but I really believe there needs to be a clear set of instructions for newbies who know nothing about computers (like me) to set up a dual boot without the fear that they're destroying their windows OS and data. I apologize if I seem a bit sharp -- among the things I do in real life is teach Freshman Comp (i.e., first-year College English), so I developed sense for when things just aren't clear enough.

--

Thanks for your help so far. I'll check back on this thread again in 8 hours or so.

---

### Post by mingus on 2005-07-07
Patience, please.  Yes, the screen interaction could be friendlier.  Your challenge however is principally due to having zero exposure to both the concepts and the terminology, and no context to put that in because you know nothing about computers.  Just give yourself and others a bit of slack . . .

To get Ubuntu installed . . . 

1.  Boot into Windows, run Partition Magic, delete the logical partition *and* the extended partition in which it resides.  You should now show unallocated free space.
2.  Boot from the Ubuntu install CD with the command:  linux
3.  You will reach a screen saying "This installer can guide you through partitioning or, if you prefer, you can do it manually . . ." and will display under "Partitioning method:" your choices.  On your system it will *probably* have 3:  Erase; Use largest contiguous space; Manually.  Choose "largest contiguous space."
4.  The partitioner will then develop a recommendation and present that to you.  On your system, it will *probably* suggest 2 partitions, 1 will be shown as ext3 and the other swap.  Select the [yes] box and hit enter.

Done.  

The "probably" is because there is intelligence in the partitioner.  The above is one likely configuration, but others are just as good.  I can't be positive what will be chosen for your particular system, although the above is a good bet.

When you get to the boot loader installation step, grub will be offerred as the default, as well as the default of installing it in the Master Boot Record (MBR).  If you wish, you can take these defaults and all should go well.  But on occasion there is a glitch with the dual-booting setup.  Since you are so new, take his precaution if you can:

This requires that your laptop have a bootable floppy drive.  If it doesn't, skip this.  If it does :  Say [no] to the default, which will take you another screen where you can specify the boot loader location.  Place a clean floppy in the drive. Type "/dev/fd0" and hit enter.  Grub will be installed on the floppy.  When you are taken to the next screen, tab to "Go Back" and repeat the Grub installation step, except taking the MBR default.

You will then proceed through the installation until you are instructed to remove the CD and floppy, and to reboot.  If all went well, there will be a menu and you will choose the first selection.  If grub doesn't boot properly, insert the floppy and reboot from it instead; we can resolve later whatever prevented the MBR boot.

One other dual-boot precaution:  It's a good idea to have available the media to restore the Windows MBR.  This can be an XP or W2K install CD, or a W98/ME/DOS bootable diskette (downloadable from bootdisk.com).  Or you can backup the one you have using a Linux Live-CD.

---

