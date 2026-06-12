---
title: "Help! Installer Crashes on Partitioner"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by annie_linux on 2006-06-15
Hi, the Ubuntu 6.06 installer keeps crashing on me and I am looking for any help I can get in order to get my computer running.  Here is the story and everything I have tried:

I have an [hp pavilion ze4560us]("http://h10025.www1.hp.com/ewfrf/wc/genericDocument?cc=us&docname=c00249077&lc=en&jumpid=reg_R1002_USEN") laptop.  Initially, it came with a 40 GB hard drive on which I was running Debian unstable.  I migrated to Ubuntu around the release of 5.04, and subsequently apt-upgraded to 5.10 and then eventually Dapper.  Everything was working fine except the hard drive began to crash and I was forced to get a new one.

I ordered a 60 GB [replacement from Comptick]("http://store.comptick.com/vtc-hd25-60.html").  Their website says the new hard drive is supported by this model of laptop, and indeed, BIOS reads it correctly.  However, when I boot the LiveCD and run the Dapper Drake installer, everything works fine until I get to the partitioner.  If I choose to manually partition the hard drive, it tells me that I have roughly 56 GB of space and then when I go to create a new partition it tells me I need an msdos disklabel.  So...we create an msdos disklabel, but no new partition is created and I am forced to give up and go with the guided install.  The guided install works fine until it gets to about 23-26% and then there is an error while it's copying files to the hard drive and everything crashes.  I filed a [bug report here]("https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/49180") with the appropriate files attached.  I tried running gparted before the install, as some people had suggested in other forum posts, but ran into the same problems as before.  I also tried reburning the CD twice, but no luck.

So then I thought I would use an old install CD from 5.04, the one I originally used to intall ubuntu on my laptop.  The 5.04 CD (and the 5.10 CD) read my hard drive as a Toshiba hard drive with 9007.4 TB of space (which it clearly does not have.)  I tried creating a 60 GB partition on this supposed 9007.4 TB and going ahead with the install, but this resulted in an endless stream of errors.

About this time I learned of the alternate install CD and decided to give it a try.  Using the good ol' text-based installer, I get a bunch of warnings to the effect of:

Buffer I/O error on device hda: logical block 0
hda: drive not ready for command

Sometimes the errors is on block 1 instead. Either way, after a few seconds, the installer boots up as though no problem had occurred and I can get all the way to the partitioner. The partitioner reads my hard drive correctly, 60 GB DOCHIBA, and it lets me manually partition the hard drive.  So I sat up the partitions the way I wanted them, 10.7 GB for / with ext3, 48 GB for /home with ReiserFS, and a 1.3 GB logical block for swap. Then, it creates all the partitions, but cannot mount / and the installer fails and insists that I go back and repartition the hard drive. If I alt-(right arrow) over to another terminal, I get output something like:

udevd-event: create-node: symlink (../hda5)
kernel: Unable to find swap-space signature
kernel: JBD: no valid journal superblock found
kernel: EXT3-fs: error loading journal

(these are my reproductions of the error messages from memory and random scribblings on paper...I couldn't copy and paste them since they are error messages produced by the installer, which failed)

Someone said something on the forums about how there was a problem with udev automatically mounting the cdrom drive or the ethernet in the wrong place and thus making it impossible to mount /. The workaround is to skip setting up the cdrom, etc., partition the hard drive first, and then go back and do the other stuff. I thought this might be my problem due to the bit about udev, but I tried this and it didn't work, same errors as before. 

And finally, I did try booting a Damn Small Linux CD, just to see if I could get a different Debian variant to work and then apt-get dist-upgrade from a different repository into Ubuntu.  The Damn Small Linux CD wouldn't boot though...

So...I'm feeling desperate and demoralized.  This shouldn't be this hard.  What am I doing wrong?! Any ideas would be greatly welcomed and thanks for your help in advance.

---

