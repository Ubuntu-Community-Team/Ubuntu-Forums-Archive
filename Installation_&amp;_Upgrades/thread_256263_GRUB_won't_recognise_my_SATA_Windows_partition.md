---
title: "GRUB won't recognise my SATA Windows partition"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by mangoHead84 on 2006-09-12
My System:

1 x 20GB HD, Primary, IDE. With Ubuntu 6.06 installed.

1 x 80GB HD, Secondary, SATA. With Windows installed.

My Problem:
Firstly when installing GRUB did not automatically detect my SATA Windows partition. 

So then I went to modify the menu.lst file. I added the lines

title       Windows XP
root        (sd0,0)
savedefault
makeactive  
chainloader +1

after the line:

### END DEBIAN AUTOMATIC KERNEL LIST

The menu item comes up but when i try to select it it gives me the following error:

root (sd0,0)

Error 23: Error while parsing number

Press any key to continue...

If anyone knows how to solve this problem it would be greatly appreciated. Also if anyone knows how to get the GRUB command line to display all the partitions it can find that would help me out.

---

### Post by confused57 on 2006-09-12
A Windows entry similar to this may boot your Windows drive:

```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```


I'm not sure what you mean by grub displaying all your partitions(if you mean other OS, they can be added manually to menu.lst)...you can see a list of your partition table by opening a terminal and entering:

```
sudo fdisk -l
```
The -l is a small "L".

---

### Post by mangoHead84 on 2006-09-13
I tried altering the menu.lst file the way you suggested, with the following results:

root(hd1,0)
Filesystem type unknown, partition type 0x7

Error 11: Unrecognised device string

When i asked about listing all the possible drives and partitions, i wanted to know how you could get GRUB (from the GRUB command line interface) to list all possible values for hard-drive and partition when you call root (harddrive,partition). i.e. all of the hd's and partitions that GRUB sees, not linux. I don't know if there is a difference and there definitely shouldn't be, but in ubuntu my secondary hard-drive has the name sd1, whereas GRUB doesn't recognise this hard-drive number.

---

### Post by confused57 on 2006-09-13
I think this thread may be relevant to your problem:

[http://www.ubuntuforums.org/showthread.php?t=234281](http://www.ubuntuforums.org/showthread.php?t=234281)

Here's an excellent site explaining grub:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

