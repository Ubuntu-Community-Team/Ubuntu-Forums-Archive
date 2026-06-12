---
title: "Dual booting.  Can't quite find the right answer"
date: 2005-11-21
forum: Installation &amp; Upgrades
---

### Post by new2linux9 on 2005-11-21
Hello everybody or anybody, 

after trying out ubuntu for a week, seeing all the support and of course the excelIent idea of Linux i.e. It's not just about money, the software does usefull things, no viruses (hardly), no spyware, no adware.  I could go on,  I have decided to use it as my main OS.  However after a few days of research, I still can't find the exact answers I'm lookng for.

I want to dual boot ubuntu breezy badger 5.10 with Win XP, with the intention of eventually wiping off WinXP.  I have read about setting up the different partitions, and understand about creating a SWAP partition, I think.:???:  (I am new to Linux), but none of the information I have found answers all my questions.  

I have an ASUS M5N with 60GB and 512MB RAM. currently runnng Win XP SP2, but this doesn't matter (I think), as I have backed up my files and want to start from scratch.  That is re-format my hard drive (too much crap, useless software, spyware etc,etc).
 
Questions:
1.  Bearing in mind I only want to boot into WinXP occasionally and will mainly be using Ubuntu, what is the minimum size partition I can give Windows - I have read differences between 5.4-10GB?  Space is a factor, as I only have 60GB.

2.  If I set the WinXP partition as NTFS, once I have finally rid myself of WinXP and want to get rid of it, will I be  able to remove all traces of it or will parts be lurking about especially as I want to set up a partition that both OS's can use (FAT32?)?

3.  How much space (GB's), do I give the Ubuntu (Linux OS) partition, bearing in mind that hopefully afterwards it will be my only OS?  Do I give more to this partition or to the OS Share partition?  I don't understand if files e.g. pictures, music, basically any files that aren't the OS, like other software programs will be better stored here (ie faster to acces, less problems or in the Linux OS Shared partition.  I don't want to set up everything now, only to have to re-do everything once I am finally rid of Windows!

4.  What is the best filesystem type, FAT32, ext2, ext3, again bearing in mind that afterwards I want to get rid of XP but for the moment want to be able to use both?
Can I change this after?

5.  Do I really have to give as mush as 1GB (roughly twice my RAM) for a SWAP file?  If I do, can I store anything on it or is it just there to keep Linux happy?  I don't understand the SWAP partition.:confused: 

6.  Is it okay to install GRUB in the MBR?  I have read conflicting reports, but mind you, this was written in regards to Hoary Hedgehog:
Quote from
[http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/)

"Continue in the Ubuntu install process until you get to the part about GRUB. DO NOT INSTALL GRUB in the Master Boot Record (MBR)! If you install GRUB in the MBR, all bets are off...you're on your own. It will request that GRUB be installed in a bootable partition, so you can use your Linux partition (this is why making it primary and bootable was important). If your Linux partition is the second partition on your first hard drive (if you have multiple hard drives), you will use the GRUB code (hd0,1). The "0" immediately after "hd" indicates the first hard drive (counting starts at zero instead of one). The "1" after the comma indicates the second primary partition (again, counting starts at zero instead of one). If your Linux partition is on another hard drive or some primary partition other than the second one, change the GRUB code accordingly."

This explanation then goes onto say that you will get an error message stating "Operating System Missing" and then tells you to put the rescue disk in and do more actions including activating the Windows partition using QTParted and eventually has you editing windows Boot ini. files. 

Please can someone let me know, is it really this complicated?!

Yet my own install just letting Ubuntu do everything as default seems fine.  I'm assuming it installed GRUB in the MBR, mind you, I have to admit I wasn't really paying attention.  Being a Windows user I have become a bit brain dead with regards to computers, I just pressed enter and selected yes when it suggested so.

7.  Last question, not sure if it should be listed here but is important, even though it might sound stupid to some.  If I have a virus on Windows that is on a file I access using ubuntu, could it transfer?  

Sorry, the questions are so many, and maybe I am missing things and giving too much waffle, but please bare with me as this is the first time I have ever written into a forum.  

Please help me rid myself of Windows, but as I said, not just yet.  Thanking anybody profusely, who has the time to read this and help me out. :D

---

### Post by pyronicte on 2005-11-21
Actually I have installed XP & Ubuntu. The first one just for games, and second one as main OS. I have a hard disk with 120 GB and find over there a hard disk with 4 GB. In order to do the installation, I decided to leave the little 4GB for Ubuntu and the biggest for Windows because the games eats a lot of space. Whe I put the Ubuntu cd, it asked me for which hard disk to use. That's all, it install at its own the multiboot.

---

### Post by yesplease on 2005-11-21
I can answer several of your questions at once: when you make a dual boot install of  XP and Ubuntu, it is because you can continu to use XP. To use XP you need a lot of space for it, I would use 30 GB because I do games on XP. Do not use just 2 or 4 GB for XP.

Do not uninstall XP, but resize the partition during install of ubuntu. Defragment XP first and check how much space is left.

Use ext3 for ubuntu: 5GB / (root), 1 GB swap, and the rest /home for instance 25GB. Make the FAT partition later , and yes you can remove the XP partition completely in a later stage.. You cant put files on swap.Next to  the RAM memory, swap is used to store things temporarely.  Change to less than 1GB swap later if you know that you can. 

Dont worry about windows virusses on ubuntu, unless they are boot virusses.

There is an installation manual on the install disk and ofcourse the ubuntuguide. [http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html) Good luck.

One more thing: if you decide to install XP again anyway, install it first (before windows). Yes, you can install Grub on the mbr without problems.

---

### Post by Herman on 2005-11-21
Re installing GRUB to MBR:
To my way of thinking, it doesn't make sense to fix a problem unless you have a problem to fix. If you just do everything the easy way and install GRUB to your MBR like you are supposed to, everything will probably be okay. 
Installing Ubuntu is nice and simple, there is nothing complicated about it.
I drive a car and I might get a flat tire some day. That's a risk I take, and a flat tire can be repaired. Most of the time, I don't get a flat tire. Tires are fairly reliable, but they can go flat sometimes. When I buy a new tire I don't get them to patch it for me  ahead of time because I am afraid it might go flat someday.  That would just be extra work for nothing, and it would be silly!:D 
If you just install GRUB to your MBR, probably it will be okay, just like your car tires. If it has a problem, then fix it when it is a problem. It doesn't make any sense to go to a lot of work in advance because you are scared there could be a problem. It's silly. ;) 
(Herman).

