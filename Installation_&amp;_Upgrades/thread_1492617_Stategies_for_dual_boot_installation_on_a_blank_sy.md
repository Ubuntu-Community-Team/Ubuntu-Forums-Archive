---
title: "Stategies for dual boot installation on a blank system?"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by TJRC on 2010-05-24
Every tutorial I've seen on installing a dual boot environment assumes you already have an installed OS (usually Windows).

My wife's XP system is pretty hosed, and she's been interested in Ubuntu.  Because she's ripe for an XP re-install anyway, I'm planning on backing up her data, completely wiping her hard drive, and installing a dual-boot Windows-XP/Ubuntu environment.  Any good step-by-steps for this, with good hints on how to partition, etc.?

If not, my plan B is to reformat and install a basic XP system, and then follow one of the tutorials for going dual-boot over an existing install.  Does that make sense?

I should mention, I've used Linux for years as a user on my ISP, but have only been using Linux on a home system for a couple months; so I'm fairly new to the install and administer side.

---

### Post by pradeepthundiyil on 2010-05-24
hi, 
 
Put your xp cd through which you can Format and partiton your hard disk. Select appropriate sizes & number of partiton .. Ubuntu takes around 17 GB of space for installation, So leave 30 Gb or so for ubuntu. Fat file system would be better. If you want to install ubuntu within windows format all the partitions. If you are planning for a separate install of ubuntu, leave some space without partitioning (unallocated space). Then install XP,  after that install Ubuntu by selecting " Install them side by side option".

---

### Post by julio_cortez on 2010-05-25
I have a 1TB drive and I did it this way (using W7 and Kubuntu, but it's almost the same):

[LIST]
[*]First of all, I made a "plan" of the partitions. I decided to reserve 300GB for the **Windows** install, plus assign 500GB to a **"shared" data partition**, and split the rest between **/**, **/home** and **swap** for Kubuntu.
[*]Then I installed Windows first. In Windows 7 I had to let it create partitions and then manually change their sizes and drop that annoying 100MB partition W7 creates for BitLocker and such stuff, leaving some free space at the end of the disk as planned.
[*]Once installed W7 I checked that everything was fine and formatted also the "shared" data partition as NTFS.
[*]Then I installed Kubuntu, using the "manually define partitions" option to split **/** and **/home** as planned.
[*]At the end I had Windows and data on NTFS (with the "data" partition automatically mounting at each startup), / and /home on ext4.
[/LIST]
GRUB installed itself successfully without having to configure anything, and still lets me choose which system to load (having Kubuntu with the newest kernel as default).
Just keep in mind that the **Windows** partition has to be **primary**, but there's no problem in having all of the other ones as logical.

---

### Post by TJRC on 2010-05-29
Thanks for both of your advice here.  After looking at my wife's system, I never realized how underpowered it was.  Instead of using her system, I'm going to do the same dual-boot install discussed above, but on my old system I recently replaced.  Anyone want to sanity-check my planned partition sizes?

The target system is  a dual-core 2.8GHz Pentium 4, with a 136GB HD and 3GB RAM.

My wife's old system has a 55GB drive, of which about 23GB is in use; about 12GB for data and about 11GB for Windows and all other software (i.e., Windows, swap, Firefox, Office, a few other apps).  She uses her system only for web browsing; using MS Word and occasionally Excel; and uploading photos from our digital camera.  Based on the target configuration and her historical disk and system usage, I'm thinking:

P1: For Windows XP, Windows swap and other Win software: 20 GB (primary, NTFS).  She's only using 11 now, 20 should be plenty of headroom.

P2: Data partition, shared between both Windows and Ubuntu, whichever happens to be booted: 80 GB (NTFS).  On Ubuntu, I'll put /home here; on Windows, I'll have "My Documents" shortcut here, too.  There's nothing magic about the 80 GB number; that's just what is left after subtracting the other partitions from the 136GB disk.  Again, she's only using 12 right now.

P3: Ubuntu OS: 30 GB (based on pradeepthundiyil's rec above) 

P4: Ubuntu swap (6 GB) except that I've read that the max size for a swap partition on a 32-bit system is 2GB (see [here]("https://help.ubuntu.com/9.04/installation-guide/i386/apcs03.html")); is that still correct?

Thoughts?

---

### Post by TJRC on 2010-05-31
Just providing an update, I have gone ahead and done the install almost along the lines of what's above in my prior note.  Seems to be working okay.  What I encountered:

1) My first take was, just as I described above, to install Windows on the whole disk, and then resize.  No such luck.  To my surprise, the Ubuntu installer would not let me shrink the Windows partition.  I tried booting from the live CD and using GParted, but no luck there, either; it would only allow me to make it larger.

I finally gave up, deleted the whole thing, and set up my partitions first, (almost) as described above; and then installed Windows into the primary.  That worked.

2) As it turns out, /home cannot be on an NTFS-formatted partition.  Makes sense, now that I think of it.  So I kept /home on the main Ubuntu partition, and called the shared NTFS partition /data.  I'll put a directory for photos there, and put a link in $HOME/Pictures to point there.

