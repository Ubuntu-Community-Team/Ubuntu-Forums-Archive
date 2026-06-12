---
title: "Wanting to install and dual boot...."
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by condawg on 2007-09-03
Hiya.
I have a disk of Ubuntu 7.04 sitting right here, and I want to dual boot with it.
The only hesitation I have is that last time something went wrong with the partitioning and I lost my Windows... Had to format and reinstall.
So I was wondering if someone could link me to a good partitioner that I can run in Windows, and then install Ubuntu to the partition I create.
I am also wondering this...
When I install Ubuntu on that other partition, does GRUB automatically take place?

Also, is there any way for me to get files from windows into ubuntu without putting them there?
Like...
Is there a way to be on Ubuntu, but to play music that's on my Windows partition?

Thanks for all your help!

---

### Post by wolfen69 on 2007-09-03
try this for partitioning: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) 
yes, it will automatically install grub.
once in ubuntu,
```
sudo apt-get install ntfs-config
```
it will show up in applications>system tools. you will use this to read/write to your windows partition.
yes, you will be able to play music from windows.

---

### Post by cosborn72 on 2007-09-03
If you install ubuntu off the live CD, it should automatically identify your windows partition, allocate space for your linux partitions and partition it for you.   Then it should install GRUB and add the windows partition to the menu.lst.


This is by far the easiest way to do it.  What went wrong the last time you tried it?  Did you get any error messages?  What do you mean by 'lost your windows partition"?


What version of Ubuntu did you try to install last time? Feisty brought significant improvements to the installer/partitioning process.  I think it even installs ntfs-g3 by default, giving you access to windows partitions.  (Although you may have to tweak it if you want to have rw access.)

---

### Post by merlinus on 2007-09-03
ntfs-3g needs to be installed separately.

Best way is this:

Open a terminal and enter:

```

sudo apt-get install ntfs-config

```

then:

```

sudo ntfs-config

```

Tick the appropriate boxes and restart.

-merlin

---

### Post by condawg on 2007-09-03
> **merlinus said:**
> ntfs-3g needs to be installed separately.



What's ntfs-3g?

---

### Post by cosborn72 on 2007-09-03
Linux can access windows partitions that are formated using FAT, but Windows XP usually installs using NTFS which linux can't access by default.  

NTFS-config allows you to access NTFS file systems.  Of course, if your windows drive is formated using FAT, you don't need it.

You can also access your linux system through windows using a program call ext2-ifs [http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by merlinus on 2007-09-03
The drivers that allow ubuntu to write to NTFS partitions, e.g. windows.

-merlin

---

### Post by condawg on 2007-09-03
Oh, okay.
Thanks :)
That's really helpful to know.

Just a quick question -- about how big do you think I should make my Ubuntu partition?
EDIT: Forgot to include -- My hard drive is a 160 gb with 98.5 gb left... I just got it last week or two weeks ago because my old one broke, and I'm always torrenting, so I need quite a bit of space for my Windows partition.

---

### Post by merlinus on 2007-09-03
How much free space do you have? If you have enough, you may wish to create a separate /home partition, which is where preferences, configurations, bookmarks, email and such live.

Then when reinstalling, that partition will not be touched, as long as you do not format it.

-merlin

---

### Post by condawg on 2007-09-03
> **merlinus said:**
> How much free space do you have? If you have enough, you may wish to create a separate /home partition, which is where preferences, configurations, bookmarks, email and such live.

Then when reinstalling, that partition will not be touched, as long as you do not format it.

-merlin
I have 98.5 gb left...
But just a quick question.
I was looking through an install guide and came across this image.

[img]https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=6.png[/img]

I was wondering -- when at this stage, are you choosing how much space to give Linux, or are you resizing your current partition (for instance, if I put it on 25gb, would I then have 25gb for my windows partition or ubuntu)?

---

### Post by merlinus on 2007-09-03
You would have 25G for windows.  The new partition size refers to hda1, which is where your windows install lives.

Note:  If you are running vista, you need to use its disk manager to shrink the partition.  Otherwise ubuntu will not install correctly.

And in any event, before attempting ubuntu install, delete temp and other unneeded files, backup data, set virtual paging to zero (set it back after install), and defrag several times.

-merlin

---

### Post by condawg on 2007-09-03
> **merlinus said:**
> You would have 25G for windows.  The new partition size refers to hda1, which is where your windows install lives.

Note:  If you are running vista, you need to use its disk manager to shrink the partition.  Otherwise ubuntu will not install correctly.

And in any event, before attempting ubuntu install, delete temp and other unneeded files, backup data, set virtual paging to zero (set it back after install), and defrag several times.

-merlin
Awesome. Thanks =)

Anyhoo, I've just completed 4 defragmentations... going pretty fast for some reason. They used to take like, 2 hours, now they're taking like, 10 minutes.
I'll backup alot of my **** on a DVD-R before attempting an install, and delete all unneeded files :) thanks
What's virtual paging?

---

### Post by merlinus on 2007-09-03
Virtual paging has to do with multi-tasking, so each app thinks it is running on its own machine.

This usually, however, results in a large block of system files near the end of the windows partition, so you cannot shrink it as much as if it is not there.

It usually shows up in the defrag window as a large green rectangle near the end of the window.

You might find it listed in System Tools.

-merlin

---

### Post by condawg on 2007-09-03
> **merlinus said:**
> Virtual paging has to do with multi-tasking, so each app thinks it is running on its own machine.

This usually, however, results in a large block of system files near the end of the windows partition, so you cannot shrink it as much as if it is not there.

It usually shows up in the defrag window as a large green rectangle near the end of the window.

You might find it listed in System Tools.

-merlin
Ah. Okay, thanks :)

---

