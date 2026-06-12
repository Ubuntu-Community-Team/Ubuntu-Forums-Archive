---
title: "Completely remove Kubuntu"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by Optiker on 2006-06-15
I'm a noob in Linux skill, though I've been dabbling for some time, so please excuse the stupidities that I may have committed in the following process.  :)

Sorry for the long background (below), but wanted to provide details of what I did that brings me to the question...how do I wipe my Kubuntu and its swap partition clean so I can do a clean install of Dapper? Please keep in mind that I'm a noob level, so need a bit of simple, step-by-step. If you want to know why I'm doing this, the remaining section of the post walks through what I've done and where it stands now.

I had installed Breezy, and after a lot of small fixes, finally had it mostly working: sound, read only NTFS for Windows C-drive partition (operating and programs), read/write for FAT Windows D-drive partition (data), recognizing all other drives, preferred dual boot order, etc. There were still some remaining issues.

During that process, I apparently messed something up because I wasn't able to get into Adept database. Error message suggested updating from terminal, which I did, but still wasn't working. Along the way, it was convenient to use an Ext2 filesystem utility to access my Linux partition.

Yesterday, I decided to try to update to Dapper. While in Kubuntu Breezy, I modified my sources.lst from Breezy to Dapper. When I tried to update, I got a message about the second line in the sources.lst file being bad, so I went back in and commented out the first and second lines - I don't recall what they were, but seem to remember them referncing a CD repository, and since I didn't have the Dapper CD, thought I'd try commenting those lines out. I did that and the update ran, and took a good amount of time to complete as expected (DL over a T1 line, so pretty quick in comparison).

After that, I logged out with the intent of going into Windows to do some pressing things, then back to reboot Linux to check it out. There seemed to be some strange things happen when I logged out, but I didn't write them down - like, Firefox extra sluggish and erratic. When it didn't shutdown and reboot, but stopped at the CL login, I physically powered down, and it shut down Linux as usual before powering off.

When I turned on and launched WinXP, XP was no longer my default boot. Again some things were a little strange, but again, I didn't write them down.

When I tried to go in and change the boot default to XP, from Windows, using Ext2 as I had in the past, it reported that there was no disk in the L-drive, which is my designated drive letter for Ext2 for the Kubuntu partition. From the looks of it, it was no longer seeing my Linux partition at all via Ext2, so I reinstalled Ext2 just to make sure. It showed my Linux partition as L: as expected. I tried again with the same result. From teh listing of drive letters, it appears that what is actually at the L-drive location is one of four "drives" of a four slot, USB card reader that indeed had no card in it. I decided that at some other time, I'd go back and try rebooting Kubuntu and see what was going on.

However, last night, when my nightly backup ran, it choked on that "no disk in drive L" thing again. I will check my backup selections and make sure it's not trying to backup L, and make sure it backs up hte rest of what I need backed up. But in the meantime, ....

Now, I'm not sure what to do. I'm hesitant to try to boot into Dapper for fear that I might somehow have scrambled something that will mess up my Windows partitions. I have most of the most important stuff backed up - data for example, but don't relish going in and having to reinstall my XP system.

Thus...I'd rather do a clean install of Dapper than of XP, so how do I wipe my Linux partition and its swap partition clean so I can do so.

Thanks!
Optiker

---

### Post by murph2481 on 2006-06-15
Use QT parted and delete the partition with linux on it and then recreate.  I use Partition Magic for XP to control my partitions as I like it better but QT parted will do the same thing for you

---

### Post by aysiu on 2006-06-15
I didn't read anything in the middle of your post--it was starting to make my head spin.

Bottom line, you need a clean reinstall.

You can just choose to erase the entire disk, but since you mentioned a Windows partition, I would suggest selecting "Manually Edit the Partition Table."

You may also want to create a separate /home partition, so that if you ever reinstall again, it isn't a pain to backup your settings and files and copy them back over again.
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by Optiker on 2006-06-15
murph...kinda expected that. I do have Partition Magic, but not real confident when it comes to messing with partitions. Seems like there are always choices that I don't understand, so am hesitant to guess. You can see where guessing got me on the current issue!  :)  But, looks like that's my best bet. I'll start down that path and see what I run into. BTW, don't know QT parted, but will look it up also.

Thanks!

ausiu...can understand why your head spun. Probably didn't understand that clean install without corrupting my Windows partition is in fact, what I was asking about - ie, how? Murph has answered that. The rest of the message was background in case it was at all useful in identifying a possible less intrusive fix.

