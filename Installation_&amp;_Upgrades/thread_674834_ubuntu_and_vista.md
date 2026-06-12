---
title: "ubuntu and vista"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by g0l3m on 2008-01-22
Hello all,

I have read a number of posts regarding vista & ubuntu...Some show encouraging results some don't ;-)

I've recently bought an acer 5920 laptop that comes with vista home premium pre-installed (i.e. I don't get installation disks...all I get is a recovery partition where all the drivers and other software lives).
I'd like to keep vista (for my games) but I need to setup ubuntu for my development.

Here comes the questions:

1) Is it safe to resize a vista partition with something like partitionmagic/acronis/gparted so that I can create some room for my ubuntu installation? (Sorry if this is slightly off topic but I'd like to hear from people that have successfully done it...Mine comes with Vista Home Premium in case it's relevant).

2) Will vista behave if grub goes and messes with MBR so that the laptop is dual boot? Again, have people successfully done it? Is there a risk that a vista update later on will go and mess up with the MBR and I will lose the ability to see my linux partition?

3) Is there a way to have the following configuration (instead of a dual boot):
    + If you boot with a floppy in the drive, the system starts ubuntu up
    + If you boot without the floppy in the drive, the system boots up to vista.

Going for (3) instead of (2) may be more wife-friendly, although I did get my missus to ditch
IE and Outlook for Firefox and Thunderbird ;-)

Thx in advance for any help,
g.

---

### Post by aashay on 2008-01-22
1) Yes. But doing so will cause the vista auto-repair thingy (via recovery partition) to stop working. So you'd be better off resizing some other partition
2) Yes. Even if it does not (for reasons beyond my understanding), you can always boot the ubuntu livecd and reinstall grub

---

### Post by Telescope_Nerd on 2008-01-22
Hi g013m
Like you I recently got a vista pre-installed laptop, with no disks and have been researching dual booting. Iam pretty much a n00b but I have found out a few things that might be usefull. Sorry if you know any of these already.

1) Vista allows you to burn a set of recovery disks once (and once only) I too have home premium and it fitted on a single dvd, this seems like a good first step incase things go really bad.

2) I don't know about partitioning the HD using any of the methods you mention sorry. But I have decided to make the partition using vista's own partitioning tool (pretty simple).

3) Yeah I have read a lot about vista/grub bootloader conflict. What I am planning on doing is installing grub on the ubuntu partition instead of the default location ( hd(0,0))) Then editing the vista bootloader to tell it to chainboot grub. I.e. give me the option of vista/linux at startup and if i specify linux go and find grub on the linux partition.
Vista has a command line program called BCDEdit for changing bootloader settings but this is too hard for me so I have downloaded some freeware caled easybcd which is a nice windowey mouse clicky front end for BCDedit.
This i hope will avoid the problems of grub overwriting vistas bootloader and vice versa.

4.)I don't know about booting using the cd sorry.

I am all set up to go now I have made my recovery disks partitioned my hd installed bcd edit and backed up my files. next time I get a free couble of hrs I am going to run the istallation. I'll let you know if it bombs!

---

### Post by ugm6hr on 2008-01-22
> **g0l3m said:**
> 1) Is it safe to resize a vista partition with something like partitionmagic/acronis/gparted so that I can create some room for my ubuntu installation? (Sorry if this is slightly off topic but I'd like to hear from people that have successfully done it...Mine comes with Vista Home Premium in case it's relevant).

2) Will vista behave if grub goes and messes with MBR so that the laptop is dual boot? Again, have people successfully done it? Is there a risk that a vista update later on will go and mess up with the MBR and I will lose the ability to see my linux partition?


1. Vista has a built-in resizing utility.  Use that (from within Vista).

2. You can either stick with Grub (which *shouldn't* have any problems, since updates don't interfere with MBR, or if you are concerned, install EasyBCD after installing Ubuntu.
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) 
How-to: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

