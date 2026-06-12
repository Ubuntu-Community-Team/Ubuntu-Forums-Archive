---
title: "Partitioning my drive that already has ubuntu?"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by cedavis8 on 2008-03-31
I would like to get Windows on my full Ubuntu gutsy gibbon hard drive but i can't find any way to partition my ubuntu drive...I would like to keep my ubuntu installation and make an NTFS or even FAT partition so i can get windows on my computer...please help me...

---

### Post by Pumalite on 2008-03-31
You are better off running Windows in a Virtual Environment.

---

### Post by cedavis8 on 2008-03-31
Hmm? what do you mean? with wine?

---

### Post by stefangr1 on 2008-03-31
No, he means using a virtual machine with vmware-server or virtualbox. With these programs you can use windows xp as a program within your linux machine.

However, you're not always better off with these programs, you need a fast computer, and it's not suitable for gaming. The faster P4's with at least 1GiB RAM are a minimum I think, but if you have a modern dual core with a few Gigs of ram I agree with the previous poster that it's the best solution.

---

### Post by Pumalite on 2008-03-31
How about this:
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by markjensen on 2008-03-31
I think that if you boot your Ubuntu CD as a LiveCD, then you can make sure your partitions are unmounted and you can resize one and shrink it down to make room for Windows.

Windows will overwrite the MBR, and you will need to re-install GRUB, and possibly manually add a Windows entry.

---

### Post by cedavis8 on 2008-03-31
I have a Intel Core 2 Duo processor (2.66 GHz) and 2 GB of RAM. So i'll check it out.

---

### Post by stefangr1 on 2008-03-31
I have the same processor and RAM, from pressing the start button (in vmware) to opening office and writing the first letters in an MS-word file takes only 15 seconds! With vmware-server you can even copy and paste between windows and linux, and if you make a backup of your machine you can just copy a new one if something goes wrong with virusses etc..

---

### Post by cedavis8 on 2008-03-31
OK :D I'm gonna get it then

---

