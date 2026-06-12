---
title: "Problems Found With Ubuntu 9.xx"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2010-02-27
First problem is that even during an install, the whole process seems to want to hang sometimes.  Watch the status bar barber pole as it rotates, then see it suddenly stop rotating.  It that happens, be prepared to press a shift key or move the mouse, and that will start it rotating again.  Aggravating, since you can't just leave the install process to run by itself.  Same problem shows up after then install, but there you don't have a barber pole effect to signal that there is a problem.  Same temporary fix though.  It even shows up as a problem under VirtualBox, but there the keyboard just locks up, and it takes certain actions with the mouse to get the keyboard to be recognized again.

Second problem is that you can be editing a post for the forums, or working on a document, and suddenly the document jumps as the local position is altered somehow, but when you keep typing, the local position jumps back to where you are entering text.  In other words, you can deal with it, but you should not have to do this.

Third problem is that the cursor keys, which should move up or down a line each time pressed, are specific to where the focus is set in a Window.  That is, you want to move up and down on the page itself, you need to use the mouse to click on some part of the page.  If you want to move up and down in a listbox, you have to use the mouse to set the focus inside the listbox.  This might suit some, but it seems like I keep having to switch between the mouse and the cursor keys as a result.

Fourth problem is that 9.04 works better on some PCs than 9.10 does.  The 9.10 can install okay, but when you boot into it, you may get no mouse pointer or the mouse pointer may not respond to mouse movements.  This alone has forced me to revert back to 9.04 for several installs.

Now here is a new one.  I'm trying to set up 9.04 four times in four different partitions on the same PC, once each on /dev/sda2, /dev/sdb1, /dev/sdb3, and then on /dev/sdc3.  If I wipe those four partitions clean by formatting them, I can get one install done fine.  But as I try to add the second install, I run into some problems.  The install may go well, but the partition check fails with Error 8.  Or the boot loader says a file is missing.  If I get past two, the third one will surely mess up, with these symptoms or something else.  If I can get as far as trying the fourth install, it may indicate that it went okay, but nothing gets written to that fourth partition.  If I go the reverse way, from /dev/sdc3 back to /dev/sda2, the problems repeat in the same order of 1st to 4th installs.

Now what I am doing is just designating the root partition and using the same swap as a default.  I use the same data settings for userid, password, computer name, and so on.  After the first install, I get a request for a userid entry on the second and later installs, meaning that I guess the installer is taking info from the partitions already installed and trying to apply it again to the current install.  That should not be happening, because I use the manual partitioning approach, and the only partitions flagged are the ones for root and the persistent swap.

I also find that grub is not doing what I would expect in adding these new installs as well.  I found that using the command grub, then find, root, and setup, and I can get the first install to boot again, but it reports something wrong or missing, then drops to a command prompt state to be dealt with.

My impression is that the installer process is not really treating each install effort as totally independent from what is found elsewhere on partitions.  I mean. suppose it looks to see if there is already a /home folder somewhere, or an /etc or /bin, and of course there will be if I only designated root (/) previously, and it is getting multiple installs all mixed up as though part of the current install effort.

Could be.  Afraid that this same approach would poison every effort to have multiple installs of Linux on the same PC if found to be true.  If it is just with Ubuntu, then it would require that Ubuntu be the first install every time, and that all other installs be wiped before it could be done successfully.

---

### Post by kerry_s on 2010-02-27
> First problem is that even during an install, the whole process seems to want to hang sometimes

turn off effects before install.

> Second problem is that you can be editing a post for the forums, or working on a document, and suddenly the document jumps as the local position is altered somehow, but when you keep typing, the local position jumps back to where you are entering text. 

are you talking about a touchpad?

> Third problem is that the cursor keys, which should move up or down a line each time pressed, are specific to where the focus is set in a Window. That is, you want to move up and down on the page itself, you need to use the mouse to click on some part of the page. If you want to move up and down in a listbox, you have to use the mouse to set the focus inside the listbox. This might suit some, but it seems like I keep having to switch between the mouse and the cursor keys as a result.

not sure what say, all programs work different, it's a matter of learning how to use it.

