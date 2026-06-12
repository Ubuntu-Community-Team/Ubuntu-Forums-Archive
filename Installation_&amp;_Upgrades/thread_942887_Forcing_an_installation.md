---
title: "Forcing an installation"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by Mr.Macdonald on 2008-10-09
I AM NOT INSTALLING UBUNTU just so you know
Also my problem requires some crazy Linx GURU, Linus I need you

I am attempting to install Archlinux, and I managed to destroy my system.

I used the [[COLOR="Blue"]_Installation_[/COLOR]]("http://wiki.archlinux.org/index.php/Install_From_Existing_Linux") from existing Linux. Heres and overview

Basically the guide has you install Arch in the folder /newarch using the archlinux package manager. At the end I figured (incorrectly) that i was supposed to delete every thing but the /newarch folder and move its contents into /. After deleting everything but /newarch I realized that I had deleted Bash!?!?!?!

Now I am booting off of a Ubuntu Live disk because the Archlive didn't work. I still want Arch, and I managed to edit and set my fstab straight, and moved the /newarch to /, not the live disks / but the drive where / resides. Basically I got the drives to the point I think they should be, but look where I got me.

So now that I think I can boot my system, I restart and I got a Grub Error 15?? I believe (not sure) that it means that Grub doesn't know where to start the boot. So I would need to make a drive bootable. But I also managed to make this harder. I have partitioned my drive and now have a different partition for /boot /tmp /home / and /data (I already setup fstab for this and moved appropriate files to the right partitions). 

So ... what now. Do I make my /boot partition bootable or the / partition, and how? I would really not like to reinstall Ubuntu. But reinstalling Grub or something else is fine.

Thank You for saving my system!!

---

