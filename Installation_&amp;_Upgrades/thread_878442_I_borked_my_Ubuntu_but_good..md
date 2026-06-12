---
title: "I borked my Ubuntu but good."
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by PaganImmolator on 2008-08-02
Ok so the short and long of it is that I totally messed up my dual boot XP/Ubuntu system while trying to re-install windows. A number of MS related f-ups caused my MBR and partitions to be corrupted (thanks MS for the memories). I managed to get my Ubuntu partition back using some utilities. **The data on my /home is now accessable if I start a LiveCD. **

However I tried to copy the files over to another machine ( I thought I would do that and then just start from a clean slate on the corrupted machine) but I am getting errors that say "you don't have permission" when I try to move them. Funny thing is that about only about 10% of the files are affected by this and its somewhat random. Anywho, I don't know unix well enough to resolve this. I am sure its something simple. It won't let me adjust the permissions on these files. None of these file have been encrypted or locked that I know of. 

Any ideas? Thanks in advance.

---

### Post by wolfen69 on 2008-08-02
while in the live cd, open a terminal and type
```
sudo su
```that will make you root. then while still in the terminal, type ```
nautilus
``` use the file browser that opens to copy over any files.

---

### Post by PaganImmolator on 2008-08-02
Thanks, I didn't think of Nautilus, I will try.

---

### Post by zvacet on 2008-08-03
Did you try to [reinstall grub?]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

---

### Post by Bucky Ball on 2008-08-03
Or even SuperGrubDisk ...

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

:)

---

### Post by Sef on 2008-08-03
> while in the live cd, open a terminal and type
Code:

sudo su

that will make you root. then while still in the terminal, type
Code:

nautilus



Also there is Alt + F2, then type in 'gksudo nautilus' without the quotes.

---

