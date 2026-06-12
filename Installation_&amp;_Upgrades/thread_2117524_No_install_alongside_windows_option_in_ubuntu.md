---
title: "No install alongside windows option in ubuntu"
date: 2013-02-18
forum: Installation &amp; Upgrades
---

### Post by Terrow on 2013-02-18
I tried to install ubuntu 12.10 alongside windows 8 but when I get to the installation type screen I don't have any option for installing alongside windows 8.Ubuntu says I have no os and my partions appear as free space.What can I do?(tried to shrink a partition but is still only free space)

---

### Post by darkod on 2013-02-18
Looks like some error in the partition table so uubntu can't see the partitions correctly (and win8 on them). If the disk had gpt table and you converted it to msdos with windows, it doesn't delete the backup gpt table, so linux tools get confused.

If this is the case, you can remove the unneeded backup gpt table with fixparts:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

It can also help fix other errors in the table, depending what they are.

You might have overlapping partitions, or similar.

Or if the disk has been used in fakeraid before, it has meta data remains. Windows ignores this but ubuntu doesn't and the  installer ignores the disk. In this case meta data is removed from ubuntu live mode with (assuming the disk is /dev/sda):
sudo dmraid -Er /dev/sda

---

### Post by kedar5 on 2013-02-19
If you want to install Ubuntu inside windows, try this thread - 

[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

> 
 If your CD drive is D: you can go to a command line and run:  

D:\wubi.exe --force-wubi 


Regards.

---

### Post by darkod on 2013-02-19
> **kedar5 said:**
> If you want to install Ubuntu inside windows, try this thread - 

[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)



Regards.

The OP said along side, not inside. Wubi is only for a short try anyway and works virtual inside windows, if you are decided to use ubuntu I would avoid wubi.

---

### Post by oldfred on 2013-02-19
IF Windows 8 is pre-installed you have to have gpt partitions and wubi does not work with gpt.

Is system an UltraBook or Intel SRT? That uses RAID.

---

