---
title: "Need to install windows from DVD with linux booting"
date: 2010-04-12
forum: Installation &amp; Upgrades
---

### Post by Mark271 on 2010-04-12
Hello

   I have a problem where I want to install windows on a system with ubuntu already installed.  I rezised the partition so that I have space to install windows.  The problem I have is my bios.

If I set the bios to load the cd first then HD then the drives will not show in the windows install.  What I need to do is have the bios to HD first CD second but not boot into ubuntu. Is this possible?

Thanks Mark.

---

### Post by Mark271 on 2010-04-12
Ok could not get it working so remove the partition but now I still have the grub loader and now boots to grub rescue.  How can I remove this so it goes to boot from cd without have boot cd first in the bios.

---

### Post by ronnielsen1 on 2010-04-12
I assume that you created a fat32/ntfs partition from ubuntu. My experience with this method is that windows doesn't recognize the partition and it's better to have unpartitioned space and let windows do it's own formatting.

> If I set the bios to load the cd first then HD then the drives will not show in the windows install. What I need to do is have the bios to HD first CD second but not boot into ubuntu. Is this possible?

If you set the bios to cd first AND have a windows cd/dvd in your drive it should load the windows disk

---

### Post by Mark271 on 2010-04-12
No I did not format the disk in ubuntu.

I had this problem when I first installed windows 7 it would not detect the drive if the bios was cd first I had to set HD first then CD and then the windows install would detect the drive.

I am now using a until to do a low level format this will hopefully fix the problem.

---

### Post by Mark Phelps on 2010-04-12
Text removed -- posted too late.

---

### Post by ronnielsen1 on 2010-04-12
Sure you have your cable right and jumpers. Does bios recognize the drive as master?

---

### Post by Mark271 on 2010-04-12
Yes it is setup correctly as I had linux installed on the drive and I have had windows installed on the drive before.  The low level format tool detects the drive and is currently formating the drive but as it is a 1TB drive its taking a while.  It is just windows wont detect the drive if the bios is not set to load from HD first.

---

### Post by ronnielsen1 on 2010-04-13
any luck?

---

