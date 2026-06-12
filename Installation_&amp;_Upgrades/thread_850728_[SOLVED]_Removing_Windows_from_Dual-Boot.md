---
title: "[SOLVED] Removing Windows from Dual-Boot"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by jonofan on 2008-07-05
Hi guys,

I have been using Hardy for the last month or so and loving it. On dual-boot with Windows. Windows was the first OS installed on the HDD.

The layout of partitions was like so:

60GB NTFS Windows
60GB NTFS Windows (storage)
20GB ext3 Ubuntu
~3GB swap

Basically what I tried to do was wipe everything Windows and expand my ext3 to make Ubuntu the dominating OS on the laptop. I used GParted LiveCD and formatted and deleted the windows partitions. I then went "ugh, doh!" realising Windows has my MBR, which was luckily picked up by GParted and not wiped. So MBR is still there and Ubuntu boots fine, Windows obviously does not.

My hopeful end result:

20GB Windows
60GB ext3 (storage)
60GB ext3 Ubuntu
~3GB swap

So am a bit stuck as for what to do now.. 

I'm not able to expand my ext3 partition in GParted, it doesn't let me, do I have to delete swap first to do this? 

I'm guessing that it is probably better to wipe the lot and start from scratch. So i guess my questions would be:

a. Which should I install first, Windows or Ubuntu?

and b. What is the best way to backup my current installation of Ubuntu? Can I simply copy the "/" directory and paste it over the new install? I'd prefer to do this so that I wont have to mess around with any drivers or settings that I have changed. I did try to copy this directory but it wouldn't let me due to permissions, even running as sudo.

Any help would be greatly appreciated :).

---

### Post by Pumalite on 2008-07-05
Get Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn iso to disk and boot from it
Post a screenshot of your partitions
(it works with unmounted partitions)

---

### Post by jonofan on 2008-07-05
Sorry it was liveCD i was using already.

Screen attached.

---

### Post by Hooya on 2008-07-05
Make sure that the partitions are actually deleted, not just formated, then you should be able to just drag the outlying edges of your existing partitions to where you want them.  Your swap partition shouldn't be getting in the way at all.

---

### Post by Pumalite on 2008-07-05
You have to delete your extended partition first. Then resize Ubuntu to the left and make a storage with the rest. Make sure you respect the rule of 4 primaries per drive. Use Gparted Live CD; not your Live Ubuntu CD.Backup everything before you start. Good luck!

---

### Post by Rallg on 2008-07-05
General note: My previous laptop had XP pre-installed (no installation CD). It seemed to be the case that the starting point of the Windows partition, on the hard drive, was one of the various factors used to determine whether my installation of XP was "genuine."

I don't know whether that is widespread. But if you intend to remove Windows and re-size partitions, itmight be a good idea to keep the starting point of the (former) Windows partition unmoved. If you move it and change your mind, you might have to call Big Bill's Shop to re-validate a reinstallation of Windows. (Yes, they did it for me, no problem, just a nuisance.)

---

### Post by jonofan on 2008-07-05
Thank you very much. Deleting the Extended Partition freed it up for me. I now have one more question regarding putting Windows on the 20GB Partition, can I just install it over the top and wipe the old MBR or is this going to screw things up?

---

### Post by Pumalite on 2008-07-06
You can do it. You will have to reinstall Grub afterwards:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by jonofan on 2008-07-09
Thanks a lot for your help Pumalite. Have installed Windows and re-installed GRUB successfully.

---

### Post by Pumalite on 2008-07-09
You are welcome. Good luck!

---

