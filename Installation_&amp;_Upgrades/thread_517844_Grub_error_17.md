---
title: "Grub error 17"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by capt scroggins on 2007-08-05
I am getting a Grub error 17 after a fresh install of XP and then Ubuntu. The output of my sudo fdisk -l is:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       13082   105081133+   7  HPFS/NTFS
/dev/hda2           13083       17945    39062047+  83  Linux
/dev/hda3           17946       18188     1951897+  82  Linux swap / Solaris




I have also tried reinstalling Grub from the LiveCD and it said it was successful but I am still getting the error. I cannot burn the Super Grub CD because the LiveCD is in the drive. The error happens soon after POST and I never get the Grub menu where you are supposed to be able to choose your OS. I also checked the menu.lst and it seems to be ok, the Ubuntu install is set as (hd0,1). I am new to Ubuntu so I am not sure where else to check. Any help at all would be awesome.

Thanks.

---

### Post by merlinus on 2007-08-05
Try this from a terminal (Applications/Accessories/Terminal):

```

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

```Substitute your results from the find command for (hdx,x).  It will probably be (hd0,1].

-merlin

---

### Post by confused57 on 2007-08-05
If merlinus suggestion doesn't work(which it should), maybe this thread will help:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

---

### Post by capt scroggins on 2007-08-05
I have already tried Merlin's suggestion although it said it was successful, upon reboot I am still getting error 17. I will try the other link as that is one I didn't find on my initial search of the forums. Thanks for the quick replies. I will post results.

---

### Post by capt scroggins on 2007-08-05
Ok my problem is solved. First in my BIOS my hard drive wasn't on Auto even though I had checked that previously. Next I reinstalled Grub and now it is working. Thanks for your quick replies.

---

