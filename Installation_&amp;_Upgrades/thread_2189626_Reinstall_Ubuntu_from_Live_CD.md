---
title: "Reinstall Ubuntu from Live CD"
date: 2013-11-23
forum: Installation &amp; Upgrades
---

### Post by kingkratos on 2013-11-23
I have moved my /home to a separate partition from my OS install and am thinking of reinstalling Ubuntu fresh from a Live CD. Is there anything I need to know or keep in mind while doing this to ensure my data is preserved and more importantly, accessible after the reinstall? Does the installer allow me to tell it where to find /home? Also, my /home is encrypted so how can I make sure I set my account up to properly decrypt and access it?

Kratos

---

### Post by grahammechanical on 2013-11-23
I know nothing about encrypted home partitions but I guess that you would need the live session to open/mount that encrypted partition before you start to install Ubuntu. As for a straight forward reinstall with an unencrypted /home partition we choose the Something Else option and then at the partitioning page we

1) Select the partition that we want Ubuntu installed into and click Change.
2) At the dialog box that appears select Use As Ext4 from the drop down menu
3) Tick the format box
4) select mount point as /
5) Click OK.

then 

6) Select the partition that is the /home partition and
7) Click change
8) At the dialog box that appears select Use As Ext4 or whatever file system we are using.
9) We do **NOT** tick the Format box. Repeat **NOT** tick the format box.
10) Select the mount point as /home
11) Click OK

when we are back at the partitioning page we double check that we have not told the installer to partition our /home partition and then we click Install Now. At this point we wish that we had made a backup of our data but it is too late. :) 

Regards.

---

### Post by ian-weisser on 2013-11-23
This seems like a classic use case for creating an unencrypted backup of all your data before beginning the reinstall.

Otherwise you're trusting Ubuntu to recognize that you have an encrypted partition, to correctly judge that you want to preserve it, that the install will not be confounded by unexpected hardware, power loss, or other events, and that after the reinstall your decryption key will still work.
Any one of those goes wrong, and you're out of luck.
And stuff does go wrong on occasion.

---

