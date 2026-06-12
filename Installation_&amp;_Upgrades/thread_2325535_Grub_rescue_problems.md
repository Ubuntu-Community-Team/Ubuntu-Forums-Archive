---
title: "Grub rescue problems"
date: 2016-05-23
forum: Installation &amp; Upgrades
---

### Post by juan63 on 2016-05-23
Hello Everyone
I have a problem when I turn on my computer. I I only get a black screen that says grub rescue. I've tried several ways to fix it including "ls" command to try to select the right partition to boot from. I get this message:
(hd0) (hd0,msdos5) (hd0,msdos1):confused:
I tried to boot from msdos5 and msdos1 and always get the "unknown file system" message. 
I read in a forum that Boot Repair could fix the problem so I ran the program form a live USB and it returned that it wasn't able to fix the issue. However it gave me this Pastebin ([https://paste.ubuntu.com/16520040/](https://paste.ubuntu.com/16520040/)). 
If I really understand the text, it tells me that the lubuntu partition I want to boot from is still there. 
Does anyone have an idea how fix this issue?
Really appreciate the time and help!

---

### Post by grahammechanical on 2016-05-23
You have Grub installed into the MBR of the first (only) hard disk (sda) but it is set to look for its configuration files on msdos1 and that is the first partition (sda1). But that is the Windows partition and not the Ubuntu partition..

You do not have a Ubuntu partition. The extended partition (sda2) only has the swap partition (sda5). Ubuntu is no longer installed. And it seems to me that you are also lacking any Windows XP boot files in the Windows partition (sda1).

Regards.

---

### Post by juan63 on 2016-05-23
Thanks for the reply. So I guess it is impossible to recover the data I had installed in Ubuntu right?
The easiest way to go would be to do a fresh install on Ubuntu, and lose all everything I had before?
Really appreciate your help!:guitar:

---

### Post by juan63 on 2016-05-24
I just wanted to tell everyone how I solved this issue. 
Using GParted (from a LiveUSB) I found out that my partitions where overlapped. I used TestDisk in order to fix this issue!
TestDisk is surprisingly user friendly! I didn't lose any data! Right now I've made a backup of all the data and will proceed to make a fresh install of the latest Lubuntu version.:D

One last message for everyone that has any sort of problem, in computers and in everyday life, don't give up! If the first attempt to solve it didn't work try, stop, analyze the issue with fresh eyes and attempt other possible solutions. If nothing really works, at least you now you exhausted all possible solutions and that you are a hard working problem solving human!
Cheers!

---