---

### Post by new2linux9 on 2005-11-22
Wow, thank you all very much for your advice especially as it was so fast.  This has further enforced my faith and belief in Ubuntu - the forums.

"Yesplease" you did infact answer most of my questions in a lot easier direct way than it took me to ask.  Thank you.:D 

"Herman", your link is excellent, [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/).  I wish I had come across it before.  I heartily recommend it to anyone doing a dual boot with WinXP.   

I have just a few more questions.

As I have decided to re-install WinXP using the FAT32 filesystem, bearing in mind my specs (60GB) and that I only want to keep WinXP for playing Lord Of The Rings, or CS or UT2004, not all at once mind, do you think it is better if I create a seperate partition between the WinXP OS and where I will save my other software eg games and other shared files or should I just leave it as one?  I am leaning towards creating a seperate partition so that when I do eventually get rid of WinXP I can easily format it and make sure all traces are gone.

Any idea what size?

If I install files on FAT32 and not ext3, what will I be losing out on? 

Again, thank you very much.

---

### Post by yesplease on 2005-11-22
I see what you mean: you want the FAT32 partition to share flles and to migrate files when you eventually get rid of winXP.

There is a curious bug with FAT32, [http://ubuntuforums.org/showthread.php?t=89992](http://ubuntuforums.org/showthread.php?t=89992),  However it is possible that this does not apply to your situation. So try it, basic install does not take much time. 

You can put winxp on 25GB ntfs and then install ubuntu on 25GB ext3, while you leave 10 GB free (unpartitioned). Format the 10 GB later as FAT.

However, consider this: you can exchange files between ntfs and ext3. That is read-only, from windows, or from ubuntu. But that is sufficient for exchanging.

Most important, you wont get rid of windows quickly, because you want to play games, and because you will benefit from a familiar OS next to ubuntu. So, there is no need to plan for this option in the forseeable future.

---

### Post by new2linux9 on 2005-11-23
Hello yesplease, again thank you very much for your advice.  What I have decided to do after reading about the differences between NTFS and FAT32 (they're not great differences) is not use NTFS just have 25GB FAT32 and 35GB ext3.  That way I'll be able to read and edit all my files from Ubuntu easily (I hope), unless there's something I'm missing.

---

### Post by new2linux9 on 2005-11-23
I obviously hadn't looked hard enough.  I have now found out that you can't store files larger than 4GB's on FAT32!  So yesplease, I'm going to take your suggestion but will reduce the NTFS to 20GB.  Partitions:  20GB NTFS WinXP,
                                                                         30GB ext3 Ubuntu
                                                                         10GB FAT32 OS Share  

Thanks again.

---

### Post by new2linux9 on 2005-11-23
I obviously hadn't looked hard enough.  I have now found out that you can't store files larger than 4GB's on FAT32!  So yesplease, I'm going to take your suggestion but will reduce the NTFS to 20GB.  Partitions:  20GB NTFS WinXP,
                                                                         30GB ext3 Ubuntu
                                                                         10GB FAT32 OS Share  

Thanks again.

---

### Post by new2linux9 on 2005-11-25
I have now set up my dual boot system:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/hda2            2433        5958    28322595   83  Linux
/dev/hda3            5959        6043      682762+   5  Extended
/dev/hda4            6044        7296    10064722+  83  Linux
/dev/hda5            5959        6043      682731   82  Linux swap / Solaris

However although everything now looks okay, apart from having trouble getting access to my windows NTFS folder, during install at 83% I got the following error message:

[4295351.0640000] NTFS - fs error (device hda1):ntfs_ucstonls():Unicode name contains characters that cannot be converted to charcter set cp437.

The install carried on and I am now using my computer with no apparent
problems.

Can anyone tell me what this means and what I should do about it?

I am currently researching about my windows partition problem.  I will post again if not successfull.

Thank you

---

### Post by yesplease on 2005-11-25
Nice to hear that there are no major problems after install.

The error message means somthing like: there where some non-standard characters used, so they cant be converted to another character set.

A lot of messages are generated (during boot up or install), many of them are just notifications.

When there are no problems, I would not worry about it. I hope someone else can help  you better with this one.

Do you still have problems accessing the NTFS partition?

---

### Post by new2linux9 on 2005-11-27
Yes, I think :confused: .  After letting a friend, who is currently using Hoary do some things.  He changed the /etc/fstab from (what I think was the origional):

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /windows        ntfs    default        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

to:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /windows        ntfs    [COLOR="Red"]ro,user[/COLOR]       0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

and doing some other things, including mount -a, umount -a?  I have to admit I did try to follow, but once he actually got my windows file loaded I forgot what he did and although I took a copy of some of the things he / I did, when I went to do it again after shutting down, it didn't seem to work.  Well, it mounted, but I couldn't access it.  So, I reverted my /etc/fstab file back to the origional (I think), trying ubuntu's guide again, adding the line which I hasten to add before my friend fiddled (technical term) didn't seem to work (however, it is possible I typed something incorrectly or missed a space):

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /windows        ntfs    [COLOR="Red"]default[/COLOR]        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
[COLOR="Red"]/dev/hda1       /windows        ntfs    umask=0222        0        0[/COLOR]

Now during boot up, I get a "failed" message next to "mounting local file systems" and although the Windows drive doesn't show up on the desktop anymore (it did when my friend changed the /etc/fstab/ from "default" to "ro,user"; it is in the file system and is accesible, however it is showing the GB's as 14.2GB free and 4.6GB used, making a total of 18.8GB.  What happened to 1.2GB.  I formatted it at 20GB NTFS:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/hda2            2433        5958    28322595   83  Linux
/dev/hda3            5959        6043      682762+   5  Extended
/dev/hda4            6044        7296    10064722+  83  Linux
/dev/hda5            5959        6043      682731   82  Linux swap / Solaris

To sum up.

Questions:
1.  How do I get rid of the failed message during reboot, well not got rid of it, by just stopping it displaying, but by solving the problem?

2.  Why is my windows folder only showing as 18.8GB's in total when it should be 20GB's?  I can accept a few MB's out, but 1.2GB's!:???: 

3.  I have a media folder in the file system showing as 23.3GB's inside of which is another "windows" folder as well as cdrom and cdrom0 folders, each with nothing in them.  Is this windows folder anything to do with my WinXp "windows" folder or is it something to do with the /media/windows/ directory I created when following ubuntu's guide to Window Partitions:

sudo mkdir /media/windows, 

which I am assuming I am not using as my windows location is /windows, not media/windows, I think:???: , and , where does the 23.3GB's come from?

4.  How can I change my windows location to "/media/windows", as this seems to be the one in all the instructions, (mind you, I am finding out more about linux this way than just following paste and cut instructions), so change this question to "Why should I..." i.e. what are the advantages of having it in a "/media/windows" directory, as apposed to just a "/windows" directory?

5.  What is the difference between having the windows drive on the desktop as it was when my friend changed my /etc/fstab from "default" to "ro, user" /dev/hda1       /windows        ntfs    [COLOR="Red"]ro,user[/COLOR]       0       0 or as a folder in the file system as it is now after adding the "/dev/hda1       /windows        ntfs    umask=0222        0        0"?

Again, thank you anyone who can answer any of my questions.  I have included all the information I could find about my set up and will gladly give anymore information if required and if explained as to how I can find it out.

---

### Post by yesplease on 2005-11-27
I understand that you /etc/fstab is now:
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 /windows ntfs default 0 0
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda1 /windows ntfs umask=0222 0 0

I see the entry /dev/hda1 /windows   ** twice**. I think 1 is enough because you have only 1 hda1.

In my fstab I have:
# <file system> <mount point>   <type>  <options>       <dump> <pass>
/dev/sda1       /media/sda1     ntfs    nls=utf8,umask=0222 0       0

where the option nls=utf8,umask=0222 is readonly for ntfs, and the mount point is /media/sda1
In the places menu I find partition sda1 in /media/sda1.   (Note that sda=sata)

So, I think that in your fstab you can make /media/windows as your mount point. If that works, the partition hda1, with the alias 'windows' will be mounted and found under /media/windows. If there is no windows folder under media, make one first.

Try this first and if you still have problems post the fstab and the question.

---

### Post by new2linux9 on 2005-11-27
Thank you so much for your prompt reply again yesplease.

Yes, this is my current fstab, I don't why there are two /dev/hda1 entries, and I don't know how to delete one.  I have only been using Linux for one week. 
Would you mind telling me how to make /media/windows my mount point, and what that means.  

Also I think there is a windows folder under media:

> 3. I have a media folder in the file system showing as 23.3GB's inside of which is another "windows" folder as well as cdrom and cdrom0 folders, each with nothing in them. Is this windows folder anything to do with my WinXp "windows" folder or is it something to do with the /media/windows/ directory I created when following ubuntu's guide to Window Partitions:

sudo mkdir /media/windows,

which I am assuming I am not using as my windows location is /windows, not media/windows, I think , and , where does the 23.3GB's come from?

Thanks again.

---

### Post by new2linux9 on 2005-11-27
Sorry, I do know how to delete one:

sudo gedit etc/fstab

But which one?  Should I just amend this /dev/hda1 /windows ntfs default 0 0 to this /dev/hda1 /windows ntfs umask=0222 0 0?

But in ubuntu help, it says to append /dev/hda1 /windows ntfs umask=0222 0 0 to the end of the file.

From Ubuntu FAQ guide:

> 3.&#8195; How do I mount Windows partitions (NTFS) on boot-up, and allow all users to read only?

    Assuming that /dev/hda1 is the location of the Windows partition (NTFS) and the local mount folder is: /media/windows

       1. Read How do I check disk space and view the partition table?
       2.

								sudo mkdir /media/windows 
								sudo cp /etc/fstab /etc/fstab_backup 
								sudo gedit /etc/fstab

       3. Append the following line at the end of file

/dev/hda1 /media/windows ntfs umask=0222 0 0

---

### Post by yesplease on 2005-11-27
OK, 

If you havent got one, first make a /media/windows folder with

sudo mkdir /media/windows 

delete both lines for hda1 in fstab with
sudo gedit /etc/fstab

and add

/dev/hda1 /media/windows ntfs umask=0222 0 0

Copy this line from the manual (it is important to get the spaces right).

Post your fstab when this doesnt work.

---

### Post by new2linux9 on 2005-11-27
Excellent, I now have my windows drive mounted on the desktop and in the media folder and no error message.:D 

I believe before I created an extra "windows" directory which is showing in the file system after the "var" folder which I do not need.  I have checked the properties it says Type: Folder, 
                        Contents: nothing
                        Location: /
                        Volume: Root Volume
                        Free space: 23.3GB
                        Modified:Fri 25 Nov 2005 04:28:03 AM CST

Can I delete it?

---

### Post by yesplease on 2005-11-27
I am glad it worked. 

Strange folder, leave it there for a while, I dont know what it means. Delete it later when you are sure.

I have some stuff for you to browse (and read when youfeel like it):

This starter guide is for breezy 5.10: [http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)

It is from the Ubuntu documentation project. You will like it. (the unofficial guide is for hoary).

You probably have seen this: [http://www.ubuntuforums.org/forumdisplay.php?f=100](http://www.ubuntuforums.org/forumdisplay.php?f=100) it contains many good howtos, fro instance for the drivers of your video card.

Reading this may also help: [http://www.tuxfiles.org/](http://www.tuxfiles.org/) , a well written practical introduction.

Ofcourse there is the Wiki: [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

This doesnt mean that you cant ask questions ofcourse :)

---

### Post by new2linux9 on 2005-11-27
Thank you very much for all your help.  I am now even more committed to becoming a full blown linux convert.:D

---