3. Why not just have Vista as the default in whichever bootloader (EasyBCD or Grub) you decide to use, so that it will give you (for example) 3 seconds to select Ubuntu from the list, else it will just boot Vista.  Seems pretty "wife" friendly to me.

---

### Post by g0l3m on 2008-01-23
> **ugm6hr said:**
> 
1. Vista has a built-in resizing utility.  Use that (from within Vista).

2. You can either stick with Grub (which *shouldn't* have any problems, since updates don't interfere with MBR, or if you are concerned, install EasyBCD after installing Ubuntu.
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) 
How-to: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

3. Why not just have Vista as the default in whichever bootloader (EasyBCD or Grub) you decide to use, so that it will give you (for example) 3 seconds to select Ubuntu from the list, else it will just boot Vista.  Seems pretty "wife" friendly to me.


Thx for the replies guys...That EasyBCD wiki makes it look easy indeed, so I think I'll go for that. I prefer dual booting if I can control the boot loader from vista (since I'm only worried about vista updates messing the MBR up).

+ The wiki mentions to go for ReiserFS...I've always installed lin on ext3. What's the difference?
+ If I resize the vista partition in order to create room for my lin install, will vista handle the different FS on that partition ok? I.e. what's the chance the an intelligent automatic disk maintenance thing will go and screw my lin installation up?

cheers,
g.

---

### Post by ugm6hr on 2008-01-23
> **g0l3m said:**
> + The wiki mentions to go for ReiserFS...I've always installed lin on ext3. What's the difference?
+ If I resize the vista partition in order to create room for my lin install, will vista handle the different FS on that partition ok? I.e. what's the chance the an intelligent automatic disk maintenance thing will go and screw my lin installation up?


I use ext3 too.  I have no idea what the benefits of ReiserFS are.
Vista will not be able to "read" an ext3 partition (I don't think any of the ext Microsoft reading utilities works with Vista), so it will just ignore the Linux partition (essentially believing your HD is smaller than it actually is).  It should not interfere with it at all.

---

### Post by bwtranch on 2008-01-23
Hi Folks,

Just reading along and I found out something about ReiserFS today. It was developed by IBM and looks promising, but there is not enough data yet to see how reliable it is. So, I guess you could call it unstable, but, so far reports are good. Recommended is still use ext3. But, if you want to try it, well, it's up to you.

---

### Post by alainhenry on 2008-01-23
I just bought a HP6820s laptop with Vista pro, and want to shrink the Vista partition to install ubuntu Gutsy. Using the Vista own partition tool, I can reduce the main vista partition to 80 Gigabytes, buit not smaller.  I did it, Vista still works fine.  But I still have plenty of available space to Vista in the reduced partition, so I would guess it should be possible to reduce it even further, but the Vista partition utility won't let me. Any idea on how to achieve this ? 

Thanks

Alain

Edit: I have defragmented (once) the disk before shrinking the partition.  It did not change a thing.  I assume that, as the pc is straight from the factory, defragmenting won't change anything.

---

### Post by ugm6hr on 2008-01-23
> **alainhenry said:**
> I just bought a HP6820s laptop with Vista pro, and want to shrink the Vista partition to install ubuntu Gutsy. Using the Vista own partition tool, I can reduce the main vista partition to 80 Gigabytes, buit not smaller.  I did it, Vista still works fine.  But I still have plenty of available space to Vista in the reduced partition, so I would guess it should be possible to reduce it even further, but the Vista partition utility won't let me. Any idea on how to achieve this ? 


Which Vista version are you using?  Vista will not allow you to shrink below a certain size.  Although I thought it was about 26GB (for Home Basic anyway).

---

### Post by alainhenry on 2008-01-23
I am using Vista pro.  Do you want another information ?

---

### Post by g0l3m on 2008-01-23
> **alainhenry said:**
> I am using Vista pro.  Do you want another information ?

Erm...I may be wrong but there's no such thing as "Vista Pro"...The available flavours are:

Ultimate
Home Premium
Home Basic
Business
Enterprise

To my knowledge, most PC that you buy these days with Vista pre-installed come with home premium by default.

cheers,
g.

---

### Post by alainhenry on 2008-01-23
Sorry, it's the business one.

---

### Post by ugm6hr on 2008-01-23
> **alainhenry said:**
> Sorry, it's the business one.

It is entirely likely that 80G is as small as Vista Business can be installed on.  Try googling for it.

---

### Post by push_harder on 2008-01-23
Vista works fine with ubuntu installed on another partition, just a few tips:
Make sure you do a back up image of you're Vista drive.

Never ever uninstall ubuntu the lazy way through windows disk management or just plain formatting the partition, because this causes very, very bad problems that took me 2 days to recover from

And don't dick around with the root files of ubuntu unless you know what you're *really* doing.

GRUB Boot loader is easily confuseing and doesn't like Vista much.
Don't mess with it, just use the Boot loader normally.

Try not to hibernate you're computer, take USB sticks/CD's out when you turn you're computer on. GRUB doesn't like it too much.

And lastly, HAVE FUN

I can't really say i did because i spent 2 days trying to fix Vista after a bung uninstallation.

But don't worry, i was in a hell bad situation that's very rare.
And if you need any advice on the Vista side of things - PM me =]

