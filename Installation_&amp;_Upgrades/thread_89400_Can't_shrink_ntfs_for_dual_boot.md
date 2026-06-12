---
title: "Can't shrink ntfs for dual boot"
date: 2005-11-12
forum: Installation &amp; Upgrades
---

### Post by sheenaramone on 2005-11-12
I decided to take the plunge and try to install Ubuntu 5.10 alongside Windows XP Pro on a laptop.  Live Ubuntu and Kubuntu worked great on this laptop and was able to connect to the internet.  I cleaned the drive up as much as possible and defragged at least a dozen times.

The drive is 60 G and Windows takes up a little over 20 G, so I thought 30 G for Windows and around 20 G for Ubuntu would be ok, but...

I was not able to resize the ntfs with either the Ubuntu install cd or qtparted on a rescue cd.  It says the minimum size is about 800 MB less than the max, and I can't shrink it any more than that.

I noticed a message on the rescue cd about resizing not working if "something about framebuffer".  I hunted through the BIOS and did not see anything about framebuffer.  I did change the setting for the disk managament from DOS to other, but still was not able to resize the Windows partition.

Any ideas on what I am doing wrong?  What is framebuffer?  I used the bigpond herman site and got the idea about the rescue disk from the Ubuntu Wiki.

Sheena

---

