---
title: "Find out which partition to format"
date: 2014-10-07
forum: Installation &amp; Upgrades
---

### Post by kyrawertho on 2014-10-07
Hello,

I want to install Mint on my system. I have one empty partition labeled 'Vista' where I want to install Linux to.
However, in the Linux installer, the labels are not shown. There's just the list with /dev/sda, /dev/sdb, etc. How can I find out which is the correct partition to format?

---

### Post by ibjsb4 on 2014-10-07
Two apps that should see labels.

Disk Utility (may already be installed on the live dvd) and Gparted (have to install it).

You say that the Vista partition is empty.  You could just use a partition editor to delete the vista partition and then during the install of Mint, direct it to use 'Largest Continuous Freespace' (an install option).  I like this method, its a no brainer :)

---

### Post by oldfred on 2014-10-07
If you have multiple Windows installs make sure all your boot files are not in the Vista partition. Windows always puts all boot files in the one NTFS partition with the boot flag.

And if removing Windows but keeping a NTFS partition, create a Windows repair CD or flash drive. You have to occasionally run chkdsk on NTFS and cannot do that from Linux. Linux runs fsck on ext partitions every 40 or 60 reboots.

       Make your own Windows repairCD (not vendor recovery):
[URL="http://forums.techarena.in/guides-tutorials/1114725.htm"]http://forums.techarena.in/guides-tutorials/1114725.htm
[/URL]
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

[URL="http://forums.techarena.in/guides-tutorials/1114725.htm"]
[/URL]

---

### Post by kyrawertho on 2014-10-08
Thanks for your replies. I used Gparted to find the correct partition as it does show the partition's labels.

---

### Post by ibjsb4 on 2014-10-08
Don't forget :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

