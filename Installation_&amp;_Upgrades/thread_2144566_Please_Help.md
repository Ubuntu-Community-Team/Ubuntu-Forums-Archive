---
title: "Please Help"
date: 2013-05-12
forum: Installation &amp; Upgrades
---

### Post by Michaelw818 on 2013-05-12
I just installed 13,04 on a friends laptop, I as i had done on several of my own computers, inside of windows. Something went wrong and it installed Ubuntu and it appears to have deleted the windows section. I can not find anything related to windows on the computer. Is there any way to recover the windows partition? or is it lost and gone forever. Thank you all

---

### Post by marianoa on 2013-05-12
Are you sure you have deleted the windows partition? If you have I don't think there's much you can do. You can check if the partition is still there with the command

```
sudo fdisk -l
```

see if you can find any NTFS partition

---

### Post by Mark Phelps on 2013-05-12
From what I've read, Wubi (installing Ubuntu from inside of Windows) no longer works with 13.04.  So, if you proceeded with this, you most likely OVERWROTE the Win7 installation.

There are Windows apps that you can use, by downloading and burning various CD images, that might be able to restore the partitions.  One such example is Minitool Partition Wizard.

---