3) I went with the 6GB /swap.  I'm not sure I'm not wasting space with this, but it's not much.  And my last install on this same system used 6GB by default, so I'm in good company.

For reasons having nothing to do with Ubuntu or dual-boot, I had to re-install Windows again after Ubuntu was already in, which caused me to lose GRUB, as expected.   I found two procedures for fixing this.  [This one]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") did not work; it failed with an I/O error on 915resolution.mod, which I never did get to the bottom of.  Fortunately,[ this procedure]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") worked like a champ.

A half-dozen Windows updates later, I'm up and running both OSes pretty much as planned.

Thanks for the tips.

---

### Post by wilee-nilee on 2010-05-31
Just for future reference I suspect you had to reinstall Windows this last time due to putting grub in a partition rather then the MBR only. Which I suspect you understand at this point as your link to the grub wiki shows this difference, glad you figured it out, and all by yourself to boot.;)

Here is a link that might of help to you in the future.
[http://www.informationweek.com/news/windows/showArticle.jhtml?articleID=189400897&pgno=1](http://www.informationweek.com/news/windows/showArticle.jhtml?articleID=189400897&pgno=1)

---

### Post by TJRC on 2010-06-01
> **wilee-nilee said:**
> Just for future reference I suspect you had to reinstall Windows this last time due to putting grub in a partition rather then the MBR only. 

Nah, it was due to a different dumb error on my part.  I used the install CD from my wife's Dell system, instead of the one that came with my old Dell system (my CD is long-gone), on the mistaken belief that they were probably the same.  But her install disk didn't include support for my network interface and some other things.  I wasn't sure what went wrong, and re-installed, this time watching a little more carefully, and realized what the problem was.  But I could download the necessary drivers from Dell's support site and get up and running okay.  

Technically, my re-install of Windows didn't buy me anything, but since both Windows and Ubuntu were both in pretty pristine states, it didn't worry me much, not much work would be lost; and it was nice to have a practice run at restoring GRUB when there was nothing at stake yet.

Had I done a more thorough check of Windows before proceeding with the Ubuntu install, I would have caught the problem, but I deliberately did not want to make a network connection until I'd moved on to installing the antivirus software.  Once I had a Windows that let me boot okay, I figured I had a stable platform (well, as "stable" as Windows gets, anyway).

---

### Post by TJRC on 2010-11-04
I just thought I'd follow-up on the results of this.  I'm pleased to report that I really cannot tell how well my partitioning scheme worked out; because my wife has been successfully using Ubuntu 100%, and has not once found the need to boot into Windows do do anything.

So while I think the Windows half went okay, I don't really know, because apart from my testing before turning the system over to her, Windows has never been booted!

If I knew she was going to be this pleased with Ubuntu, I wouldn't have bothered with the Windows partition; or maybe set it up as a VM under VirtualBox.

---

