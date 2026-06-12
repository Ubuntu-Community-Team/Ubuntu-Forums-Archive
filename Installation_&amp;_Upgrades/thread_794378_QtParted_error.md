---
title: "QtParted error"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by ArsNecardi on 2008-05-14
Hi Guys

I run Ubuntu 8.04 - Hardy Heron and wanted to use QTParted, so I installed it via Add/Remove (later also with the Synaptic Package Manager)
When I try to start QTParted I get the following Error:

Could not launch menu item
Failed to execute child process "qtparted-root" (No such file or directory)

So as I'm new to Linux I don't know what to do.

thx Ars

---

### Post by Pumalite on 2008-05-14
sudo <command>

---

### Post by Kevbert on 2008-05-14
I've raised a launchpad bug on this: [https://bugs.launchpad.net/ubuntu/+source/qtparted/+bug/223852]("https://bugs.launchpad.net/ubuntu/+source/qtparted/+bug/223852") 
This bug has also been reported occurring with Awn and Evolution.
If I get a reply I'll let you know.

---

### Post by IBNubei on 2008-06-12
Hi there,,,

I found this command which worked for me.

Open the terminal and type command:

gksu qtparted

I then was asked for my password and QtParted started!

I will am still testing it out, I can't resize the main partition, but I think that's because I may have to unmount it first, which means I need to boot from a CD!  IBTesting and Practicing!

So far, I love Ubuntu, finally looks like I shall have freedom from the "Ms bum"!

---

### Post by Fhernd on 2008-06-19
Hi!


I had the same problem, but I launched the Terminal and typed: *gksu qtparted*, and now QtParted works perfectly.

Thanks **IBNubei**.


So long!

---

### Post by eshant_engineer on 2009-01-03
Now i used it on 8.10 result - it is running but i cannot access directly from system tools and each time after starting my pc i have to run this to just run it......the fact is that, through it no operation is operational, just a "progress" steady-window is coming with 100% progress whereas terminal is showing-

$ gksu qtparted
Error: File system was not cleanly unmounted!  You should run e2fsck.  Modifying an unclean file system could cause severe corruption.
Error: Could not detect file system.
No Implementation: Support for opening ntfs file systems is not implemented yet.
No Implementation: Support for opening ntfs file systems is not implemented yet.
Error: Could not detect file system.

---

### Post by eshant_engineer on 2009-01-03
.

---

### Post by NowIsAllWeHave on 2009-01-10
Like in the first post in this thread, I installed QtParted through Add/Remove and no errors were reported on the install.  When I try to run it from the menu system, I see it appear on the status bar with the spinning hourglass, but after a period of time, it completely disappears and no matter how long I wait, QtParted never starts.

I tried the "gksu qtparted" in a terminal window that was suggested in a previous post, and indeed the program starts, but as soon as I click on the hard drive to see the partitions, the program says "getting information", and then the program disappears from both the status bar and the screen and it never returns.

I tried an uninstall of QtParted and reboot, then a reinstall of QtParted and reboot, but the result remains unchanged.  I've tried QtParted on a fresh boot with no other programs running on the status bar, but I still get no result from the menu system approach.

When I activate Windows XP through my dual-boot and run Partition Magic 8 (which QtParted is said to be a clone of), Partition Magic shows everything is normal on the hard drive, so I can't verify that there seems any errors on the hard drive that are preventing QtParted from running (besides, I would assume QtParted would report the errors rather than just disappear).

I am using Kubuntu 8.04, since Kubuntu 8.10 gives me only a black, empty desktop on my Dell GX260 with the motherboard Intel video chip, so 8.10 is totally useless until the black or empty screen problem with many video cards (as identified within other forum threads) finally gets fixed in 8.10 (so 8.04 it is!).  I have a 120 GB Western Digital HD which was first partitioned within Windows XP on another computer by Partition Magic 8.  Initially, XP was installed and there were no HD disk errors, and then after the failed attempt to install 8.10 (and a reformat of the partition set up as ext3 for Ubuntu), finally 8.04 was successfully installed in the ext3 partition without any HD disk errors and 8.04 has been running as expected for a new install (well, it's about a week old).  I have 512 MB of memory and a 2 GB swap partition.

I would like to get QtParted to run from the Menu system normally, which I assume is possible but is not yet what I have attained.

---

### Post by silvagroup on 2009-02-13
> I would like to get QtParted to run from the Menu system normally, which I assume is possible but is not yet what I have attained.

Do a right click on Application>Edit. In the left window highlight Syetm Tools. In the right window now right click QTParted. Select properties and change qtparted-root to gksu parted. Close and it will now run from menu.
You will be asked for password, there's probably a way to also circumvent the asking for password but so far it's beyond my Linux capabilities.
Hope this is of some help.

---

