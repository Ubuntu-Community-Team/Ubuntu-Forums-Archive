---
title: "Grub Sata Help"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by itchanddino on 2006-10-28
I have Windows installed on my primary IDE drive with the slave being for backup.  I want to install Ubuntu on my sata drive, but I don't want the install to touch my Windows drive at all.  What should I do in the last step of the install, I don't want to point grub to hd0, right?  Thanks!

---

### Post by itchanddino on 2006-10-28
Should I install it to sd0 or something?

---

### Post by Herman on 2006-10-28
This method by lha might be just the thing you are looking for, [http://www.ubuntuforums.org/showpost.php?p=677880&postcount=6](http://www.ubuntuforums.org/showpost.php?p=677880&postcount=6)
You can also boot from a non-first hard disk if you press F8 or F12 while your computer is booting up.

Regards, Herman :D

---

### Post by gn2 on 2006-10-28
This may also help: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by itchanddino on 2006-10-28
So what should this read:
title Windows NT/2000/XP (loader)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader +1

for me if hda and hdb are for Windows drives and sda is for Linux? Thanks!

---

### Post by Herman on 2006-10-28
The easiest and best way to find out how Grub sees your disks is to ask grub itself. To do that, press your 'c' key from your Grub menu and follow this how-to, 
Grub's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")

You should be able to do something similar to the examples given there and boot your operating systems up. 
Take notes while you are doing so, because you can use essentially the same commands when you edit your menu.lst file, just add the 'title' at the top, like in the example you already showed in the post above.

Regards, Herman :D

---