> Fourth problem is that 9.04 works better on some PCs than 9.10 does. The 9.10 can install okay, but when you boot into it, you may get no mouse pointer or the mouse pointer may not respond to mouse movements. This alone has forced me to revert back to 9.04 for several installs.


agreed, 9.10 sucks. i'm using 9.04

> Now here is a new one. I'm trying to set up 9.04 four times in four different partitions on the same PC, once each on /dev/sda2, /dev/sdb1, /dev/sdb3, and then on /dev/sdc3. If I wipe those four partitions clean by formatting them, I can get one install done fine. But as I try to add the second install, I run into some problems. The install may go well, but the partition check fails with Error 8. Or the boot loader says a file is missing. If I get past two, the third one will surely mess up, with these symptoms or something else. If I can get as far as trying the fourth install, it may indicate that it went okay, but nothing gets written to that fourth partition. If I go the reverse way, from /dev/sdc3 back to /dev/sda2, the problems repeat in the same order of 1st to 4th installs.

i'm not even going to ask why you need 4 installs, but sounds like a bug thats to late to fix or it's just the way your trying to set it up, can't say as i've never tried something like that.

> Now what I am doing is just designating the root partition and using the same swap as a default. I use the same data settings for userid, password, computer name, and so on. After the first install, I get a request for a userid entry on the second and later installs, meaning that I guess the installer is taking info from the partitions already installed and trying to apply it again to the current install. That should not be happening, because I use the manual partitioning approach, and the only partitions flagged are the ones for root and the persistent swap.

i guess machines can get confused to, i always have a time figuring out which twin is which. :lolflag:

> I also find that grub is not doing what I would expect in adding these new installs as well. I found that using the command grub, then find, root, and setup, and I can get the first install to boot again, but it reports something wrong or missing, then drops to a command prompt state to be dealt with.


it's confused they all looked the same. :lolflag:

> My impression is that the installer process is not really treating each install effort as totally independent from what is found elsewhere on partitions. I mean. suppose it looks to see if there is already a /home folder somewhere, or an /etc or /bin, and of course there will be if I only designated root (/) previously, and it is getting multiple installs all mixed up as though part of the current install effort.

Could be. Afraid that this same approach would poison every effort to have multiple installs of Linux on the same PC if found to be true. If it is just with Ubuntu, then it would require that Ubuntu be the first install every time, and that all other installs be wiped before it could be done successfully.

not something a average user would do, so having problems is no surprise to me.

---

### Post by oldefoxx on 2010-02-28
The problems (and I mean many) about installs hanging or evidence of it hanging in normal use have occurred both on a Toshiba laptop with touchpad and on a Gateway with an optical mouse being passed to the PS/2
port through a USB to serial adapter.  On both machines I have plugged in a second USB to mouse connector and the problems remain even with the second mouse attached.  When working normally, either or both mice work as they should.

A long time problem with PC software is the dependency on keystrokes to see if the user is currently active.  AOL used to bump dial-in users if they did not initiate some command in a certain period of time.  One way to deal with this was to run a small program that periodically asked for either a page update or made some other query, and that kept AOL from kicking you free of the internet.  Really handy program if you had huge files to download, because they never bothered to see if there was traffic with the PC, just how long it had been since the keyboard was last used.  Maybe there is a setting issue with the installed software, but that does not account for why the same problem happens when it is being installed, unless a default setting within the installer's version is having the same effect.

I'm not surprised that you see my efforts as going beyond what most users would attempt.  I figure the same, but if true, as my experience suggests, then it needs to be addressed at some point.  The installer plainly says that in manual pratitioning mode, that if you do not designate a partition for a specific purpose, it will be ignored and not used.

But what I've gone through shows that this may not be the case at all.  In fact, I can foresee many circumstances where this would work against a dependency on Ubuntu, or Linux in general, because it is often a better choice to add a second install and shift work over to it before just ridding yourself of the first.  The first may be on a drive that is suspected to be reaching the end of its life, or the user may be moving to a newer PC which has to be reconfigured to support ongoing work.

Some would choose to use a tool like Clonezilla to copy one partition or drive to another, but if your original configurations is actually spread over two or more partitions, even if just in part, than a one partition copy is not going to get everything needed.

---

