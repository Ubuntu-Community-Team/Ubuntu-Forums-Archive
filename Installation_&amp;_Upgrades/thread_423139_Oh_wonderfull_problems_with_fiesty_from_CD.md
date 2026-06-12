---
title: "Oh wonderfull problems with fiesty from CD"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by chuckyp on 2007-04-25
Trying to install fiesty from CD on one of my other boxes.  No matter which variant of the installer I use i.e. alternate, desktop, or net install it locks up when formating partitions.  The system was working fine with a fiesty server install all during development.  I now need to make it in to a another desktop so I'm trying to install from CD and i've run in to this hitch.  Looking for ideas...

---

### Post by charleseddy on 2007-04-25
You could always make a LiveCD of Gparted from here:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Then you can just tell Ubuntu not to format anything, because Gparted will have already done it for you.

---

### Post by chuckyp on 2007-04-25
Well gparted is on the install cd.  I've found that if I run fsck on the partition that was created by the installer it also locks up.  I'm going to try to delete the partition and create my own but i'm sure it will lock when it goes to format it.

---

### Post by chuckyp on 2007-04-25
Going to move on to a different hdd if no one has any suggestions i've changed out the cable and gave the hdd a little nudge this time as well.   If it doesn't work bang on it approach I guess.

---

### Post by Manatherin on 2007-04-25
i had this, if u browse on the cd Places>Computer then into media, it shold detect your other partition (or it did with me) and then continue the setup

---

### Post by chuckyp on 2007-04-25
Its detecting the partitions its just hanging when it goes to format.  If I use a text based installer it hangs at 33%.  If I use the gui installer it hangs at 5% while formating.  I'm trying another hdd right now to see if I get the same behavior.

---

### Post by chuckyp on 2007-04-25
Yeap appears to be the hd at this point.  Oh well time to check samsungs warranty policy.

---

