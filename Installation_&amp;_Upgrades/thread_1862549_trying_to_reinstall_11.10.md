---
title: "trying to reinstall 11.10"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by fzxjkg on 2011-10-16
An automatic upgrade of Ubuntu failed and I cannot boot. I have an HP G60 laptop running dual boot windows 7 and ubuntu.  The Ubuntu partition is still there, when I try to reinstall I try to select the Ubuntu partition to start the install and I get an error along the lines that there is no root defined, go back to the partition screen and correct this. I am not sure what to do on the partition screen.  I can select the ubuntu partition and select change, but what option do I want?  Any help would be greatly appreciated, i am worried about playing with the partitions.

I have 4 partitions defines, Windows, an NFTS storage partitions shared by windows and ubuntu, a windows recovery partition, and the Ubuntu partition.i

---

### Post by hansdown on 2011-10-16
Welcome to the forum, fzxjkg.

You need to select "/", for root.

Be sure which partition you choose.

---

### Post by fzxjkg on 2011-10-17
So, I select root, not one of the defined partitions, and later get the opportunity to point at the Ubuntu partition to actually install the system files?

---

### Post by hansdown on 2011-10-17
I should have been more clear, fzxjkg.

Double click the partition you want to use.

The partition editor will open.

You'll see a "use as" box. Click the arrow, and choose ext4 journaling,

The box that says "mount point", has a drop down menu, also.

Choose "/ ", and click install now.

This should help.

[http://blog.sudobits.com/2011/09/11/how-to-install-ubuntu-11-10-from-usb-drive-or-cd/](http://blog.sudobits.com/2011/09/11/how-to-install-ubuntu-11-10-from-usb-drive-or-cd/)

---

