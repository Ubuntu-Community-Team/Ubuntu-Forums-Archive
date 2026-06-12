---
title: "request info on dual boot - please read entire post"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by windowsfree on 2010-01-16
I have a laptop with **Ubuntu 9.04** on it and it is pretty much set up the way I like it.
(1 gig memory, 60 gig HD and a celeron processor- Yes, it is an old Gateway)
anyway i have windows 7 ultimate running in a virtual machine and for performance gains and other reasons was thinking of having the laptop setup to dual boot Win7 and Ubuntu.
I heard and read so much about the partitions with Win7 and the boot manager that I don't know if this is something I want to do.   My workplace is adopting Windows 7 from XP shortly and using MS Office so that is another reason I was thinking about doing it.

I have a desktop with 1.5 gig of ram and 200 gig hd, an old semperon processor 2.0, that runs **Ubuntu 9.10**.  I was thinking of doing it on that machine as an alternative, but again, will I have to wipe my install of Ubuntu just to save headaches of putting Win 7 on it.

Any and all feedback will be read, considered and much appreciated.  Thanks!

---

### Post by fancypiper on 2010-01-16
Have you checked out this guide yet?

[Dual Boot Ubuntu and Windows](https://help.ubuntu.com/community/WindowsDualBoot)

Perhaps if you posted the output of these commands, we would know more about your systems.

sudo fdisk -l
mount
df -h

---

### Post by windowsfree on 2010-01-16
> **fancypiper said:**
> Have you checked out this guide yet?

[Dual Boot Ubuntu and Windows]("https://help.ubuntu.com/community/WindowsDualBoot")

Perhaps if you posted the output of these commands, we would know more about your systems.

sudo fdisk -l
mount
df -h

Okay, thanks for your response, I attached the screenshots.

---

### Post by fancypiper on 2010-01-16
If your /home folder isn't too big (**du -sh /home**), you could copy that to a dvd, (possibly backing up /etc as well), you can then start from scratch with a better thought out partitioning scheme.

You are using a little over 8 GB for everything except swap, so I think you can probably save your settings on DVDs.

I would recommend something like this:
Windows partition - whatever Microsoft suggests,
/ - 8-10 GB
swap - no more than 2 GB
/home - the rest of the drive.

Install Windows first, then Linux, then you can copy your /home/<user>.

Be cautious about replacing your /etc files as you will have to rebuild your software selection.

---

### Post by windowsfree on 2010-01-16
OK, here is the output from that command.   

Thank you for your help on this.  I know I need at least 20-25 gigs for **Windows 7**, which will give me about the same for **Ubuntu 9.04**.  I was told **Windows 7** installs another unnecessary partition.  I don't remember what forum thread I read that in.


> **fancypiper said:**
> If your /home folder isn't too big (**du -sh /home**), you could copy that to a dvd, (possibly backing up /etc as well), you can then start from scratch with a better thought out partitioning scheme.

You are using a little over 8 GB for everything except swap, so I think you can probably save your settings on DVDs.

I would recommend something like this:
Windows partition - whatever Microsoft suggests,
/ - 8-10 GB
swap - no more than 2 GB
/home - the rest of the drive.

Install Windows first, then Linux, then you can copy your /home/<user>.

Be cautious about replacing your /etc files as you will have to rebuild your software selection.

---

### Post by fancypiper on 2010-01-16
You have too much in /home (5.1 GB) to fit on one DVD, you may have to split it so that it is less than 4.7 GB (standard DVD-R).

You can probably get by with 5 GB for / if that is all the software you intend to install.  My / is 20 GB and I had it full at one time.  I am a little more selective with software now and I have 9 GB free in /.

---

### Post by fancypiper on 2010-01-16
[This thread]("http://ubuntuforums.org/showthread.php?p=8676460#post8676460") has a method to copy your /home to /media/<foldername> and you won't have to burn to CD.

---

### Post by windowsfree on 2010-01-17
I looked at my home folder, i have an ISO subfolder and 3.5 gigs of that is my Windows ISO image.  So I will be okay.  Thanks for the help.......think I am gonna do it on the desktop that is running Ubuntu 9.10 for now.  It has more ram and a quicker processor.  I do appreciate your input.  I may dual boot the laptop with XP and some point and your instructions were helpful and also a learning experience for me.  Thanks again.

---

