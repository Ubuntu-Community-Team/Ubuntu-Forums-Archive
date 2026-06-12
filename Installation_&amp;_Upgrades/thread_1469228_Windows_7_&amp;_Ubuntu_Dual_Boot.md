---
title: "Windows 7 &amp; Ubuntu Dual Boot"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by cblah001 on 2010-05-02
Sorry if this is a repost in advance.
 
I am trying to dual boot both Windows 7 and Ubuntu. I want to partition my hard ddrive so that I can do this. I am getting a little sick and tired of Windows though my job requires me to have certain programs. Even though I think I can make these programs work with Ubuntu (Adobe CS4 Design Premium), I cannot afford even 1 day of having to troubleshoot any issues I may have. In effect, I plan on having one partition to use for work basically and one to use for personal use.
 
My problems:
 
1) I hear a lot about partitioning in different amounts for different operating systems and then partitioning for another drive for some other stuff... What should I really be doing?
 
2) What is the deal with Wubi? Supposedly I can dual boot without partitioning? Can I access the same files? Is this "really" using two different operating systems or is this a virtual version of Linux through Windows?
 
3) Does anyone know if using Ubuntu will reverse my "consider replacing your battery" and my computer shutting down every 20 minutes? *HP tech support had spent several long hours with me to determine that there is nothing wrong with my battery and that Windows 7 is creating this problem (computer is 10 months old and I know how batteries work).
 
Thank you so much for any help you can give me. I understand what patitioning is but everyone seems to have their own methods and opinions about every which way you can do it... I mainly want to be able to run both operating systems and access the same files (i.e. music files, video files, etc.) with each OS.
 
Thank you again.

---

### Post by Herman on 2010-05-02
> 1) I hear a lot about partitioning in different amounts for different operating systems and then partitioning for another drive for some other stuff... What should I really be doing? You just need a partition for Ubuntu plus a small swap area, but if you want you can have the swap in a file. That's what I do, so I only have one partition for most of my Ubuntu installations.
Some people like to divide their installations up into a lot of separate partitions, but I have never really gone in for that, they still need to keep backups of their files, so what's the point? It just makes things more complicated in opinion. 
The smallest you can install Ubuntu in would be about 4GB, but that wouldn't give you much room left over to add anything. 10 or 20 GB would be more reasonable. If you think you'll like Ubuntu then you might want to shrink Windows to a minimum size and give Ubuntu the lion's share of the hard disk. I have friends who prefer to just delete Windows and install Ubuntu. I know what you mean about needing some program for work though.
> 2) What is the deal with Wubi? Supposedly I can dual boot without partitioning? Can I access the same files? Is this "really" using two different operating systems or is this a virtual version of Linux through Windows?I don't know anything about wubi since I've never tried it. From what I have read about it, it's a 'virtual' version of Linux that runs as a program inside Windows.
> 3) Does anyone know if using Ubuntu will reverse my "consider replacing your battery" and my computer shutting down every 20 minutes? *HP tech support had spent several long hours with me to determine that there is nothing wrong with my battery and that Windows 7 is creating this problem (computer is 10 months old and I know how batteries work).
I don't know, my EeePC has always had a warning like that from Ubuntu every time I start it and the battery in it seems to be okay. Ubuntu does not shut my computer down on me because of it though. Is that a common problem in Windows? I have heard of a few other Windows users complaining about their computers shutting down on them and I know one of my friends from work who can hardly wait to delete Windows 7 and install the new Lucid Lynx. His Windows7 computer kept shutting down on him, so we tried out the Lucid Beta2 Live CD and it kept running great. No problem in the hardware. Now that Lucid Linux is released he's on my list of installations to go and perform. 
> I mainly want to be able to run both operating systems and access the same files (i.e. music files, video files, etc.) with each OS.I know we can access Windows files from Ubuntu without any problems since a long time back, but I'm not sure about the other way around. We used to need to make a separate FAT32 shared data partition but I haven't heard of anyone making one of those for a while now. 
All you really need to do is decide how much room you want to use for Ubuntu and then install Ubuntu.

Will you be using the Ubuntu Installer's inbuilt partitioning tool to resize Windows or are you planning on doing that first with some other partitioning program?

---

### Post by goldshirt9 on 2010-05-02
you run wubi from within your windows o/s.