---

### Post by articpenguin on 2008-01-23
> **bwtranch said:**
> Hi Folks,

Just reading along and I found out something about ReiserFS today. It was developed by IBM and looks promising, but there is not enough data yet to see how reliable it is. So, I guess you could call it unstable, but, so far reports are good. Recommended is still use ext3. But, if you want to try it, well, it's up to you.

IBM didnt develop reiserfs. reiserfs was made by hans reiser who is in jail for killing his wife. IBM made JFS.

---

### Post by Telescope_Nerd on 2008-01-24
> **Telescope_Nerd said:**
> Hi g013m
Like you I recently got a vista pre-installed laptop, with no disks and have been researching dual booting. Iam pretty much a n00b but I have found out a few things that might be usefull. Sorry if you know any of these already.

1) Vista allows you to burn a set of recovery disks once (and once only) I too have home premium and it fitted on a single dvd, this seems like a good first step incase things go really bad.

2) I don't know about partitioning the HD using any of the methods you mention sorry. But I have decided to make the partition using vista's own partitioning tool (pretty simple).

3) Yeah I have read a lot about vista/grub bootloader conflict. What I am planning on doing is installing grub on the ubuntu partition instead of the default location ( hd(0,0))) Then editing the vista bootloader to tell it to chainboot grub. I.e. give me the option of vista/linux at startup and if i specify linux go and find grub on the linux partition.
Vista has a command line program called BCDEdit for changing bootloader settings but this is too hard for me so I have downloaded some freeware caled easybcd which is a nice windowey mouse clicky front end for BCDedit.
This i hope will avoid the problems of grub overwriting vistas bootloader and vice versa.

4.)I don't know about booting using the cd sorry.

I am all set up to go now I have made my recovery disks partitioned my hd installed bcd edit and backed up my files. next time I get a free couble of hrs I am going to run the istallation. I'll let you know if it bombs!

Ahhhhhgh! It didn't work!   The best laid plans........
I followed the instructions on the easybcd website for manually configuring the partition and I tried to specify that I wanted grub installed on the partition using the advanced tab on step 7 of the setup. But then I get a fatal error message saying grub couldn't install. Where did I go wrong????!!!

---

### Post by Computer Guru on 2008-01-24
ReiseRFS is developed by Hans Reiser, who is under *suspicion* of murdering his wife. But Reiser's questionable legal status has no bearing no the quality of his filesystem.

We (NeoSmart Technologies) recommended ReiserFS because it's fast, stable, reliable, fragmentation-free, and out-performs anything else available for Linux on the home PC right now.

ReiserFS is **not** beta or untested (the new version, Reiser4 is though).

Feel free to use ext3 if you prefer, but there's nothing to lose and everything to gain by using ReiserFS instead.

As for Vista, the minimum partition size for the Vista installation partition is 20GB.

