---
title: "Help with Ubuntu 7.10 Install on USB External Hard Drive"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by Orius on 2007-11-04
Hello,
     I have been attempting to install Ubuntu 7.10 on my external USB drive with no success.  Several attempts have all been met with an apparent freeze.  
My Hardware:
Asus Z96J Laptop w/ Intel T7200 and ATI X1600
WD 250GB External USB Hardrive
Partitions:
1) Linux Ext3 17GB (Primary)
2) Linux Swap 3GB
3) NTFS 230GB (Primary)

I am using the Ubuntu 7.10 64-bit LiveCD.

The liveCD boots with not problems, is seems mostly functional.  Gparted seems to crash or fail when trying to run any partition changes.
The installation procedure works fine up until the time to actually format the disk.  A window pops up saying Installation Progress....Detecting File Systems.  The meter at the bottom of the window crawls up to 15% then does nothing.  I have left the system like this for more than 10 minutes and there was no change.  This is not a complete freeze, but there is no activity on the USB HD or by the optical drive.  I have attempted this procedure using a completely unformatted drive and with it formatted as I have noted above.  I have also attemtped using the guided install as well as the manual.  The guided results in a different error, stating that the "The ext3 file system creation in partition #1 of SCS1 (0,0,0) (sda) failed.

Any help/suggetstions would be greatly appreciated.

Thank you,
Zack

---

### Post by cliffdanger on 2007-11-08
Hey there! I was just actually having the exact same problem until I found this!
It sorted out all my problems
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)
I hope this helps!

---

### Post by Orius on 2007-11-09
Thanks for the reply.  I had actually found that page myself, but foolishly read the options to "deselect" as to SELECT, so I was thinking the problem somewhere else.  Will give this a go and report back.

Zack

---