i believe the battery problem was just with windows 7 o/s.
[http://blogs.msdn.com/e7/archive/2010/02/08/windows-7-battery-notification-messages.aspx](http://blogs.msdn.com/e7/archive/2010/02/08/windows-7-battery-notification-messages.aspx)
i personally have partitioned my system with a section for music, vid's etc etc.
they are both then easily seen in either operating system.

---

### Post by cblah001 on 2010-05-02
Thanks for all of your help so far, this is making me much less confused.
 
I plan on using Ubuntu's Installer to partition instead of manually partitioning. Instead of being worried about whether or not I will be able to access files, would it be a good idea to go ahead adn get a hard drive enclosure/SATA hard drive and just use that for most of my shared files? I have an ESATA port on my computer that I've been dying to use.
 
Thank you again.

---

### Post by reiki on 2010-05-02
> **cblah001 said:**
> Thanks for all of your help so far, this is making me much less confused.
 
I plan on using Ubuntu's Installer to partition instead of manually partitioning. Instead of being worried about whether or not I will be able to access files, would it be a good idea to go ahead adn get a hard drive enclosure/SATA hard drive and just use that for most of my shared files? I have an ESATA port on my computer that I've been dying to use.
 
Thank you again.

Your HP laptop may have partitions that HP installs for recovery (like my Dell does).

You MAY have difficulty shrinking your windows partition beyond a certain point as Windows writes "unmoveable" files sometimes and you can't shrink past them. So do a defrag on your Win7 partition and clean it up as best as possible before proceeding.

Adobe CS4 might be REALLY tough to get working under Wine (if at all). If it's critical to your job, then I'd hang on to that native Win7 install for a while.

Once you get Ubuntu installed you can get VirtualBox running and create a Windows virtual machine and install CS4 into that and see how it works. Generally speaking, you want a lot of memory if you're using virtual machines as the native OS needs memory and teh virtual machine needs memory. If you have 4 GB or more of memory in your laptop, this should work fine. You'd just have to see how the virtual machine (using a virtual graphics card) handles the rendering from CS4.

I noticed you have an eSATA port. I have one as well and I got an eSATA external enclosure that houses a 640GB SATA har drive. I use it for testing and right now it has the Ubuntu 10.04 RC on it. I installed Ubuntu to the external drive, installed grub to the external drive and when I boot my machine I can hit F12 and the BIOS gives me the option to choose a boot device. I choose the eSATA and away we go and I get the Grub menu from the eSATA external.

Easiest way I've found to share file is to simply put them on the windows partition. I create a folder in Windows called "OS-Share" and put any files that both operating systems need access to in that folder. It just didn't make sense to me to create a solution when one already existed. I like to keep things simple if I can.

I know this was wordy... hope it gives you some ideas of your options.

---

### Post by cblah001 on 2010-05-02
Thanks Reiki, goldshirt, and Herman. This has helped me out a good deal.
 
I have an auto-defrag set up each week but I suppose one more cannot hurt. I will be heading out to grab some DVD RWs so I can back up my files.
 
So here's what my plan is...
 
1) Defrag and back up all of my stuff
2) Partition hard drive using installer so I have 10-20 Gb for Ubuntu, one for Windows, and one Swap partition.
3) Install Ubuntu
4) Try and get my programs working properly
5) Call Windows up and tell them how they pushed me to Linux
 
Let me know if I am missing anything here. Windows has been my life since I was tall enough to reach the keyboard and enter DOS commands so I am pretty newbtastic at this.
 
Cheers :popcorn:

---

### Post by Herman on 2010-05-02
> Let me know if I am missing anything here. Windows has been my life  since I was tall enough to reach the keyboard and enter DOS commands so I  am pretty newbtastic at this.:) That looks good.

I think running CHKDSK /R would be a good idea, and possibly more important that running defrag. While neither of those will do any harm, (but could just be a waste of time), a file system check will actually look for problems in your file system and try to repair them for you, or at least report to you on the state of your file system. That seems to me an important step before resizing.

You can run CHKDSK /R easily in a working Windows system by going into 'My Computer', right-clicking on 'Drive C', and choose 'Properties'. Then click on the 'Tools' tab, and go to 'Error Checking'. Click 'Check now'. Windows can't really run a file system check in its own file system while it's running, that's just silly, but you can set the file system check to occur next time you restart Windows. For a thorough file system check, place a checkmark in both boxes, one for 'automatically fix file system errors', (CHKDSK /F) and the other box for 'Scan for and attempt recovery of bad sectors', (CHKDSK /R).

You can also run a file system check from a Windows 'Installation' CD, by bringing up the Windows Recovery console and runnning CHKDSK /F or CHKDSK /R.
CHKDSK /F is quick, but CHKDSK /R is thorough and therefore takes longer.
I prefer to use CHKDSK /R most of the time, especailly when I'm working on other people's computers, I don't like taking any chances.

Strangely, many Windows users seem to have a phobia about running a file system check, but have no problems with the concept of running defrag often. 
You really should be doing both if you want to keep your system running well. 
It's my guess that failure to run a file system check in Windows before installing Ubuntu would be the cause of many of the 'failure to detect', 'failure to resize', and 'GRUB not detecting and including Windows' problems here in Ubuntu Web Forums.

GParted documentation advises running CHKDSK again after resizing Windows, and it places a 'dirty flag' in the Windows file system to induce Windows to run CHKDSK on the next reboot following a resize, so the user doesn't need to bother doing anything.
I think running CHKDSK before the resize would avert a lot of potential problems. :)

---

