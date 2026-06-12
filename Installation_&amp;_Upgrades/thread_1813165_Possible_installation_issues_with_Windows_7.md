---
title: "Possible installation issues with Windows 7?"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by dooberheim on 2011-07-27
Hello all - I'm new to this forum but have been using Ubuntu since about 2008.
 
I have a new Dell Inspiron 620 with i5-2310 (2.9 GHz), 1 TB HDD, 8 GB DDR3 running Windows 7 home 64 bit, that I want to install Ubuntu 10.10 64 bit LTS on from a CD (as a dual-boot system). I was looking on the web last night for information on how long the installation might take, and ran across a number of comments/posts in several places as to how the installer crashes, and in some cases corrupts Windows 7 to the point of requiring a complete reinstall.
 
I have installed older versions of Ubuntu (7.10 and 8.10) on Pentium 4 machines running XP Pro without difficulty, but had a problem installing 7.10 on a Pentium 4 machine running XP Home requiring chkdsk to reformat the partition I was trying to make.
 
I read in my somewhat limited search that Windows Vista and 7 have files that need to be in a particular physical place on the hard disk, and if the partitioner tries to move them it hoses Windows.
 
My question is - has anyone sucessfully installed Ubuntu 10.10 64 bit on a machine comparable to mine in a dual-boot configuration with Windows 7 Home 64 bit? I really don't want to proceed unless there is some positive experience with this, as I have other options for running Linux that are possible, but simply less convenient.
 
Thanks for any info.
 
Mark

---

### Post by Beacon11 on 2011-07-27
First of all, the latest LTS is 10.04, not 10.10. Did you try searching with the wrong terms?

Also, I think you're more likely to see horror stories than success stories-- if you're searching for bad things, I bet you'll find them. Not very many people post "Oh look, I this machine with Ubuntu 64 and Windows 7 64 play nice!" Windows 7 has a great backup utility-- I'd get a good backup taken, and then take the leap. If it fails, it's just a little inconvenient to restore. I bet you'll find it works great. Sounds like a nice machine.

If it makes you feel better, I currently have a desktop that dual-boots Windows 7 64 and Ubuntu 10.04 LTS. Works like a charm, but the machine is not identical to yours. The installer was great at picking up my Windows install.

---

### Post by dooberheim on 2011-07-27
Thank you, Beacon11.  I got the download from here:
 
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
 
and see that I probably downloaded 10.04.  That's fine - I am always leery of using the newest version of any software like this.
 
I understand about dissatisfied people posting more than satisfied ones, and I did do a boot DVD, and image from Windows onto an external hard drive.  I just don't have a lot of time to mess with getting things to work.
 
I'll give it a shot.  Thanks!!
 
Mark

---

### Post by Beacon11 on 2011-07-27
Hey Mark. I understand the lack of time! I've been using Ubuntu since 2007 and have yet to have installation issues other than burning a corrupt CD (make sure you check that by the way, along with the MD5 sum of the image you downloaded). If you run into issues, make a new post and post a link in here letting me know. (Creating a new issue gets more eyes).

---

### Post by oldfred on 2011-07-27
Most new Windows computers today come with all four primary partitions used. They seem to want to make it difficult to install anything else. Do not create new partitions in windows as it will convert from the basic 4 partitions to dynamic or logical and lead to huge problems.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by dooberheim on 2011-07-27
To beacon11 and oldfred:
 
I couldn't even boot from the CD - the start screen (with the 5 dots) was still running a half an hour later.   MD5 chacksum was correct, and I could get the pop-up giving you the choices on how to use the CD from within Windows.  It just wouldn't boot.
 
Having read some of oldfred's links I've decided not to mess with this.  I like the Ubuntu I have on my computer at work (a newer Pentium 4, XP Pro), but I guess I'll just have to use it there (or on MU's overloaded cluster, where your jobs can wait hours before they are run).  Disappointing.
 
Thanls for all your help.
 
Mark

---

### Post by YesWeCan on 2011-07-27
You are probably more worried than you need to be. :)
The hang up while booting the cd might be a graphics card issue. This is not unheard of. There is an options function key menu where you can select nomodeset. This might fix it.

---

### Post by Mark Phelps on 2011-07-28
If you don't have a Win7 install DVD, BEFORE you do anything regarding dual-boot, use the Win7 Backup feature to create and burn a Win7 Repair CD.  That will prove invaluable later, should you need to repair the Win7 boot loader from the dual boot setup.

---

