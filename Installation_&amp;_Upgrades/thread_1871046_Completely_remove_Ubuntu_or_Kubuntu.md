---
title: "Completely remove Ubuntu or Kubuntu"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by Don Vosper on 2011-10-28
Had Kubuntu working. Upgraded to 11.10.
Had problems with the various windows and eventually lost the main menus.
Tried reinstalling 11.1 with new cd but it failed. It seems that if I have an existing system I can't install over it amd I've now run out of hard drives!
Tried installing 11.04 again but that didn't work either. I ticked the box saying "use whole disk" now it tells me that I don't have 3.8 gig of space needed to install.
Is there an easy way of completely cleaning this hard drive and starting again?
Don

---

### Post by vicshrike on 2011-10-28
Have you tried reformatting your hd before installing? Mind you that means that you will loose all your data, or do you have a backup maybe?

---

### Post by WasMeHere on 2011-10-28
Hello Don Vosper,

Are you willing to wipe the disk? Do you have a backup of your private files?

In that case it is easy. Run a live session with one of your installation CD or USB drives! Do not mount any partition on your hard drive(s)! Start Gparted and delete all partitions! Then you can make new partitions with Gparted or let your 'installation wizard' do it during installation or restore your old system.

Have fun finding out :-)
Olle

---

### Post by Don Vosper on 2011-10-28
Thanks for the replies.
I have nothing I wish to save on this hard drive.
Do you mean the Kubuntu CD?
Where do I find Gparted please?
Don

---

### Post by WasMeHere on 2011-10-28
It is in the Administration menu (when you run it ***live***). You can also call it from a terminal window
```
gparted
```

---

### Post by Don Vosper on 2011-10-31
Couldn't work out how to do it that way but went into the system administrator and found that I could remove the partition that I had created.
That worked ok and I was able to re-install 11.04.
Cheers
Don

---

### Post by WasMeHere on 2011-10-31
When you feel that the problems of the thread are solved,
please mark it SOLVED

Have fun :-)
Olle

---

