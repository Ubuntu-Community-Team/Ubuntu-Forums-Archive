---
title: "Can I have both Ubuntu 32 bit and 64 bit on the same machine?"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by tonysonney on 2011-07-27
Hi Fellow Ubuntu users,
           I would like to have both 32 bit and 64 bit ubuntu installed on the same machine. Is it possible? Am I trying something stupid? I have tried installing 64 bit Ubuntu and 32 bit Ubuntu separately on the same machine. But never tried both on same time.
         I intend to make one partition which has 32 bit OS and the second partition 64 bit. I hope I can use ext4 file system. Should partition 1 or 2 be primary partition? Any thoughts? I am going to do this tomorrow. So any thought before I (ruin ?) the machine would be helpful.

Many Thanks,
Tony

---

### Post by oldfred on 2011-07-27
Should not be a problem. Just format partitions in advance. You need to decide which version has control of the MBR as it will boot first. So install that second. You will have to manage updates in both and rerun sudo grub-update on both unless you want to customize grub to directly boot the other install.

You can share swap as long as  you do not hibernate, but should not share /home as different versions of software may save different settings. If you want to share data create another ext4 partition for data.

I like to use one or two primary partitions, use the third as the extended for many logical partitions and keep one primary available in case I need it sometime.

If you put all your data that is normally in /home into a data partition then you can have /home inside / (root) and keep root partitions at 20 to 25GB.  If separate /home for both installs root can be even smaller.

Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by tonysonney on 2011-08-04
Dear Oldfred,
             Thank you very much for the information. I have managed to install 10.04 64 bit and they both work together. Thank you all.
Cheers,
Tony

---