### Post by yesplease on 2005-11-12
Does your reply here [http://www.ubuntuforums.org/showthread.php?t=89453](http://www.ubuntuforums.org/showthread.php?t=89453) mean that this problem is solved?

---

### Post by sheenaramone on 2005-11-12
[QUOTE=yesplease]Does your reply here [http://www.ubuntuforums.org/showthread.php?t=89453](http://www.ubuntuforums.org/showthread.php?t=89453) mean that this problem is solved?[/QUOTE]

No, it was just something I noticed while I was attempting the install.  Sometimes the arrows do the job and once in a while you gotta use tab.

I have Ubuntu on a desktop and the install was trouble free, but it was a fresh install.

I was tempted to take over the laptop but then I give up all the lunar mapping programs, the telescope operating programs, etc.  So I wanted the best of both worlds- Ubuntu, for which BOINC is blisteringly fast on my Pentium M and the Windows programs for when I use the laptop at the observatory.  However, I am finding that Linux observatory software does exist and that would eliminate the last reason to keep Windows.

From further research, it appears a Windows XP ntfs partition cannot be resized.  If I truly want a dual boot machine, I'll have to start from scratch, and reformat the drive and then install the two OS.  So I am afraid that is what the answer is.

Sheena

---

### Post by brallan on 2005-11-12
i have just gone through a similar process with FAT32, not NTFS, it took me forever to figure out how to defrag (optimize) that is to the unmovable files that XP refuses to move with defrag. I could not do a reinstall without the XP CD. here's what i was able to do:

It sounds as if you COULD make a partition if only you could make a big enough free space at the end of the drive:

[http://linuxmafia.com/faq/Filesystems/ntfs.html](http://linuxmafia.com/faq/Filesystems/ntfs.html)
[http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html)

If that's the case, my solution might work for you:

I tried all sorts of defraggers to no avail, and finally downloaded the eval version of perfectdisk, which in <offline mode> was able to fully optimize the files XP doesn't let you touch. 

also, you might try  turning off your page file: R click on <MyCOmputer><Properties><Advanced>and <settings> under performance, i did that and maybe it helped, booting in safe mode and defragging didn't.

good luck. Now that i've got an 8 G partition, my problem is that i can't get the external USB CDROM to boot (I even flashed the BIOS!) so i need to figure out how to copy an iso file over to the XP partition and set up a floppy with grub which will find it and boot it. but everything i read about grub is like Egyptology. AAAARGH! I MUST get GEEKIER....

---

### Post by Herman on 2005-11-12
[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)
You should normally be able to resize your NTFS partition with either the 'Hoary' or the 'Breezy' Ubuntu partitioner. I have this on good authority, and also if you check the screen caps in the above link, it is shown being done. Some out-of-date information is still circulating referring to the old 'Warty' partitioner, which couldn't resize NTFS.
The Ubuntu partitioner is very safe and sensitive and won't do anything if it 'thinks' it might wipe out something it isn't supposed to.
My wife's and my computers are both identical and we are both dual booting with Win XP, FAT32. Both identical hardware and software. But hers is like yours, I tried to partition it and _no partitioner_ will touch it. Others on the forum have occasionally reported this too. I have defragged it many times. I can't see why mine can be partitioned more, but hers can't. It used to be able to, because obviously we already did it to get it dual booting the first time. Has she got some kind of third party software installed, or a setting somewhere we've both forgotten about? :confused: 
Sorry I can't help, but I don't think it's the partitioner, that's the main point I want to make .:D (Herman)

---

### Post by yesplease on 2005-11-12
On top of that, I read that defragging before resizing is not necessary. (**edit: Incorrect info,  read McDuck's post below**) The resize option of the partitioner is safe, except when it warns you that it cant resize. 

NTFS resize FAQ: [http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html)

Perhaps someone may be able to help you when you give more information on your hardware (and the BIOS settings of the hard disk).

---

### Post by sheenaramone on 2005-11-12
Thank you Herman and Yesplease for the links, I will try again tomorrow and let you know how it goes.

 Tonight I am testing between Ubuntu 5.1 and KUbuntu 5.1 to see if there is any speed difference with BOINC.  Using Live Kubuntu right now, typing this on the Gateway Pentium M laptop.

What BIOS settings are pertinent for the hard drive?

Sheena

---

### Post by yesplease on 2005-11-14
I stumbled upon this [http://www.linux-laptop.net/](http://www.linux-laptop.net/) perhaps your gateway is on there.

---

### Post by mcduck on 2005-11-14
[QUOTE=yesplease]On top of that, I read that defragging before resizing is not necessary. The resize option of the partitioner is safe, except when it warns you that it cant resize. 

NTFS resize FAQ: [http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html)

Perhaps someone may be able to help you when you give more information on your hardware (and the BIOS settings of the hard disk).[/QUOTE]
That page says, that you don't need do defrag first if the ntfsresize is version 1.11.2 or later, and there's also a table about version in different linux distros that reports Ubuntu 5.10 to have 1.9.4 so defragging is indeed needed.

Other than that, when I installed Hoary I did let it's installer to shrink my NTFS-partition, and it worked perfectly. It's worth a try, but backups are sure important. But sure everybody has those anyway? :)

---

### Post by sheenaramone on 2005-11-14
[QUOTE=yesplease]I stumbled upon this [http://www.linux-laptop.net/](http://www.linux-laptop.net/) perhaps your gateway is on there.[/QUOTE]

I have a 450 RGH and there were two 450's in the list.  One mentioned setting the disk management in BIOS to "other", which I have done.  Neither were trying to do a dual boot thing, though.  But they were happy with using their distros, Fedora and Red Hat.

Sheena

---

### Post by sheenaramone on 2005-11-14
I noticed a setting in disk properties for "compress files to save disk space" and I selected this.  It took about an hour and a half to go through and when it was done, everything was red in the defragment display.  So I went through a bunch more defrags and turned everything blue again.  Then I tried to intall 5.10 again and when I got to the partition resizing, it still would not let me shrink it any more than 2% less.  

I didn't much care for the behavior of the system with this compression back in Windows, so I undid it and went through all the defragging again. 

I ran across this

[http://nishants.net/articles/ntfsresize.htm](http://nishants.net/articles/ntfsresize.htm)

which I thought was rather provocative.  It said you could resize ntfs partitions using a Live Ubuntu CD.  I thought, wow, I thought you couldn't do anything to the hard drive with the Live CD, and this says you can mount the Windows partition and install ntfstools!  I had read about ntfstools before and even downloaded it and looked at all the files and folders and had no clue what to do with them.  But this article gave me a step by step of what to do except when I tried to mount /dev/hda1 /mnt/hda1, I was told only root can do that and I guess a Live CD has no root.

(pause for laughter)

So is this article an example of Linux humor?  If it is, it is not as funny as the one about installing Linux on a dead badger.  I wonder if you can run Live Ubuntu on a dead badger?

Sheena

---

### Post by missmoondog on 2005-11-14
yep. been going through these changes for the last few days also. wound up giving up on trying to resize ntfs and wiped all 5 computers out and started everything from scratch. installed xp using fat32. installed windows on minimum amount of disk space, let ubuntu take the rest. i now have 1 dual boot xp pro/ubuntu 5.04 and 1 xp pro/ubuntu 5.10 up and running, and 3 full time 5.04's (for now).

searching for what might be the smoothest way to upgrade those 5.04 machines without losing anything now.

---

### Post by yesplease on 2005-11-15
On the install CD there is a manual under /doc/install manual/en . Section 5.2.1 is about boot parameters. Apperantly there are boot parameters to disable framebuffer (and pcmcia). 

I have never done this (my install took 45 minutes :) ) but perhaps it is of use.

Edit: [http://www.waltzking.org/linux/450.html](http://www.waltzking.org/linux/450.html) DID install dual boot. Both authors on [http://www.linux-on-laptops.com/gateway.html](http://www.linux-on-laptops.com/gateway.html) are very detailed and do not speak about framebuffer problems. Now the advice of missmoondog seems solid, just do a clean install. However, trying the boot-options or ntfs resize is not that much work, and would be a more satisfying solution if it works.

---

### Post by missmoondog on 2005-11-15
yeah, this version (5.10) did take forever to install, didn't it? i had xp pro installed in half the time when installing them both on here just yesterday.

---

### Post by yesplease on 2005-11-15
@missmoondog: It can save a lot of time to do a clean install instead of repairing a major issue. I understand that reinstall leaves your data intact if you have a separate root swap and home partition.Resizing works properly for most people (which is quite an achievement of the linux people).  However, if there is really a problem with ACPI or framebuffer the poster would run into that later anyway. 

Perhaps laptop manufacturors use non-standard bioses, non-standard hardware or even customized windows, which give features like fast hybernating. This may be usefull in 90 % of the cases.

---

### Post by sheenaramone on 2005-11-16
I think I found the problem with resizing the ntfs partition.  

I ran across this article

[http://www.osnews.com/story.php?news_id=10206&page=2](http://www.osnews.com/story.php?news_id=10206&page=2)

where it said the resize didn't work, chkdsk /f was run and then the resize did work.

I have another laptop that I often have to run recovery console on so I am familiar with chkdsk from that.  I dug out the system cd and booted into recovery console and ran chkdsk /r.  This is suppposed to find and repair bad sectors.  

When I next booted with the rescue cd and ran qtparted, it said I could resize the partition down to 2 mb!  It let me squish it down in the graphical display but when I said ok, it said the disk had bad sectors or is dying.

So now I'll see if I can solve that problem.  I'll run chkdsk /f and also try the resize with the Ubuntu install cd.

Sheena

---

### Post by codemarauder on 2005-12-03
[QUOTE=sheenaramone]
I ran across this

[http://nishants.net/articles/ntfsresize.htm](http://nishants.net/articles/ntfsresize.htm)

But this article gave me a step by step of what to do except when I tried to mount /dev/hda1 /mnt/hda1, I was told only root can do that and I guess a Live CD has no root.

So is this article an example of Linux humor?  If it is, it is not as funny as the one about installing Linux on a dead badger.  I wonder if you can run Live Ubuntu on a dead badger?

Sheena[/QUOTE]
You can become root by simply running this command on a xterm:

# sudo bash

And can then mount the filesystem to install the packages that are on the Windows partition.

regards,
Nishant

---

### Post by sheenaramone on 2005-12-09
Thank you, Nishant for your kind reply.  I will indeed try that again.  And please forgive me if my remarks were taken to be unkindly.  I obviously don't know much about what I am doing and appreciate all the help I've gotten here.

I was able to get the rescue disk to tell me I could shrink the windows partition, but when I tried, I got a message that the disk has bad sectors or is dying.  The resize with the Ubuntu install disk was also ineffective.

So Nishant is my last resort, and after that, if I truly want both OS on this laptop, then I will start over, format and partition the disk first and then install each OS.

Sheena

---

