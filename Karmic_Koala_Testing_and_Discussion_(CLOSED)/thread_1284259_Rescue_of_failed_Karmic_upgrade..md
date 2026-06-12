---
title: "Rescue of failed Karmic upgrade."
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jheaton5 on 2009-10-06
Let's get the stupid part over at the outset:  On October 2, I did a full-upgrade from Jaunty to Karmic.  Now I cannot boot into Ubuntu at all.  I did this thinking that the Beta version had been released.  The release schedule said it was scheduled to be released on October 1st.  I should have known that nothing gets done on schedule.  I should have verified.  OK, Beta is now released so I want to try to recover my system

System: I have 2 hard drives sda has the mbr with grub2 and Debian testing.  sdb has Ubuntu and all my data.  I have backed up my data to my server.

Since I have Grub2 set up on sda, I don't want to change it to sdb, which would happen with a fresh install of Jaunty or Karmic.  I went through great agony getting grub2 set up.  

I have read of using a live CD to rescue a broken system.  Is there a how-to or other documentation for this procedure?

---

### Post by mikewhatever on 2009-10-06
As for your information, beta=unstable, unfinished, under development. I'd strongly advise going back to Jaunty and waiting a few weeks after Karmic's final release before upgrading.

---

### Post by jheaton5 on 2009-10-06
Well, I beg to differ.  Beta means testing, almost finished.  I started using Hardy when it went into beta and upgraded to Intrepid and Jaunty when they went to beta.

I upgraded to Karmic while it was still in alpha by mistake.  I know I can do a fresh install, but I would really like to get some experience with the rescue disk.

---

### Post by ghostborg on 2009-10-06
Bummer. Actually I did the same thing to my HP laptop, rolling the dice and the sound and touchpad did not work. So, I downloaded the Beta iso and installed from disc and all is good. The dist upgrade doesn't seem to work so well at this time.:lolflag:

---

### Post by jheaton5 on 2009-10-06
Yea, I'd like to rescue the system if I can, but there is not much in the way of documentation for the process.  I know I can do a fresh install without installing a bootloader, thereby using the bootloader on the Debian disk.  And I can restore my data from back up.  Still I'd like to try the rescue.

---

### Post by mikewhatever on 2009-10-06
> **jheaton5 said:**
> Well, I beg to differ.  Beta means testing, almost finished.  I started using Hardy when it went into beta and upgraded to Intrepid and Jaunty when they went to beta.

I upgraded to Karmic while it was still in alpha by mistake.  I know I can do a fresh install, but I would really like to get some experience with the rescue disk.

If beta is almost finished, what's release candidate, finished, but don't tell anyone?:P I haven't seen a rescue option on Karmic beta cd, nor any other Ubuntu cd, but to be honest, I haven't looked for it either.

---

### Post by Pumalite on 2009-10-06
Not a good idea at this point.

---

### Post by jheaton5 on 2009-10-06
I'll leave it here for now.

---

### Post by jheaton5 on 2009-10-07
I have found this [https://help.ubuntu.com/9.04/installation-guide/powerpc/linux-upgrade.html]("https://help.ubuntu.com/9.04/installation-guide/powerpc/linux-upgrade.html")

This may be a solution to my problem.

---

### Post by heu on 2009-10-08
> **mikewhatever said:**
> If beta is almost finished, what's release candidate, finished, but don't tell anyone?:P I haven't seen a rescue option on Karmic beta cd, nor any other Ubuntu cd, but to be honest, I haven't looked for it either.

according to your criteria if a beta can screw up your system like it did mine then ppl might starting calling the simple announcement of a new release the alpha version. As far as I know an alpha version is "anything could happen" and a beta version is thought of as of having a few (or lots of) MINOR bugs that the developers want the users to help them pinpoint and solve. As for the RC, it should be thought of as "lets see if we have solved everything reported THROUGH the beta program" before lighting up the cigar. If i had wanted to take a bold risk i would have installed the alpha, which i didnt. I went for the beta and it never finished the install process and there's clearly a huge screw up somewhere (seems related to python) that just left a system that'd survived with minor (or not that minor) annoyanced through many upgrades UNUSABLE. Thats NOT a BETA release. Period.

---

### Post by heu on 2009-10-08
> **jheaton5 said:**
> Let's get the stupid part over at the outset:  On October 2, I did a full-upgrade from Jaunty to Karmic.  Now I cannot boot into Ubuntu at all.  I did this thinking that the Beta version had been released.  The release schedule said it was scheduled to be released on October 1st.  I should have known that nothing gets done on schedule.  I should have verified.  OK, Beta is now released so I want to try to recover my system

System: I have 2 hard drives sda has the mbr with grub2 and Debian testing.  sdb has Ubuntu and all my data.  I have backed up my data to my server.

Since I have Grub2 set up on sda, I don't want to change it to sdb, which would happen with a fresh install of Jaunty or Karmic.  I went through great agony getting grub2 set up.  

I have read of using a live CD to rescue a broken system.  Is there a how-to or other documentation for this procedure?



Just in case you havent solved the problem and reinstalling is not an attractive option just like it was with me here is how I restored my system to a working condition.

I upgraded from a working kubuntu 9.04 to kubuntu 9.10 beta on october the 6th. The Upgrade program downloaded everything and everything seemed fine until seemingly the upgrade broke python which seemingly prevented the installer to proceed any further, leaving me with a broken system (it wasnt booting anymore, not the old kernel nor the new not completely installed 2.6.31.12). I downloaded the live kubuntu cd, booted from it, mounted the original kubuntu partition and chrooted to it

example:
running kubuntu live open a terminal
then
sudo mkdir /media/kv
sudo mount -t ext3 /dev/sda5 (or whatever your ubuntu partiton is) /media/kv
sudo chroot /media/kv su


now you can try apt-get upgrade (you can try dpkg --configure -a before)

That should finish the upgrade process but if you, just like me, are getting a nightmare of python dependencies or errors with files like __init__.py, CommandNotFound.py, etc

(not even apt-get -f install was able to solve the dependencies..and yes I tried Aptitude as well)

what I did was, since the install sources had been downloaded, and apt-get would go through the downloading process finely every time, you can go to /var/cache/apt/archives and do

root@ubuntu:/# ls /var/cache/apt/archives


It will give you a list of .deb files that have failed to install. You can install them manually using dpkg -i xxxx.deb starting with python base files and paying attention to the dependency errors, going back to install those packages the one you just tried to install depends upon and so on.

Then you can try 

dpkg --configure -a

and

apt-get upgrade

again, reboot,and you should be fine and have your system back and upgraded

---

