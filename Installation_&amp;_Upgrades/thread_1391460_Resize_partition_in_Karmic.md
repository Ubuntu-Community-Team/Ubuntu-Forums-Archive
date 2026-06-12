---
title: "Resize partition in Karmic"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by marxistvegan on 2010-01-26
When Karmic came out I made the decision to leave OSX and become fulltime linux.  The one thing I took for granted is OSX's ability to resize a partition to create space for another partition.  I am wondering if this is possible?  The reason is I want to put all my storage data (i.e. papers, pictures, music, etc) into a partition separate from the OS.  I seek to do this so that I can test out Lucid and subsequent alpha's/beta's, any help is appreciated.:)

---

### Post by louieb on 2010-01-26
Can't resize a mounted partition. That means you can't resize the Ubuntu partition when Ubuntu is running.   
You'll need to run Gparted from a live CD. I suggest using the [SystemRescueCd]("http://www.sysresccd.org/Main_Page")

---

### Post by lindsay7 on 2010-01-26
You can also use the ubuntu install disk. You will find Gparted under system/administration menu.  I like to use the Gpared stand alone program. Make a bootable cd of this. You can get it on their web site.  The documentation for the Gparte program can be found their too.

---

### Post by audiomick on 2010-01-26
I've seen quite a few recommendations for the gparted live CD.
The site is here
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by fiklein on 2010-02-14
I had a Karmic install on too little space. If you have a dual boot with Windows, run defragment in Windows to move any files out of the way of an enlarged Linux partition. Then , the easiest thing to do is [SIZE=3]_BACK UP_[/SIZE]_[SIZE=3][/SIZE]_ all your files (wise to do in any partitioning), and from the live CD, run it as if you are not making changes to the system. That is, boot and use the live CD as your operating system. You can then go to:  System==>Administration==>Disk Utility.  Find your Linux partition and Swap partition. Delete them both. This will create free space. Then, just reinstall Ubuntu with the partitioning tool and slider (I find the manual partition difficult) at the size you wish, and restore your backed up files. All done.

---

### Post by oshunluvr on 2010-02-14
Another option that can expand drive space and not threaten your install (as much) is to create a separate partition and move /home, /tmp, or /var to it.

This can prevent having to resize your install partition.

---