Thanks for replying.

Optiker

---

### Post by aysiu on 2006-06-15
Create a separate /home partition *first*, using the instructions in the tutorial I linked to above.

For reinstalling, follow this tutorial:
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

Select "Manually Edit the Partition Table" and for mount points:

/home for the /home partition. Uncheck "reformat."

/ for the other Kubuntu partition (to be reinstalled). Check "reformat"

swap for the swap partition. Check "reformat."

Pick whatever mount point you want for Windows. I use /windows, but you can use whatever you want. Uncheck "reformat."

The tutorial is based on the Ubuntu installer, but I'd imagine the Kubuntu one is quite similar, just blue instead of orange.

---

### Post by Optiker on 2006-06-15
aysiu...I'll take a look at the tutorial and see if I can understand it. If so, will give it a try.

Thanks!

---

### Post by aysiu on 2006-06-15
Just remember--it's always best to be cautious and ask a lot of questions than to go ahead and do something that screws up your computer and try to fix it later.

If you're not sure what you're doing, post back here.

---

### Post by Optiker on 2006-06-15
Well...I took a look at aysiu's link and decided to leave the home partition for next time around. Instead, I DLed the ISO and installed using his link to help me along. There were some points where it was scary being as I don't really know the process well enough, but decided to try it.

_Almost_ worked flawlessly - in fact, better than when I installed Breezy.

Exceptions:

(1) during the installation, something went by about scanning security something or other and that apparently failed. When I clicked OK, it apparently skipped that step and went on. Sorry I didn't take notes. If anybody recognizes that, would be nice to know what it was about and if important.

(2) when I booted the new installation, one line went by that said something about "open /dev/sdb1 no such file or directory". I think that just means I don't have any sdb devices, only sba...right? No prob?

(3) something went by, and I can't remember now if it was in launching the live CD, closing it, or opening the new installation, where the startup dialog has all the lines with OK at the right of the screen...well, one line had a "failed" but it went by so fast I didn't get a chance to read it and see what it was. I think I recall that there is a log of the startup (and shutdown?" process someplace, but no idea where to find it - someplace in /etc/* I presume?

(4) the default mouse was apparently a two or three button wheel mouse. Mine is a 5 button wheel mouse. The result is that I don't know how to go in and disable the two side buttons (I never use them even in Windows) and it's too easy to inadvertently press one of the side buttons that I don't want. In the setup, I don't see any way to change that. I remember doing it in Breezy, but don't recall how or where. Where do I look?

(5) I tried to install GIMP from Adept - wouldn't let me! Something about can't download and it might break the installer.

(6) I'd sure like to have a little more resolution - came up with max at 1280x768. I recall something about a config file in the X.. folder that I can manually change for other settings, or can go back through the X... config utility. I'd rather manually edit. Can anybody point me to it?

That's for starters..I have sound but haven't tried any mp3s yet, and recall something about needing to use Adept to install other codecs, and I also recall something about enabling the universal repositories by manually editing the sources.lst file. Any pointers on either of those to refresh my memory would be appreciated. Haven't tried printing yet, but HP 6122 should be a no-brainer. Canon iP5200 at home is another animal...on Breezy, had to DL and install a third party driver. Worry about that when I install at home.

Installed Firefox, favorite theme, and imported bookmarks fromFirefox in XP with no probs.

Lots of points...probably should each be a new thread, but we'll start here and followup on any not answered.

Thanks!
Optiker

---

### Post by Optiker on 2006-06-15
Found the sources.list file and uncommented the universe and backport lines. Also, in that file, saw the following section at the end:
-------------------------
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
----------------------------------

Does this have something to do with point (1) in my previous post, and if so, should I do anything about it?

Finally, I mentioned that I had installed an Ext2 file utility to access my Linux partition from Windows XP, but after trying to update my Breezy installation to Dapper, it wasn't seeing the partition. It is now - working nicely!

Any replies on other issues appreciated!

Thanks!
Optiker

---

### Post by silentb on 2006-08-21
This is sources.list how I use it:

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Backports
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) dapper-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
deb-src [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) dapper-seveas all

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main

# kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main

# Bleeding edge wine packages (packages)
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# Bleeding edge wine packages (sources)
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main
deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main

# Automatix
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) kubuntu main




For the resolution you need to change /etc/X11/xorg.conf:

- change monitor parameters to yours
- add correct driver (e.g. nvidia)
- add desired resolutions

Use the search button..

---

