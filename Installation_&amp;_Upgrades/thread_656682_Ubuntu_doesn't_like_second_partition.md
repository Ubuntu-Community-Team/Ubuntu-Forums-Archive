---
title: "Ubuntu doesn't like second partition?"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by meburke on 2008-01-02
I'm trying to install Ubuntu Desktop on a Dell Dimension 8300. I have a 70GB Windows XP SP2 partition that works very well. I used Partition Commander to partiton the drives and it installs a version of GRUB. This has worked for me in numerous other Ubuntu/Kubuntu installations, so I don't believe this is a problem.

Ubuntu eventually comes up from the CD (after a long period of "inactivity" where the cursor just flashes on the screen...If I hadn't been distracted by some other task I would have cancelled before I got the desktop.)

When I click "Install", I get the choice of "Guided Use full disk" or "Manual". OK, I don't want to use the full disk, so I choose manual. The dialog walks me through to the partitioning and recognizes the Linux partition, but I have to delete it and repartition for the installation to recognize the "/" mount point partition (20GB). I delegate the last 5GB for a "/swap" partition. I get an alert that tells me Windows won't like the sector and cluster size, which I ignore. THEN I get an alert that tells me I haven't created a partiton for "/swap". I choose not to go on at this point until someone can tell me what's really going on.

Kubuntu gets a little wierder: I get all kinds of crazy graphics flashing at me, and "safe graphics" mode just goes dark.

Neither alternative disk seems to help.

Yes (somebody is bound to waste the bandwidth by asking), the install disks check out perfectly.

Any suggestions?

---

### Post by hardyn on 2008-01-02
i am not familliar with  partition commander, but is it applying a filesystem to this newly created partition?

is it possible to simply shrink the windows partition to whatever want, and just use the ubuntu installer from that point to create your root, and swap paritions?  that is the method i have allways used, with no trouble.

(not exactly true, i create the windows partition using the windows installer, i have not actully ever had to shrink a partition, then use the ubuntu installer to process the rest of the disk. and also allow the ubuntu installer to apply grub to the disk)

---

### Post by meburke on 2008-01-02
Actually, Partition Commander was used to shrink the original NTFS partion from about 95GB to 70GB. It works a lot like Partition Magic. I did use PC to create the free space into a ext3 partiton, but I ended up deleting that partion through the Ubuntu dialog and re-creating it.

---

### Post by meburke on 2008-01-02
OH, yeah, I forgot to mention: The monitor that doesn't play well with Kubuntu is a ViewSonic vx2235wm. The Kubuntu alternate disk looks like it installs from text mode (I get past the partitioning by automatically partitioning the free space, which allocates a swap partition), but when the system boots from the drive I get split irregular blocks (white, black, white, black) and a little red flashing cursor in the top left corner. Switching to tty1 (Ctl-Alt-F1) give me a message that uspash tried 1980 x (something) and failed, reverted to 16xx something x something), and the text doesn't scroll up the screen, the cursor doesn't locate after the login prompt, and I can't see to adjust any parameters.

This proves that the OS installs, but there are errors. Switching screens (Alt-F2) and switching back (Alt-F1) locates the display at the right line, but the cursor is still flashing at the top left and the display still does not scroll.

The Ubuntu Alternate disk just hangs.

Any hints? If I telneted in from another system, what would I change to make the display work correctly? (oops, is telnet even enabled? Yes it is! I found out by juggling between screens after doing "cat /etc/services |grep telnet")

Thanks for any help you can offer.

---

### Post by meburke on 2008-01-04
OK, I think the problem for installing to the second partition is solved. Interestingly enough, although I didn't have any problems until I finally got it installed, when I tried booting up into Windows XP I would get a "Blue Screen" and couldn't boot Windows.

I used a free utility named "NTFS4DOS", which I got at bootdisk.com, and ran checkdskg and repaired the errors in my NTFS partition. Then when I started up GRUB failed with "Error 22". OK, I got pissed and simply used Partition Commander (booted from CD) to delete the LINUX partion and Swap partition. After that, GRUB failed with "Error 15". I used an XP installation CD to enter the repair console and used the "FIXMBR" command. Now I can boot up to Windows XP and that part runs perfectly.

The problem seems to be that Partiton Commander, when installed on Windows XP, installs a version of GRUB as the MBR. Ubuntu overwrites this, and corrupts the attributes and settings needed by the XP boot partition. In other words, don't install Partition Commander. Run it from the CD.

Now my problem is limited to the problems with the installation not liking my GeForce FX5200 and Viewsonic VX2235wm combination. I will create another post for that.

---

