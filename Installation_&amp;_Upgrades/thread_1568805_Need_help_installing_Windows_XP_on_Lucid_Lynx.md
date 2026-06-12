---
title: "Need help installing Windows XP on Lucid Lynx"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by Dmikegarcia on 2010-09-05
So heres my problem. I'm trying to install Windows XP off of a burned disc. I can't load it up from the boot menu just because it doesn't seem to want to work. Fairly dated computer (got it in 2004) which has two CD drives. One, which doesn't recognize the burned dvd with the windows OS on it. And the other, which is able to recognize the dvd, and does show up on my desktop. But I'm not exactly sure how to go about installing it. Unfortunately, I don't want to keep Lucid Lynx, I'd rather just go back to Windows. Not sure if I'm able to use Wine for this type of situation. I tried it and got an error message saying "No valid system partions were found." Any help or insight would be much appreciated.

-Derek

---

### Post by oldfred on 2010-09-06
Windows will not see any linux partitions. Windows will only install to a primary NTFS (or maybe FAT?) partition with the boot flag or unallocated space with an available primary partition. You should be able to shrink your Ubuntu partition and make it dual boot.

Use gparted to create a NTFS primary partition and set the boot flag on that partition. Then the windows installer will see it. 

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Dmikegarcia on 2010-09-06
Alright cool. I'll give it a try. 

Thank you.

---