### Post by oldefoxx on 2010-03-03
Took another look at Clonezilla.  No matter what screen resolution I specify, what shows up is extremely small.  Have to get right up to the monitor to read it.  I tried following the three choices out a bit, and decided that it might do after all, but then found that it only permits a maximum of two internal hard drives, and I am using three.  Can't blame them that much, seeing as most PCs sell with only two internal slots for hard drives, but you can get another one or two in there if you want.  Trick then is to beef up the power supply and make sure you have adequate cooling, meaning sticking in another fan or something.

Did some more checking online, and found a couple of posts that indicate that rsync will do the job just fine.  Lots of parameters involved, but I have it on their advice that you can probably do the whole thing as simply as this:

sudo rsync -ax --exclude=gvfs / /media/disk/

Something a bit buggy about copying or deleting the .gvfs folder and contents.  Some suggestions on how to work around that, but I just ignore the error when it occurs.  If you want to replace what already exists on the destination partition, you can use something like this:

sudo rm -r /media/disk/

or format it again (gparted is good for this), or if you just want to replace matching folders and files on the target partition you can add this to the rsync command:

sudo rsync -ax --delete --exclude=gvfs / /media/disk/

Others use the tar gz command, which works, but more for creating an archive file, or putting its contents back.  Another big advantage with rsync is that you can actually keep the contents of two partitions or folders synchronized to each other, and one of them can be remote, or just networked to the PC where you want to do this.

The gparted ISO image that you can download and burn to a CD actually seems to support more file system formats than the version you download and install as part of your Ubuntu setup.  Most notable is that it has the ability to format a partition to any of the file systems associated with Windows.

Here is a problem that can up and bite you if moving from an older PC to a newer one is that before Vista, Windows did not natively support large hard drives.  For Windows 2000, there was a fix added in SP4.  This was at the same time that a similar fits was added to XP in its SP2.  Now with XP, there is a method of creating an install CD that has the fix already in it, but you have to read up on Bart's PE to learn how to create that CD.  Similar methods have been tried with Windows 2000, but while Bat's method works with Win2k up to SP3, I could not find any way to embed SP4
into it, just add it to the disk.  And without SP4 included, Win2k cannot properly deal with large hard drives.  Now there has been some mention of a USP5.1, which does not come from Microsoft, and discussion of how it finally whips this problem.  Trouble is, there are no details on how to put it all together, and USP5.1 is still out there, but hard to find.  I think the last place I saw it was on Softpedia.

Why mention this on a non-Windows forum?  As a favor to anyone that wants to go for a dual boot setup, possibly with a new machine or with much larger hard drive(s).  You leave it to Windows to be the last installed, you can be in for a rough time.  What I found seems to work best is to wipe the hard drive(s), then go through a Windows install, and put it as the first partition on the first and maybe the second hard drive.  Heck, make it the first partition on a third drive too if you want.  You have to limit the partition size though, and I usually find that 40 GB - 60 GB makes for a good size.  I've gone up to and over 100 GB, but there always seems to be problems later when you do this, not sure why.  Format it as NTFS, install your Windows, and update them if you have time for it.

Next step is to partition and install Ubuntu or whatever you want to use in its own partition.  I would go with Ext3 in most cases, because there is at least one driver out there for Windows that will let it see, read, and write to Ext2 partitions, which are the basis of Ext3, just without the added journalling feature.  Ubuntu can of course see, read, and write to the ntfs partitions because of the ntfs-3g drivers.  This gives you a way to share between the two OSes later.

Like I said, there seems to be a problem with multiple installs of Ubuntu, as I think the Installer looks to see what is already there and just uses it again if found in another partition.  That's not what I want it to do,
and I can't swear that this is actually what is happening, but it is a hinderance.

It comes to mind that if I install Ubuntu once, then use something like rsync to copy that partition to others, I could create multiple instances of root, one in each partiton, by doing this.  But more than likely, all of them would relate back to the first partition for other folders that come after root, most particularly /home.  Since /etc/fstab only addresses where root is, and swap, there has to be some other place that spells out which partition(s) hold the other folders.  And I don't know where that is.

