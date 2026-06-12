---
title: "Mount problem after upgrade"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by asearle on 2011-06-10
Hi Everyone,

I am trying to help a friend who had a problem (power-outage) during an upgrade from 10.10 to 11.04.  Now he finds that grub will come up but the disk won't mount.

I took a look and it seems that the upgrade process has commented out the mounting of sda1 in /etc/fstab.

So I believe that I could fix the problem by editing his fstab file (and removing the commenting out).  However, when I try to open fstab (with vi) it is read only.  I have tried "sudo vi /etc/fstab" but it is also read-only.

Does anyone have any tips for me?  Can/should I edit the fstab file?  Or is there a simpler way to fix the problem (without running a complete install/overwrite)?

Many thanks for any tips or ideas that you can give me.

Regards,
Alan

---

### Post by asearle on 2011-06-10
I am convinced that I've found the reason for the problem:  amendments that the installation/upgrade had made to fstab.  Indeed, there is even an fstab.bak which seems to have the correct entries.

However, when I try to make changes either within fstab (with vi) or try to exchange fstab with fstab.bak I get the message that the file system is read only.  

This is understandable but I really need to know how to override it?

So far I have been working with the command line which is made available (as root I believe) after the failed start (and the failed mount of the hard disk).  Is this the best way to do it?  Or would I have better luck booting with a live CD (either Ubuntu or Knoppix) and editing the fstab from there?  Or would that also be blocked by the file system?

Any tips would be most gratefully received.

Regards and thanks,
Alan

---

