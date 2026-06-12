---
title: "How to format the hard drive and Re-Install"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by Nbala on 2010-06-23
Hi! I'm semi-new to Ubuntu- but I *do* know my way around the terminal and general system procedures.

[CENTER][FONT=Century Gothic][SIZE=3]**Here's the situation I need help with:**[/SIZE][/FONT]
[/CENTER]

[LIST=1]
[*]An upgrade %100 pwnd my system: I performed an upgrade to *Lucid* from *Karmic* and I lost my keyboard input and sound *etc* *etc* *etc*.  :mad:
[*]I then **made a Karmic boot-run/install CD, & a USB startup stick.**
[*]I then **backed up** my important information on flashdrives etc.
[*]At this point in time **I have  2 partitions** :?: one with my old user account & info on it, and the other as a new (re)installed Karmic partition.
[/LIST]
[CENTER][FONT=Century Gothic][SIZE=3][COLOR=Red]_**My question is:**_[/COLOR][/SIZE][/FONT][FONT=Century Gothic]
[/FONT] [/CENTER]
[FONT=Century Gothic][SIZE=3][COLOR=Blue][COLOR=Teal]What is the procedure for: [/COLOR] 
a)[I] **formatting the drive**,
[/I]b)[I] **not** keeping the 2 partitions, and 
[/I]c)* **re-installing Ubuntu** (karmic) back onto it?*[/COLOR][/SIZE][/FONT]

I have **GParted** ( but I can't see how to use it to ***format*** ), and *I have no clue* how to format the Drive from either within the GUI or at the command-line.

[LEFT][B][SIZE=4]How do I format & re-install Ubuntu?
[/SIZE][/B][SIZE=4]**What is the sequence or steps?**[/SIZE]

I can probably do the re-install intuitively but I'm concerned there may be Ubuntu tricks I don't know about! **Also- does this 2 partition thing cause any complications to formatting??**
So honestly ***my question is simply how to format the drive from within the system.***

Community, you have been **very** helpful in the past =D> and I am hoping someone will reply with the what to do. I thank you very much in advance ( I use this box for my online university program so its really important to me to clear this up! )

Thank you SO much! :-D
~Drew, aka Nbala
 [/LEFT]

---

### Post by dabl on 2010-06-23
1. (with some other computer) download the ISO and make a [[COLOR="Green"]**Parted Magic**[/COLOR]](http://partedmagic.com/download.html) Live CD.  Same rules as usual -- check the md5sum of the download, burn it as slow as you can.

2. Boot your Parted Magic Live CD.  When it is loaded and running, use the window/box in the upper right to select your hard drive.

3. Observing the two partitions in the graphical display, make sure they are not mounted (they shouldn't be), i.e. that there is no little padlock graphic on them.  If they are mounted, right-click on the graphic for each partition to unmount it.

4. Right click on each partition, and choose "Delete".  Then click the green "Apply" arrow on the top menu.  When it is done, you will have an empty hard drive with no partitions -- the graphic will show all the space as "unallocated".

5. Now you can right-click on the unallocated space graphic, choose "new", and add a partition, or (one at a time) multiple partitions.  Note that when you add them, you can choose the filesystem type, and that will make them formatted at the time they are created.  Again, once it is set up the way you want it, you click the green "Apply" to make it happen.

6. Before you're done, if you're planning to boot an OS on the first partition of this drive, it's a good idea to right-click the partition and choose "manage flags", and put a checkmark in the "boot" box -- it's not mandatory for all BIOS's (for Linux -- it is for Windows), but sometimes it makes the difference.

That's the basics.  Google can help you find lots more on partitioning if you need it.  Your minimum requirement is a swap space (1.5x RAM is good) and the balance of the drive can be for the OS.  Or you can make a swap partition, a 15G partition for the OS, and the rest of the drive can be a third partition on which you can mount /home when you install Ubuntu, using the Alternate Install CD and choosing "manual" partitioning.

Once you're finished with the Parted Magic session and partitioning, boot your Alternate Install Ubuntu CD and away you go!

---

### Post by Nbala on 2010-06-23
:) Ok thank you very much!- this is a very well explained procedure! :)
    My only hesitation is that *since I already have the iso on CD **and** an install USB*- 
_why cant I just *format then install?*_
    I **have** noticed that the partitions mount separately, *sometimes* requiring sudo but sometimes *not*. Is the issue: that the "mount status" of the partition would effect whether it was open/able to be formatted? 
If so, can I not just unmount both and format them? Is there an issue with formatting from **within** the Ubuntu OS? (or running cmd from an unmounted drive?) 
I am asking this because it seems like it would be much easier to just let the ubuntu CD format all from starting point and then copy my data back from USB.
[COLOR=Blue]
Again, **dabl** - seriously, thanks so much for your quick, intelligent and concise reply![/COLOR] :)
- Nbala/Drew