The GRUB error: I'm following up on that in your other thread.

---

### Post by lswest on 2008-01-24
i have an HP laptop with Vista Home Premium pre-installed, was able to create a recovery CD and i have a recovery partition on my laptop (the recovery CD basically lets you boot into the recovery partition, or restore that partition) and i install Ubuntu normally, set up / and swap, let it install. i have the entries for Ubuntu on my grub, plus Vista and my recovery partition.  runs like a charm.

---

### Post by Telescope_Nerd on 2008-01-24
Just to let you know:
Given the reiserfs vs ext3 discussion on this thread I tried changing from reiserfs to ext3 to see if would help me with my failed installation problem (posted above) and it worked! Yey!
So thanks everyone,
Reiser-0 ext3-1

---

### Post by articpenguin on 2008-01-24
> **Computer Guru said:**
> ReiseRFS is developed by Hans Reiser, who is under *suspicion* of murdering his wife. But Reiser's questionable legal status has no bearing no the quality of his filesystem.

We (NeoSmart Technologies) recommended ReiserFS because it's fast, stable, reliable, fragmentation-free, and out-performs anything else available for Linux on the home PC right now.

ReiserFS is **not** beta or untested (the new version, Reiser4 is though).

Feel free to use ext3 if you prefer, but there's nothing to lose and everything to gain by using ReiserFS instead.

As for Vista, the minimum partition size for the Vista installation partition is 20GB.

The GRUB error: I'm following up on that in your other thread.

1.Reiserfs isnt fragmentation free
2. reiserfs dosent outperform everything. JFS and XFS do far better on large files.

---

### Post by alainhenry on 2008-01-25
> **ugm6hr said:**
> It is entirely likely that 80G is as small as Vista Business can be installed on.  Try googling for it.
Vista business is indeed large.  I just discovered iot is because it has a lot of programmes, such as Office, preinstalled.  You only need a license key to activate it.  It is thus possible to save a lot of space by  uninstalling those program you will not use.

---

### Post by LordOfThePigs on 2008-01-25
The trick with shrinking partitions with windows vista is that the tool that comes with windows will not attempt to move file clusters. This means that if your drive happens to store a piece of the file at the end of the partition, you won't be able to shrink it. In order to be able to shrink your partition more, you must do the following things:

1. Disable hibernation
2. Disable System Restore
3. Disable the pagefile
4. Reboot
5. Download and install PerfectDisk
6. Do a smart placement defragmentation of the partition you want to shrink
7. Do an offline defragmentation of the partition you want to shrink (this will reboot)
8. Shink your partition (if you still can't shrink as much as you want, consider repeating steps 5 and 6)
9. Reenable Hibernation, System Restore and the pagefile
10. Install ubuntu :)

Disabling hibernation, pagefile and system restore, does 2 things: it frees up space on your HD, so defragmentation is faster (hibernation and pagefile will free up about the total size of your RAM each, and System Restore can free up to 15%), and it unlocks some system files that are otherwise unmovable, so the defragmenter can move all the files at the beginning of the partition.

This is quite a long procedure, but it is totally risk free, you can't screw up your vista install or lose data that way (as far as I know).

