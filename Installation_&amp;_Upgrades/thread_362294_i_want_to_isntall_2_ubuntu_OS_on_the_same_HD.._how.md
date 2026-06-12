---
title: "i want to isntall 2 ubuntu OS on the same HD.. how to do this?"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by raffytaffy on 2007-02-15
i have 6.10 right now.....however i also want feisty to test out and whatnot... but i dont wanna get rid of 6.10 as ive put alot of hard work into it ( custom kernel, custom gnome etc etc ) . how would i go about installing feisty next to it. this is my partition set up. 
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        7033    56492541   83  Linux
/dev/hda2   *        7034        9352    18627367+   7  HPFS/NTFS
/dev/hda3            9353        9729     3028252+   5  Extended
/dev/hda5            9353        9729     3028221   82  Linux swap / Solaris


hda1 is my 6.10 hda2 is a windows xp install im willing to sacrifice. im guessing both would share the swap partition. can someone give me detailed instructions on how to accomplish this feat? thank you in advance, raf

---

### Post by IgnorantGuru on 2007-02-15
During install, choose to manually edit the partition table (or it will erase the entire drive by default).  Set the mount points for fiesty...
/   hda2
swap    hda5   (yes, they can share a swap)

That will overwrite your XP with fiesty.  Not sure if the installer will make grub see the other Ubuntu.  But if not, you can install grub to hda2, then manually edit menu.lst, adding an entry for hda1 boot (you can get the details from hda1's menu.lst if needed).

---

### Post by raffytaffy on 2007-02-15
so im gona back up current grub lst . and attempt to mout feistys root on hda2 ...now...do i mount hda1 as anything...or totaly leave it out of the install and add the proper entry to grub later?

---