---

### Post by dabl on 2010-06-23
Ubuntu is set up, by design, to let you do all the partitioning and the formatting and the installation in a single session. However, for a lot folks, that is a bit too much complexity, especially when their hardware (or their plans) have "special needs".

My personal experience, supported by the zillion posts on this forum regarding installation problems, is that while it may _sound_ easier to do it that way, the reality is that it is actually _simpler_ to treat the partitioning problem as a separate process, in a separate booted session before you install, and then let the installation process be the one that you do with the Ubuntu CD.  For example, all the problems and questions surrounding "mounted or not mounted" will just disappear if you do it as I recommended.

So, I say "simple is better than easy".  :guitar:

---

### Post by Nbala on 2010-06-23
*Ok that's great- this makes sense to me procedurally*.=D>
Thanks, I get why that is a better way to go about it.  
So- I have the Ubuntu CD (& backups of my data) ready to go (eg. all set)- but from here I still have just a couple more questions and *you'll have straightened it out* **%100**:

[LIST]
[*]**How to I access the 'separate booted session' before I install? **( When I was trying to "save" my system after the *Lucid* upgrade damage, I set it to *automatically* log me in, so now I turn it on, and it takes me *right to the gnome  desktop* _without_ login other than network admin and other sudo situations) .
[*]**What is the correct 'interrupt-key' to launch the type of separate boot session you're talking about? **(eg. is it **F9** before the splash screen?- what is the exit-to-shell "hotkey" for this? *Unlessss*- alternatively: it may load to the OS choice screen ( version / recovery mode, etc ) if I do a hard reboot- would that be a good place to start?)
[*]**When I'm in the correct environment how to I 'treat the partitioning problem'?** What command sequence do I use ( I'm still new to Linux- grew up with Dos so cmdline is ok with me, but I don't know the linux terminal commands for this )?
[/LIST]
Ok! So _**there's the entire thing in a nutshell**_**.** You've really been a *great* help- if you can answer these 3 questions, or *even give a link* to these, you'll save my comp I need for work with autistic children and you'll totally get your good Samaritan badge! 
(j/k- I'd really appreciate it!)
Thanks dabl!  :smile:

---

### Post by dabl on 2010-06-23
> **Nbala said:**
> *Ok that's great- this makes sense to me procedurally*.=D>
Thanks, I get why that is a better way to go about it.  
So- I have the Ubuntu CD (& backups of my data) ready to go (eg. all set)- but from here I still have just a couple more questions and *you'll have straightened it out* **%100**:

[LIST]
[*]**How to I access the 'separate booted session' before I install? **( When I was trying to "save" my system after the *Lucid* upgrade damage, I set it to *automatically* log me in, so now I turn it on, and it takes me *right to the gnome  desktop* _without_ login other than network admin and other sudo situations) .[/list] 

Sorry, I probably do not understand the question.  You say you have backups of your data --- Good!  That is all you need.  Everything else on the hard disk is going to go "bye-bye".

You say you have "Ubuntu CD", but, is it the "Alternate Install"?  That is the one I recommend.  It does not use the Ubiquity installer, and therefore it does not have problems with SATA drives.  Also, the Alternate Install CD has more packages on the CD itself, so there is less need for packages coming through the ethernet from the repositories.


> [LIST]
[*]**What is the correct 'interrupt-key' to launch the type of separate boot session you're talking about? **(eg. is it **F9** before the splash screen?- what is the exit-to-shell "hotkey" for this? *Unlessss*- alternatively: it may load to the OS choice screen ( version / recovery mode, etc ) if I do a hard reboot- would that be a good place to start?)[/list]



Again, I'm not certain that I understand.  When I say "booted session", I mean the running Linux system that you have when you boot the Parted Magic Live CD, and also the running Linux system that you have when you boot the Ubuntu Alternate Install CD.  "booted session" just means "the system you are running after you booted a Linux CD".

> [LIST]
[*]**When I'm in the correct environment how to I 'treat the partitioning problem'?** What command sequence do I use ( I'm still new to Linux- grew up with Dos so cmdline is ok with me, but I don't know the linux terminal commands for this )?
[/LIST]

OK, when you boot the Parted Magic Live CD, it will start a Linux system and take you to a graphical desktop, then it will eject the CD and it runs 100% in memory.  On the desktop, you will see "Partitioner".  Just use your mouse and click that to start the partitioner.  Then follow my instruction above to choose your drive that you want to partition.

I hope this helps!  ):P

---

### Post by Nbala on 2010-06-23
Yep!:)
Got it- its all ok now- Ubuntu has the HD and its not fragmented into these residual partitions anymore.
Thanks for taking the time to break it down for me!!
~Nbala

---

