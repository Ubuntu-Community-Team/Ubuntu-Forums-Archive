---
title: "[SOLVED] Can't access whole hard drive"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Sef on 2008-10-22
My home paritition has 24 GB on it and only 3.6 GB are used.  However,  when downloading Knoppix to my Desktop, it says that the drive is full.  How can I resolve this problem.

---

### Post by lisati on 2008-10-22
Anythinhg hiding in the trash can that could be messing with the stats?

---

### Post by Sef on 2008-10-22
> Anythinhg hiding in the trash can that could be messing with the stats?


When I do ```
gksudo natilus
```, I get this message:

> sef@sef-desktop:~$ gksudo natilus
No space left on devicesef@sef-desktop:~$ 

---

### Post by Polygon on 2008-10-22
maybe try booting up from a live cd and using gparted to check the filesystems? i know i have had problems where the filesystem was reporting itself too small then it actually was.

---

### Post by Sef on 2008-10-22
> maybe try booting up from a live cd and using gparted to check the filesystems? i know i have had problems where the filesystem was reporting itself too small then it actually was.Thank you for your suggestion.  I found the problem.  My hda1 partition, which is root, is is 9.32 GB, and 8.85 GB are used.  What can I do to check why it is that.  I have a second partition for home.

---

### Post by cariboo on 2008-10-22
Check for cached packages in /var/apt/cache/archives. or even easier in a terminal:

```
sudo apt-get clean
```

Also check /boot for extra kernels. Check Synaptic for obsolete installed packages.

Jim

---

### Post by Sef on 2008-10-22
> Check for cached packages in /var/apt/cache/archives. or even easier in a terminal:

 	Code:
 	sudo apt-get clean 
Also check /boot for extra kernels. Check Synaptic for obsolete installed packages.


That helped a bit.  I have 8.68 GB used.   When I tried to go to '/var/apt/cache/archives', I got a message that 'No such file or directory exists.'

---

### Post by Polygon on 2008-10-22
you can again try a live cd and check baobab (disk usage analyzer) and see which directories are taking up the most space

and remember, by default ext3 partitions have space reserved for root, so if you dont have any space left to even delete a file, try logging into root (sudo su)

---

### Post by Sef on 2008-10-22
> you can again try a live cd and check baobab (disk usage analyzer) and see which directories are taking up the most space

Baobab is installed in Intrepid under Applications > Accessories > Disk Usage Analyzer.

Thanks for that idea.  I used it and got rid of some files and all is working ok now.

---

### Post by cariboo on 2008-10-22
That was a typo it should have been /var/cache/apt/archives. :)

Jim

---

### Post by Sef on 2008-10-23
> That was a typo it should have been /var/cache/apt/archives. :smile:

Thank you for the correct version.

---

