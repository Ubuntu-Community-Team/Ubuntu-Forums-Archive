---
title: "I need help getting started"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by DrCreosote on 2010-06-02
I am not new to Linux, but I've taken a vacation from it for 6 or 7 years as I teach college students how to use Windows and Windows software, such pursuits naturally drifted from my reality. Recently, my department chair asked me to take a class that has a Linux component and the current instructor is using Ubuntu. I would like to set up my system for dual boot, but rather than coming here for help fixing it later, I would like to set my system up right the first time. I need to know if it is easier to set it up on Windows 7 or Windows XP. I have two computers to choose from and I want to make it painless, though I would prefer it on the XP machine since that's the one I use for my classes. I've browsed this forum for instructions or articles on dual boot setups and found lots of information, but I feel the need for some baby step instruction. If anyone here could give me a good direction to go, I would sure appreciate it. 
 
I've experimented with Linux in the past and always liked the direction it was going, but it has changed drastically since I last tinkered with it. I've probably devolved into total noob territory, which isn't so bad because it is fun to explore. 
 
DC

---

### Post by darkod on 2010-06-02
If your windows partition(s) are taking the whole disk, you have to resize (shrink) to make space for ubuntu. Win7 has a built-in tool in Disk Management, XP doesn't. From that point of view it's easier on win7, because for XP you need to use third party software or Gparted from the ubuntu cd (which works just fine by the way).

Regardless whether using win7 Disk Management, or Gparted/other software for XP, shrink the windows partition first. Leave the created space as unallocated.
Reboot windows few times so it can do its disk checks. It is VERY picky about this. After windows is happy again, reboot with ubuntu cd, start the installer and in step 4 just use Use Largest Available Free space option. That will use the unallocated space you left for a standard root + swap setup.
Or use manual partitioning if preferred.

That's it, in short.
Some screenshots for 9.10 here, 10.04 is almost identical:
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

---

### Post by DrCreosote on 2010-06-02
Thank you, I'll get started on that process and let you know if I was able to pull it off. :)
 
DC

---

### Post by irv on 2010-06-02
> If your windows partition(s) are taking the whole disk, you have to resize (shrink) to make space for ubuntu. Win7 has a built-in tool in Disk Management, XP doesn't. From that point of view it's easier on win7, because for XP you need to use third party software or Gparted from the ubuntu cd (which works just fine by the way).

I disagree with this statement. (not that you can't use gparted, I do, but it is not necessary.) 
First, this past week I installed Ubuntu 10.04 on two PC's one with XP and the other with Win7. Both were very clean installs. Here is what you do: If you have XP or Win7 running on the PC and it is running good, just leave it alone. Next put the install CD in the CD player and boot from it. Chose the install and follow the steps. When you come to the part that ask if you would like to install side by side with XP or Win7, do so. It will automatically slice your hard drive into two partitions and install grub so you can choose either OS at boot time. The first time you run Windows it will do a check disk because your hard drive changed. This is normal. After that it will just go right into Windows. Every time you boot, it will have Ubuntu as the default OS, but you can change this if you like by editing your menu file. If you want to do this we can go into that later. 

[COLOR="Red"]One thing I would suggest you do.[/COLOR] Try the live CD and try the OS off the CD first to see if there is any issues. I did this and found my wifi card was not support in the install, but that was easy to fix with a third party driver I installed by hooking up a network cable to my laptop and within System> Administration >Hardware Drivers, I found the driver for it and I installed it and everything just worked.

Hope this helps.
Irv

---

### Post by new_tolinux on 2010-06-02
> **irv said:**
> I disagree with this statement. (not that you can't use gparted, I do, but it is not necessary.) 
I don't.
Although you _can_ use the installer like irv suggested, Windows 7 really doesn't like any other program messing around with it's partitions. Sometimes it all goes well, sometimes it goes terribly wrong.
That said: you should shrink your Windows 7 partition within Windows 7 as explained.
For XP it doesn't really matter that much which tool you use, besides, xp has no on-board partition tool that's capable of resizing existing partitions.

For grub/boot problems: both Windows XP and Windows 7 are recognized well by the Ubuntu installer. Windows 7 _will_ give you problems as it's a pre-installed system and there is no partition of ~100MB on the disk (the loader) -> been there, resulted in a lot of trouble getting things right again.


Then comes the most important question: hardware support.
As suggested you're best way of choosing a computer is through the live-CD.
Hardware is different for about every computer. Probably both computers do well with Ubuntu, but nobody can say that for sure without that being tested.
If the live-cd runs smoothly without any real problems, you can expect ubuntu to install without too much trouble. If the live-cd runs with nothing but trouble...... so will the install most likely cause you serious headache.

---

### Post by irv on 2010-06-02
> I don't.
Although you can use the installer like irv suggested, Windows 7 really doesn't like any other program messing around with it's partitions. Sometimes it all goes well, sometimes it goes terribly wrong.
The only reason I disagreed with you on this one point, is from experience. But I must admit, I only did one install with Win7 and it went perfect, no hiccups. Like I said when I started up Win7 for the first time it did a check disk and found no problems and went right into Win7 after that. Since I install both Win7 and Ubuntu I have use gparted to resize both Win7 and Ubuntu partitions. I sliced off a piece of both to make two more partitions for other reasons. here is a snapshot of my gparted screen.
[ATTACH]159130[/ATTACH]

---

### Post by arpanaut on 2010-06-02
Afew other hints:

Defrag your windows drives a couple of times before you resize.

Back up your important files that are on the partitions you are working on.

If you have a spare or secondary hard drive use that, makes things much simpler.

Good Luck!

---

