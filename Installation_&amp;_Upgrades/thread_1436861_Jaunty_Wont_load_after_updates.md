---
title: "Jaunty Wont load after updates"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by nickhopkins07 on 2010-03-23
Hi Guys, 
 
I've done a fresh install of Jaunty on my Acer Revo, first things first I thought I'll be good and do the updates. So I've run the update manager and installed all of the updates suggested, and now it wont boot up :(
 
The Ubuntu splash screen pops up and the loading bar gets about a 1/10th of the way across and then just stops.
 
Anyone got any ideas on how I can fix this?
 
Many Thanks

---

### Post by lemming465 on 2010-03-24
One thing to try is a more verbose boot, to see if you can figure out where it is going wrong.  E.g. hit escape at the boot menu stage, and assuming you are using grub version 1, use "e" to edit the boot entry, arrow keys and another "e" to edit the kernel line in the entry, arrow keys and backspace to remove "quiet" and "splash" keywords.  Press enter to complete the edit and "b" to execute the modified boot.  Now you might be able to see what it's doing wrong.

To try and fix it, you need a live CD (or bootable USB stick).  Best if it's a jaunty CD, e.g. the one you installed from.  What you want to do is use a chroot ploy to try another round of updates, possibly from a different mirror.  You'll need to know where your root filesystem lives.  Assuming that your root filesystem is on device partition /dev/sda3, and that you didn't use a lot of other partitions except a second one for swap, this could look like```
sudo -i
fdisk -lu  # check for an ext3 partition at sda3
mkdir /media/sda3
mount /dev/sda3 /media/sda3
cd /media/sda3
ls  # check for root-like structure such as bin dev usr proc ...
for f in sys proc dev; do mount -o bind /$f $f; done
chroot .
aptitude clean
aptitude update
aptitude full-upgrade
exit
cd /
umount /media/sda3
```
Substitute your actual root partition everywhere sda3 appears if yours isn't sda3.

---

### Post by nickhopkins07 on 2010-03-25
Thank you very much for taking the time to reply. I'll give your suggestion a try. THanks.

---