So how can I avoid having multiple installs borrow from prior installs?  The best way might be to first rename all the folders directly under root
for each of those installs so that the installer cannot identify them readily.  For instance, my /home folder on my first install might get renamed /HOME temporarily, until all the installs are complete.  Since I am running from a LiveCD for each install, I have the option to make such changes before actually initiating the install.

But that brings to question what would be the best way to do this.  The problem I already see is that many commands have to work around ownership and priveleges issues, which is easiest to do by being root or becoming what many call super user, but in doing that, you usurp ownership and the rights associated with folders and files, and those do not get restored automatically.  Heck, I don't even know where you would find information like who owns a certain file for folder, or which group has access to it.  That info has to be in there somewhere.

Now what if I created a special folder, call it "/r", and then issued a command like this?

rsync -ax --exclude=/r / /r/

What I am trying to avoid is where I might start with the /boot folder and copy it into /r, then /bin would get copied under /r, and so on, until I get to /r itself, at which point everything starts getting copied over again but further down in the folder tree, until I run out of disk space.  The --exclude is suppose to keep that from happening. Maybe it will, but this is only a copy process, the originals are still left in place, with their original names, and the installer has the same problems going forward.

So I guess the real question is, can I move or rename the first rack of folders under root (/) quickly and without sacfificing ownership and priveleges for each, and then reverse the process later so that I get back my original arrangement?  Now if that is not my only problem (I mean the installer might be just grabbing this or that partition and designating them for use as /home or whatever anyway), what would be a method that would work?  I mean I see where I can just set up one Ext3 and one swap partition each, install into it, back it up someplace else (like an external drive), wipe out that partition (no longer marked as for use by Linux), and begin all over again with another partition.  But does it really have to be that hard to just have one partition associated with each install (aside from swap, that is)?

it's one of those areas of uncertainty that you can fall into when you try to go a step or two further on your own.  My own fault you might say, and I won't argue that point, but it is something I have to ask at this point.

---

### Post by oldefoxx on 2010-03-22
I reported this as a problem against 9.xx awhile back.  I never keep up with comments added to bug reports over time, or final conclusions.  If they want to do something about it, they have enough data from me to at least start on it.  The rest is up to them.

The problem I reported is that if you try to install Ubuntu into two or more partitions independently, confining all settings to the one partiton you select as root (/), the subsequent installs will "borrow" settings from the one or more installs done previously, meaning the installs are no longer independent of each other.  To verify this, use apt-get install gparted, then go under System/Administrative/Partition Editor and loog at your partitions after the second one is complete.  Most likely you will find one marked as / for root, but another named as boot, even though you did not designate a separate boot partition.  The more installs you make, the more settings, such as /home, are taken away from the new install's partition.  And reinstalls to fix the problems just compound them.

Sure, if you are only doing one install that should not bother you.  But what if you have a working version of Ubuntu, and just want to install the next Alpha or Beta version to get a feel for it?  It would not bother you that the second one crosses over onto the first, and maybe compromises it?
And there seems to be no way to prevent it?

That is the reason I bring it up again.  I am trying to find a way to prevent this from happening.  The only way I can see to do it is to take the first install and completely eliminate it, or make it so that none of the essential folders like /boot, /bin, /svc and so on are recognized by the installer for the second effort.  I looked at the flags, and even though one is named hidden, that only seems to impact MSDOS and Windows.

So technically, I can either back up a whole partition, delete it, install a second one to another partition, then restore the first one to its partition, and have two at once, or I need some method of renaming all the folders at the / level to not be what they say they are, then name them back when the second install is finished.

Some good solvent methods for doing either of these would be welcomed.  Of course it they just fixed the installer not to to jump out to any of the partitions marked not to be used would be ideal, but who knows if or when that will ever happen?

So first question:  How can I simply rename all root-attached folders like /boot or /bin to include another letter or number like /r-boot or /r-bin, or even /boot0 and /bin0, then name them back later?  

Second question:  How can I just flag a partiton not to be used or checked by the installer during the install process?  And oh yes, if you ever tried a repair of an install, and it was not the first one, expect that your efforts will likely effect any other Linux installs on the same PC.  Not just Ubuntu, you understand, because Ubuntu shares many common naming convensions with other versions of Linux.

---

