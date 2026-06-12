---
title: "Installing Ubuntu on same harddrive as WindowsXP. Need to know how please!"
date: 2005-08-16
forum: Installation &amp; Upgrades
---

### Post by Solomon on 2005-08-16
Ok, I am really new to this whole Ubuntu-Linux craze I've heard so much about. I ordered the CD and it finally arrived today and given the fact that I have no patience left for Microsoft, I want to install Ubuntu. However, appearently... Dreamweaver and Adobe Photoshop... two programs I cant live without... Well means I have to keep Windows for those tasks.

I have one 40GB HDD (I know, it's horrible).

I have WindowsXP installed on it. What I need to do is install Ubuntu on the same harddrive so when I start my computer, I have the choice of loading Ubuntu or WindowsXP. Two seperate partitions if possible.

What I need is detailed steps on how to do this effectively and as easily as possible. Please, detailed steps only. I thank whomever helps me with this in advance. I am sure I'll have more questions as I learn this OS.  ;-)

---

### Post by GreyFox503 on 2005-08-16
Maybe I can help a little:

-Yes, you can install Ubuntu on the same drive while leaving Windows there.

-Ubuntu needs to be on a separate partition from your windows installation

-I believe the Ubuntu installer has the ability to resize NTFS partitions (that's your Windows one if you're using winXP)

-The Ubuntu installer can also install the GRUB bootloader which will let you choose which OS to boot into when you start your computer.

One important question is: How much free hard disk space do you have?  40GB is a limiting factor.

---

### Post by Blue1k on 2005-08-16
If you want a quick guide I can help. I have the same setup at home.

Step1: Install WinXP FIRST. In the XP installer create an NTFS partition about 15GB in size or so. Leave the rest as free space.

Step 2: Put in the Ubuntu disk. Boot into the install menu and when you get to the partitioning part choose "guided paritioning". In this submenu choose "install into largest free space". This will setup a swap and root partition. Make sure the boot flag is in the first partition (the windows one). You will know this because it will have a lightning bolt listed for that partition. (If you need a separate home partition) you will have to do an extra step.

Step 3: When the Ubuntu install asks where to load Grub install to MBR

And presto you are done. The grub menu will list WInXP and Ubuntu. 

Cheers,
Karl

---

### Post by Buffalo Soldier on 2005-08-16
[QUOTE=Solomon]Ok, I am really new to this whole Ubuntu-Linux craze I've heard so much about. I ordered the CD and it finally arrived today and given the fact that I have no patience left for Microsoft, I want to install Ubuntu. However, appearently... Dreamweaver and Adobe Photoshop... two programs I cant live without... Well means I have to keep Windows for those tasks.

I have one 40GB HDD (I know, it's horrible).

I have WindowsXP installed on it. What I need to do is install Ubuntu on the same harddrive so when I start my computer, I have the choice of loading Ubuntu or WindowsXP. Two seperate partitions if possible.

What I need is detailed steps on how to do this effectively and as easily as possible. Please, detailed steps only. I thank whomever helps me with this in advance. I am sure I'll have more questions as I learn this OS.  ;-)[/QUOTE]Welcome to Ubuntu and I do hope it will be a great introductory experience to the world of GNU/Linux.

Here are some sites that I think is important:[list]
[*] [Ubuntu User Documentation](https://wiki.ubuntu.com/UserDocumentation). With the specific page for [ installation](https://wiki.ubuntu.com/Installation/I386) and [re-partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning).
[*] [Un-official Ubuntu Guide](http://ubuntuguide.org/)
[/list]

---

### Post by Solomon on 2005-08-16
Ok, well.

I have WindowsxP already installed. I have approx. 30GB of free HDD space left. I want to partition that 30GB, leave 15 for WindowsXP and 15 for Ubuntu. What I need is a step-by-step instruction that I can follow. I have checked ot the Ubuntu CD and clicked F1 to avoid the "Default" install but at which point, I get really lost. Can someone provide me with a detailed Step-By-Step please?  :?

---

### Post by h4rdc0d3 on 2005-08-16
I would recommend installing WinXP first and have the Windows Installer create an NTFS partition ( C: ) less than 20GB and install WinXP there. Choose the size based on how many programs you're going to want to install in Windows. I would go with 15 to 20 GB if I'm going to install several large games. But, if you're not going to install many programs, you could get by on a 5GB partition for C:. Leave the rest unallocated.

**I know you didn't ask for this (and you can ignore it and just do 15GB per OS) but I still would recommend:**
Once inside WinXP, right click on "My Computer", select "Manage". The Computer Management window pops up. Under "Storage" select "Disk Management" and create a FAT32 partition. To judge the proper size take your 40 GB disk, subtract the size of your C: partition (we'll say 10GB) and subtract how much space you want for Ubuntu (again judging how much you need to install programs. Not many? Estimate around 5GB. Lots? Choose around 15GB. We'll say another 10GB for Ubuntu... that leaves about 20GB. So make your FAT32 partition 20GB and choose a label: Z:, X:, whatever you want. Now, the purpose of your FAT32 partition is to have a data partition in the middle of both OS's, that is easily accessible and where you can save all your files to. This could also enable quick recovery in the case you want or need to reload either or both OS's as you will just reload over each OS's main partition and leave your FAT32 one alone. [color=Red]However, just to be safe I would still recommend regular backing up of your FAT32 data partition to CD or DVD.[color=Black]

After that, pop in the Ubuntu Install disk, reboot and install to the free (unallocated) space which should be ~10GB (in this fictional scenario). Install GRUB to MBR and Ubuntu will automatically realize that you also have Windows installed and adds it to your GRUB list (/boot/grub/menu.lst). And that's it!

Good Luck!

Sorry, I forgot to mention that you'll want to edit your /etc/fstab to include your FAT32 partition, i.e. something like:[/color][/color]
```
/dev/hda2   /media/data   vfat   auto,user   0 0
```
'man mount' and 'man fstab' will help with the details.

Then do:
 ```
mkdir /media/data
mount -a
```

---

### Post by varunus on 2005-08-16
Little known fact about Ubuntu:

THE INSTALLER CAN RESIZE WINDOWS DRIVES.  Its much much MUCH easier than parititioning ahead of time, or reinstalling windows.

Just pop in the Ubuntu install CD, and follow these instructions (they have pictures too, to help you resize!):
[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

---

### Post by DancingSun on 2005-08-16
varanus has got it right.  I also used the Ubuntu installation CD to resize my Windows XP partition.  And it was really damn easy!  Just remember to choose the manual partitioning option when prompt!

I would go against using a FAT32 partition as the data partition as FAT32 are not journalized, therefore, can easily end up corrupted if you ever need to force rebooting the computer (which I had to do a couple of times in Ubuntu and XP).  The only reason that I would use FAT32 would be to use it as a space to transfer files from Ubuntu to XP, and vice versa.  This is because Ubuntu, by default installation, cannot write to a NTFS partition, and XP cannot write to a Linux partition.  However, both OSes can write to the FAT32 partition.  So sometime it may come in handy.

But if you're not going to be messing around with your OSes too much, just go with the "auto-allocate" for the Ubuntu partitions.

---

### Post by h4rdc0d3 on 2005-08-16
> FAT32 are not journalized ... can easily end up corrupted

Good point. It works for me though.

---

### Post by Solomon on 2005-08-16
So let me see if I fully understand you folks...

I need to completely reformat my drive and re-install WindowsXP on a partitioned section of my 40GB Harddrive. Once I re-install WindowsXP on that partition (15GB Partition), I then need to insert the Ubuntu installation disks and install it one the other 15GB partition. Correct?

Above I see that it is possible for the Ubuntu install disk to partition a drive that already has WindowsXP Professional installed. However, that leaves me really lost. See, I am scared that when I try to install this OS, I'll accidently erase all of my currently installed programs (IE: Photoshop CS, Dreamweaver MX04, Chessmaster Pro).

So once I insert the Ubuntu install disk, do I hit enter for the "default" installation? What I need from you guys is a walk-through of each screen, where to click, what to click, what to change, change to what. I know you guys are really trying to help here and some of what you've said has indeed made sense to me but realize... I've been a Windows user for many, many years and am finally ready to switch but am dumb-founded by some of these things.  ](*,)

---

### Post by varunus on 2005-08-16
Ubuntu can repartition XP partitions without data loss.  That's what the guide I posted above lets you do.  So, if you want even more step by step:

1.  Insert the install CD.  Reboot and boot from CD.
2.  Press enter at the boot prompt, no special options needed.
3.  Choose your language, keyboard layout, etc.
4.  Ubuntu may go through some network config, you can do it here, or skip it if you don't understand and do it later.
5.  When it asks you about partitioning, choose MANUAL PARTITION.
6.  Follow this guide: [http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)
This will guide you through shrinking your XP partition and creating a new one for Ubuntu with NO DATA LOSS.   :) 
7.  Continue the rest of the install, fairly easy (create a user, set the password, reboot)

If you do this, this will shrink your XP partition (no reinstall needed, no data loss).

However, if something goes wrong (power failure, you type the wrong option, freaky random error) there is a chance that you'll lose all of your data.  So I would back up anything super-essential...

But I've done this on 3 computers now, and no problems.

---

### Post by Solomon on 2005-08-16
Thank you Varunus for your replies. You've made more sense than half of the people who have replied thus far. I truely thank you. I'm going to give this a shot and I'll let you guys know how it turns out. Thank you again.  :)

---

### Post by GreyFox503 on 2005-08-16
Ok, so you have 40GB total, with Windows only using about 10, leaving 30 free.  That's good since you have a lot of space to work with.

I don't know which one you plan on using more, but something easy would be just to do a 50/50 split where winXP and Ubuntu each have 20GB.  This will still leave around 10GB free on your winXP partition.

Before you start the install I would go into Windows and defrag the drive a couple times to move all the data together.

Most of the install is really easy and straightforward, just read the prompts and use defaults if you're not sure.  Of course except in the partitioning part!

Choose manual partitioning, and then tell the partitioner to shrink the NTFS partition to whatever you want (eg. 20 GB)

Then you have approx. 20GB of just free space.  I would recommend letting it auto-partition the rest, which will make a / partition and a swap partition I believe.

EDIT:  I just looked at these screenshots : [http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

and that looks almost exactly like what you need to do.  One thing I would like to add is that, in the example, when asked for the new partition size the guy put in 70%.  That's Ok, but if you don't want to do the math, you can just enter the size you want, literally "25GB" would resize the NTFS partition to 25GB or whatever.  And then he goes on to do the auto-partitioning of the free space, which I recommend.

Don't forget to defrag Windows first.

---

### Post by redfox on 2005-08-16
What would be recommended for 7 GBs of free space for Ubuntu?

Also, how many boot flags should be assigned during install?  Just one, or one for Ubuntu and XP?

---

### Post by Hobbsee on 2005-08-18
[QUOTE=redfox]Also, how many boot flags should be assigned during install?  Just one, or one for Ubuntu and XP?[/QUOTE]

There's only one boot flag - so if you say you want the windows partition to have a boot flag, and then the / partition to have the boot flag, the boot flag will switch from the windows partition to the / partition, as the / one was the last selected.  

On installing - it is possible to screw it up - I've done it.  If you arent absolutely sure that what you're trying looks right, dont write it, come back to windows, and get some more help - there's nothing worse than going "oh no, it's screwed up, and i've just deleted windows, what do i do now?"

---

### Post by GreyFox503 on 2005-08-18
I don't know how to respond about boot flags.  I'm a new linux user, so I ignored them completely and it turned out fine.  I could dual-boot immediately after installing.

---

