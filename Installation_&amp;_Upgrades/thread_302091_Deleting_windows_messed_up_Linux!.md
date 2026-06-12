---
title: "Deleting windows messed up Linux!"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by DimitrisC on 2006-11-18
I decided that it was time for me to move to linux alltogether on my laptop.  So i used gparted live cd to delete the windows partitions and resize my linux partition to take up the free space created.  

My problem is that when the procedure finished and i restarted my computer grub was gone and i get an error 22. ](*,) 

I used ubuntu livecd and i can see my linux partition on /dev/sda6 (/dev/sda5 is swap)just fine with all the data i had on.

Is there a way i can make my linux partition bootable again so my computer starts in linux?  I put a lot of effort into getting linux to work the way i want to and i dont want to do it all over again.   Even when we are trying not to use them wind*ws still causes problems!!! :-D

---

### Post by Herman on 2006-11-18
Try re-installing Grub from the Live CD and see if that will cure the problem.

Here's an example in case you need help to do that, or if you don't, someone else reading this post might some day,
                             Re-install Grub with a GRUB shell eg; with Live CD..........................................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

This is not guaranteed to cure the problem for sure, but it's the easiest thing to try first, and won't do any harm.

You probably need to edit /etc/fstab too if you have not done so already, or Ubuntu will boot half way and then halt at the filesystem check. You can press 'Ctrl'+'d' to resume normal bootup if it does. Then delete your Windows partition entries or at least 'hash them out in /etc/fstab. Maybe you already know all about that so I'll just shut up for now unless you ask for more help.
Again, this extra information might help someone else who may find this post some time in the future. We have a lot of new forum members who may be shy.

---

