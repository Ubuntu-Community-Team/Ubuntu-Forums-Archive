---
title: "/home on another disk."
date: 2005-02-23
forum: Installation &amp; Upgrades
---

### Post by deBaas on 2005-02-23
Hello folks!

Feels great to be a part of the Ubuntu linux community, Keep up the good work!


My problem:
I have ubuntu installed together with win XP on /hda. Dual boot no problem, works fine. But /hda is " just" 80 gig of wich just 10 is for ubuntu. But I do have two other drives: two 200gig SATA disks. /sda and /sdb.
Althoug i tried to fix it when installing ubuntu it didn't work out. I would like to have my documents music etc (which are supposed to be in /home isn't it?) on these disk. Either with Raid0 or just something that creates one big 400gig disk. So i can drop all my stuff in the /home folder (presuming thats correct to do?) where i'll have 400gig of space. 
What to do?

Sorry for my poor English, it's not my native language.

---

### Post by illek on 2005-02-23
1.  Create the partition you want to use on the other disk with ext3 filesysystem

2.  copy your current home directory to the new partition
      

3. edit /etc/fstab to add the new home mount point:

    /dev/<new partition> 	/home 	ext3 	defaults,errors=remount-ro 1 2     

4. reboot

If everthing is OK, then you can delete your old home directory to reclaim the space

---

### Post by deBaas on 2005-02-23
That sounds pritty easy. Worth a try.

Thanks a lot!

---

### Post by tonym on 2005-02-23
If you are working with two such disks it might be worth looking at LVM.   This is more flexible when creating volumes for file systems.  See [http://www.tldp.org/HOWTO/LVM-HOWTO/](http://www.tldp.org/HOWTO/LVM-HOWTO/)   Its a little more messy but not difficult.

Regards

Tony Middleton

---

### Post by deBaas on 2005-02-23
LVM might do the trick but I don't have a clue how to use it or set it up.

---

### Post by deBaas on 2005-02-23
I re-istalled ubuntu to try software raid or LVM (availible in the disk setup) but none works. Everytime ubuntu complains about missing filesystems.

just trying to get something like:
80 gig ide with ubuntu
2x200 gig with ubuntu's /home

somehow it seems impossible.  :-|

---

### Post by misterlizard on 2005-03-13
I had a problem where I had a software RAID-1 on my two SATA drives where the RAID wasn't starting on boot up, even though I'd done everything in the software RAID HOWTO.

For SATA drives to be seen, the hotplug subsystem needs to be started. However, in /etc/rcS.d/ it can be seen that the hotplug subsystem gets started after the raid arrays are started. If you change this so that the hotplug subsystem (S40hotplug) gets run before the raid stuff (S24raid2, S25mdadm-raid) then the SATA drives should be available under /dev and the RAID array can be started.

The following command should do this:
sudo mv /etc/rcS.d/S40hotplug /etc/rcS.d/S23hotplug

then reboot and see if it works.

Of course, this may not be the problem you've been having, but since I've spent 8 hours today (arrrrrgh!) getting this working, I thought I'd share it :)

---

