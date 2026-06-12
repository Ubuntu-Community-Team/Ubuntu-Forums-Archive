---
title: "READ THIS FIRST prior to posting/upgrading/installing (discussion)"
date: 2006-08-08
forum: Installation &amp; Upgrades
---

### Post by ubuntu_demon on 2006-08-08
This is the discussion thread for this sticky :
[B]
READ THIS FIRST prior to posting/upgrading/installing
[http://www.ubuntuforums.org/showthread.php?t=232037](http://www.ubuntuforums.org/showthread.php?t=232037)[/B]

If you have suggestions for links to add to this sticky then please post them here in this thread.

Here's a general discussion about this stickies management test :
[http://www.ubuntuforums.org/showthread.php?t=233199](http://www.ubuntuforums.org/showthread.php?t=233199)

---

### Post by Golly on 2006-09-18
Hi,
I have installed ´ubuntu´ last week, I´m a newbee in ´ubuntu´.
All is running well.
But now I need a new monitor-resolution (1280x1024).
I never found a place where I can configure my monitor-type (eg. Sony 17SF).

If you able, answer in German!
Golly

---

### Post by j0nn0 on 2006-11-02
This upgrade path worked for me going from breezy to dapper. But in the end I still downloaded the iso for other machines.  My question is: to save on downloading (which is expensive in South Africa) can I download and upgrade using a CD/DVD? If so, how do I do it - presumably by editing out all the repositories in sources.list and then doing apt-cdrom?

tia

j0nn0

---

### Post by westmatrix on 2007-05-02
Hi (not sure if right place to post this)

I am busy right now with the installation and am having a few questions or problems:

I am at the Partition screen, what do I do if the drive I have is partitioned from 80GB to two 40GB's.

Should I select manualy edit and then what?
I have no idea and am really lost here?

---

### Post by Tsen on 2007-05-02
westmatrix,
Was Linux already installed, or is this the first time you've installed it on that machine?
What filesystem are the two partitions (NTFS, FAT32, ext3, ReiserFS?)?

Finally, once that is out of the way, how much space do you want to give to Ubuntu, and how much to Windows? (Assuming you're planning on dual-booting.  If you only want Ubuntu, then don't bother manually partitioning, just tell it to use all of the hard drive)

---

### Post by westmatrix on 2007-05-02
Ok they are both NTFS and (+ -) 40GB's each.
Ubuntu 40GB and Windows the same.

---

### Post by westmatrix on 2007-05-02
Ok back in now and deleted the D: drive, now in the partition section looking at select a disk.
Please note that I have 2 drives and one is partitioned into two 40GB's the other is 120GB, namely C:40GB (non-existent D:40GB) and E:Other
What should I do now?:confused:

Was not sure where to post this question but I seem to have posted it her as well, sorry:
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2573940](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2573940)[URL="http://ubuntuforums.org/showthread.php?p=2578035#post2578035"]
[/URL]

---

### Post by westmatrix on 2007-05-03
Problem solved, Ubuntu is installed and working.
Thank you all.

---

### Post by Naci Sey on 2007-08-02
Just installed 6.10 desktop with the hope of 'fixing' problems encountered with Dapper [_screen resolution_]("http://ubuntuforums.org/showthread.php?t=513803"), for example. Had taken steps to install Feisty, actually, having downloaded and burned the image CD. However, no matter the option I chose on my ash-checked CD, I kept getting stalled with the message [_can't access tty... (initramfs)_]("http://ubuntuforums.org/showthread.php?t=514944") - as, apparently, several other people have.

As to my new install of 6.10 desktop:

Good news:
* Screen resolution fixed.
* Looks nice (probably b/c of the screen res), sound is improved.
* In the Update Manager, there's an Upgrade button for 7.04.

Gone:
* System -> Admin -> Disks. 
In Dapper I used this GUI to mount my other hard disk so I could access my WinXP files. In Edgy desktop, there doesn't seem to be a GUI for this and I don't know how to access my Win files otherwise.

Odd:
* Installed the desktop version of Edgy, yet server stuff has been included. **Don't want a server**. (This absolute beginner is challenged enough with the desktop.)

Related to the last... 
Tried upgrading from 6.06 to 6.10 several days ago using Terminal b/c there was no Upgrade button in 6.06's Update Manager. What I got was the 6.10 server package, not the desktop.
Still want to install Feisty. BUT, given the foregoing I'm wondering what's going to happen when I click that handy-dandy Upgrade button. Will there be an option between desktop and server, or will the install automatically be for the server?

---

