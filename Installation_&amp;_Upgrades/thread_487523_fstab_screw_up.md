---
title: "fstab screw up?"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by KingHanco on 2007-06-29
[http://img440.imageshack.us/img440/3957/screenshotxi2.png](http://img440.imageshack.us/img440/3957/screenshotxi2.png)

I can't unmount at all. ubuntu 7.04

I did install NTFS-3g 1:1.328-1 and it didn't fix it.

I also can't get NTFS-3g to enable my slave drive which I save stuff on.

So how I fix this?

---

### Post by PoltoX on 2007-06-29
try to send the fstab file and post the details message in the errorbox.

//Simon

---

### Post by KingHanco on 2007-06-30
I got rid of NTFS-3g when I done a clean ubuntu install. I think too many hard drives causes fstab reading error. So I quit using it. I have been using my XP to download stuff onto slave ntfs. After that I copy stuff from there onto the ubuntu.

Oh yea that doesn't do anything.

mitchell@pc-desktop:~$ //Simon
bash: //Simon: No such file or directory

---

### Post by acoustibop on 2007-06-30
You need to install ntfs-config, kinghanco; AIR this should install ntfs-3g as part of the package.

Then you need to enable NTFS writing in the NTFS Configuration Tool that will now appear in your Applications -> System Tools menu.

---

### Post by KingHanco on 2007-06-30
I'm not going to install it back because I get an error on unmount and fstab. The unmount and fstab part need to be fix on ntfs-3g. I guest nobody did a test on unmount and fstab when using ntfs-3g. Mount and unmount is fine without ntfs-3g install. I do not know fstab is install or not. After ntfs-3g install will screwup unmount and fstab. I recommend do not use it until it is fix on unmount and fstab when using ntfs-3g.

Did you seen the snapshot?

It is fine without it. [[IMG]http://img92.imageshack.us/img92/4798/screenshotrq4.th.png[/IMG]](http://img92.imageshack.us/my.php?image=screenshotrq4.png)

---

