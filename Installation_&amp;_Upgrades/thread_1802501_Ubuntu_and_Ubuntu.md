---
title: "Ubuntu and Ubuntu"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by Al Eastman on 2011-07-12
I have installed Ubuntu 9.04 alongside Ubuntu 11.04. I would like to remove the earlier version and use the full drive for the newer version. I would like to remove the partition without making any changes to Ubuntu 11.04. Any help would be appreciated. Please note: I do not have Windows at all, and do not want it either. Many thanks.

---

### Post by Bucky Ball on 2011-07-12
Welcome. 

Your only issue with this is that you might kill grub in the process of  deleting 9.04 (as it is probably controlling grub if installed first).  To fix this is straightforward. Use 'Boot-Repair'.

[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

Run this in 11.04 to install the 11.04 grub. Boot Repair, once installed  can be found in Applications>Accessories. When you run it you will  be confronted with the gui I have attached. Click yes, install grub.  Done. Reboot and you should find the grub looks a little different. If  so, 11.04 now has grub control.

Now, boot from a LiveCD, choose 'Try Ubuntu', go to System>Administration>Gparted, delete the 9.04 partition, expand the 11.04 partition into the free space you created by deleting the 9.04 partition, done.

This has to be done with all partitions you are working on unmounted, therefore you need to do this running from the LiveCD. ;)

---

### Post by Al Eastman on 2011-07-13
Thanks very much for your help. I will follow the instructions and let you know the result. I appreciate your help very much.

---

### Post by Bucky Ball on 2011-07-13
Good-o. Just remember to give 11.04 control of the grub ***first***, and make sure that is the case, then kill 9.04. ;)

If you don't you might not be able to boot to 11.04 (because grub from 9.04, which was running the show, will be missing). That is also fixable but a bit of faffing about to do it.

* I have changed the order around of the instructions in my first post to make it a little less confusing.

** The process of resizing can take some time so you might need to be patient, depending on how much data needs to be moved. As for setting up 11.04, I always run with at least three partitions:

/
/home
/swap

You may want to move and shrink / to the beginning of the drive and make it about 20Gb (heaps) and utilise the rest of the drive as required (/home for the rest and /swap at the end of the drive the size of your RAM).

The choice is yours, but if you need to do a clean install at anytime you can use the existing /home partition without needing to create a new one, and install the new OS into the / partition, which only kills the existing OS, NOT your personal data (although wise to back that up in case of mishap). If you don't have /home on a separate partition, /home will default to being a *directory* inside / (so if you kill / you effective also kill /home directory). Hope you follow me with this, just ask if not.

This is handy if you decide you want to install another Ubuntu; you can use the existing /home for that, too. I have three Ubuntu installs and they all use the same /home partition.

Good luck and let us know how you go ...

---

### Post by YannBuntu on 2011-07-13
Hello

Good help from Bucky Ball, just one little mistake: Boot-Repair, once installed can indeed be found in System>Administration>Boot-Repair (not Applications>Accessories ).

Tip: you can also download and burn "[Ubuntu Secured CD]("http://ubuntuforums.org/showpost.php?p=10084551&postcount=1")", it is a Ubuntu CD that already includes Boot-repair.

See [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) for more information.

---

### Post by Bucky Ball on 2011-07-13
Thanks for that, YannBuntu, my mistake. I am using xfce at the mo and Boot-Repair is in Applications>System as I have slightly different different menu setup to Gnome. ;)

Interesting tip about 'Ubuntu Secured CD'. I'll have a look there (I think Boot-Repair should be in the repos as it rocks!).

---

### Post by YannBuntu on 2011-07-13
Hi,
if you like this tool, you can now vote on Launchpad ("Does this bug affect you?" -> Yes) to ask inclusion in Ubuntu's repositories : 
- of Boot-Repair : [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/806291](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/806291)
- of Clean-Ubiquity : [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/747279](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/747279)

Thanks :)

---

### Post by Al Eastman on 2011-07-19
Thanks to both of you for taking the time and trouble to reply. I did follow instructions and used boot repair. But came up with a new problem and the computer would not start, so I ended up re-installing 'natty'. It seemed simpler and now works like a dream. But thanks once again for all the help.

---

### Post by Bucky Ball on 2011-07-19
No probs. Please mark thread as 'solved' from 'thread tools'. ;)

---

