---
title: "Grub 2 lost W2K after Kubuntu 11.04 dual boot install"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by pwrcul on 2011-07-04
I just installed Kub 11.04 on 866MHz, 500MB 10 year old system.  There are two drives.  I left the 2nd (Win2K E:) as a place for storing backup images of the Win2K with DriveImage 7. 
I made a clonezilla image of the Win2K C: drive a couple weeks back. So if I have a disaster I could restore the clonzilla image and then replace it with Friday's DriveImage 7 backup.
But you know I don't want to do that and if I need to I want to be successful on a 2nd try at dual-boot.

I modified etc/default/grub so I have a "#" now in #grub_hidden-timeout=0 so I can see the boot screen and to my horror Win2K is a no-show.
Is there a way of fixing that?

I used Kub i386 ISO and chose the "manual" partition option for the 80MB C: drive.  I changed sda so the first 40 MB became sda1 primary, first, "do not use"  assuming that is where Win2K is (should I have used a partition manager first?)
I made another 37999 sda5 formatted as ext3 with / mount point and another 1998 swap.
 
Suggestions appreciated.

---

### Post by pwrcul on 2011-07-05
I am looking for any suggestions for my next try at dual-boot, e.g., on repartitioning first, etc. as after trying to mount sda1 as ntfs without success ("NTFS signature missing, not valid as NTFS"), I am running Clonezilla now, overwriting sda (restoring Win2K's C: drive).

---

### Post by Roger49 on 2011-07-05
Hi,
Not altogether sure this is your problem, but:
On my 10.10 installation, a program called "os-prober" runs on installation, but is not installed. I had to run "update-grub" and my Windows installation disappeared.
Downloading "os-prober" from Synaptic and running "update-grub" again fixed it.
Good Luck!
Roger49

---

### Post by pwrcul on 2011-07-07
Thanks, Roger49.

I will keep os-prober in mind for the next time.

When I restored the Win2K image with Clonezilla, it did not find grub but noticed an NTFS boot partition and adjusted the filesystem geometry for it and ran ntfsfixboot so it may have fixed part of the reason kubuntu install failed to find Win2K. I hope so.

I will also look into doing a proactive repartitioning before I try.

My recovery plans went awry because the version of Drive Image 7 I had was purchased over the web without a CD 7 years ago.  Since the product is obsolete, I did a manual restore of newer files with its image browser from the DI7 image I had made several days before after the Clonezilla image from 3 1/2 months ago completed.

To my surprise Amazon listed two people offering to sell the CD version of DI7 so I sprung for one of them and see if it will work before I try again.  Every time I looked before I came up empty handed.

I will also run Clonezilla immediately before I try Kubuntu so I have in a USB drive a clone I just can overwrite.  Unfortunately, Clonezilla does not let you recover individual files.

---

### Post by Blasphemist on 2011-07-07
What you needed to have done was shrink the windows partition and use the unallocated space that creates for an extended partition that will be home to ubuntu and swap. I recommend that you look at herman's dual boot site with an eye toward learning about the partions. [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

I wasn't smart enough to do that before I first installed ubuntu. I did do that before I made my next partition changes. I installed 6 more distro's last weekend on this laptop. I had some boot issues along the way but by the time I installed my last distro, oneiric, I had everything figured out. You may learn faster than I did but even I didn't loose a thing.:D

---

### Post by pwrcul on 2011-07-13
Thanks also to Blasphemist for the partitioning reference.

Before I tried again, I did a fresh Clonezilla backup.

Then I used the KDE Partition Manager in the Kubuntu 11.04 live CD--as recommended by  several others on the web.  It has a great GUI.  I divided the space on sda.  It seems the Clonezilla restore had fixed the boot record issue so Kubuntu recognized Win2K.

I did the actual install with the Alternative Kubuntu 11.04 disk, but most likely the live CD would have worked this time also.

---

### Post by Blasphemist on 2011-07-14
So you're solved right? If so, you should mark the thread solved.

---

### Post by pwrcul on 2011-07-16
I inserted a "<Solved>" string in the title, but I doubt it will appear and could not find a way to mark it.  I looked in the FAQ etc. but found no "solved" hits.

Please advise.  It is solved.

---