My favorite setup when setting up a dual boot computer is to have 1 partition for windows (+1 recover partition if it is a laptop. Never delete this one), and 3 partitions for linux (1 swap, 1 reiserfs as root, 1 ext3 as home). Having the ext3 partition as home in linux allows you to share files easily between windows and linux by mounting your home partition as another drive in windows ([http://www.fs-driver.org](http://www.fs-driver.org) a little bit of tinkering is required to get this to work under vista, but its not too hard).

And finally, don't worry about grub and the windows vista bootloader. Ubuntu Gutsy's installer will setup everything by itself, and it will work great. To make it wife friendly, just boot into linux yourself, and change the default grub setup. I personally use a 3 seconds timeout (default is 10 seconds), and keep Ubuntu as the default choice (but it is very easy for you to change the default to vista).

I have used this exact procedure with 2 laptops, one Fujitsu Amilo, and a Fujitsu U810.

---

### Post by r5ive on 2008-02-12
i have installed UBUNTU on a working Vista. unfortunately, i couldn't boot back to vista and all my files and work are there. can i recover my files from vista? and possibly boot to vista in a way? HELP!!!

---

### Post by Telescope_Nerd on 2008-02-12
Hi r5ive

Can you let us know what procedure you used for the install?? I can give you some info but will understand better what's wrong with more details..

Probably Ubuntu's bootloader (Grub) has overwitten vistas bootloader, i've heard of this happening sometimes. you can restore vistas bootloader using vista's recovery disks. This will wipe out grub so from boot you will go straight to vista.

Then I strongly suggest that you get easybcd and follow these instructions for installing Ubuntu:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

This gets around the problem that vista's bootloader doesn't play happily with grub. It worked for me and I now happily dualboot vista and Ubuntu no problems!

---

### Post by SteveHillier on 2008-02-12
> **alainhenry said:**
> I am using Vista pro.  Do you want another information ?

What is this version?  Here in the UK we get Vista Home Basic, Vista Home Premium, Vista Business and Vista Ultimate.

Oh isn't uniformity nice!!!!!!!!!!!!!!!!!!!

---

### Post by r5ive on 2008-02-13
> **Telescope_Nerd said:**
> Hi r5ive

Can you let us know what procedure you used for the install?? I can give you some info but will understand better what's wrong with more details..

Probably Ubuntu's bootloader (Grub) has overwitten vistas bootloader, i've heard of this happening sometimes. you can restore vistas bootloader using vista's recovery disks. This will wipe out grub so from boot you will go straight to vista.

Then I strongly suggest that you get easybcd and follow these instructions for installing Ubuntu:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

This gets around the problem that vista's bootloader doesn't play happily with grub. It worked for me and I now happily dualboot vista and Ubuntu no problems!

i intalled UBUNTU by ordinary installation. the first pick of the menu. i have 2 partitions and now i cant even get my backup partition to appear. is the things inside gone or what? 

i did the same installation method on a friend's Laptop and it works fine. both functions well. thinking it would be the same with my desktop, i just installed it right away without doing backups. and it turned out the other way. my Vista and backup partition are not to be seen anywhere.

tried to reformat using Vista (HOME) but only the custom method is available. that means clean format. yet, i couldnt format the file system to a Windows friendly File System. 

my last choice was using XP. it works, the c was formatted but my partition disc is still missing. Along with 39GB storage.

im all Blacked out!:confused::confused::confused:

---

### Post by Telescope_Nerd on 2008-02-13
Whoops, sound like it might be more serious than I first assumed. When you got to step 4 if the istallation  there were two or three choices:

Prepare Disk space

- Guided -use entire disk
- Use largest contiguous volume
- Manual

Which option did you choose here?

---

### Post by Kajong on 2008-02-13
I have vista regular and ubuntu gutsy gibbon and my vista didn't die :D

---

### Post by r5ive on 2008-02-13
> **Telescope_Nerd said:**
> Whoops, sound like it might be more serious than I first assumed. When you got to step 4 if the istallation  there were two or three choices:

Prepare Disk space

- Guided -use entire disk
- Use largest contiguous volume
- Manual

Which option did you choose here?

Yes it is. silly me picked all first choices of the setup which were the first things of every menu. si it means i used the whole disk right? but my hard drive have 2 partitions. C: and D:. does it affect both when i install using the first choice? i mean, whole disk right? does it mean whole C: partition or whole 80 GB?:confused:](*,)#-o

---

### Post by alainhenry on 2008-02-14
It's the business version, named "Professionel" in French. See a few messages above on this thread for some details.

> **SteveHillier said:**
> What is this version?  Here in the UK we get Vista Home Basic, Vista Home Premium, Vista Business and Vista Ultimate.

Oh isn't uniformity nice!!!!!!!!!!!!!!!!!!!

---

