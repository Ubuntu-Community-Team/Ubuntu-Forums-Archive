---
title: "[SOLVED] Upgrade to 8.10: Only 137 GB recognized"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by Average Joe on 2008-10-06
Yesterday it was very rainy and I decided to upgrade my Ubuntu 8.04 to 8.10 beta. That was a mistake.

Intrepid Ibex (8.10) beta does not recognize my full hard disk. I have a 160 GB hard disk in my laptop, and only 137 GB was recognized. I have [experienced]("http://ubuntuforums.org/showthread.php?t=851374") this with [several]("http://mepislovers.org/forums/showthread.php?t=10551") Linux distributions now, and the fact that Ubuntu always did it right was one of the reasons to use this nice distro.

I know that the problem is most likely that my bios does not support [48-bit LBA]("http://www.48bitlba.com/"). I already flashed it with the latest version, but that didn't help. However, so far Ubuntu has always been overriding the bios, and detected my full hard disk correctly upon starting. Up to 8.10, that is.

I am afraid I will have to look for a different distro in the future, since upgrading doesn't seem to be an option for me any longer.

Does anybody out there has a clue how to fix this?

---

### Post by maruthi_s@infosys.com on 2008-10-06
[COLOR="Blue"]
How did you do the upgrade ?
[/COLOR]

---

### Post by Average Joe on 2008-10-06
I have done the upgrade to Ubuntu 8.10 beta with Synaptic. Just with the GUI.

---

### Post by Mr. Man on 2008-10-06
this might have to do with the pations. or just the file that u downloaded takes up that space and therefore isnt available so it doesent show. (example: if your operating system takes up 5gb buy your hard disk has 20gb on it. it will only show the 15 that are available to you for use. do the math). it could also be that your computer's hard drive isnt fully used. say you have 20gb on ur hard drive but your partion (the part of ur hard drive that you gave to the operating system to use) is only 18gb it probably wont show you those extra 2gb because it doesent have acces to them. you can figure this out by going to system > administration > Partition Editor. here you can see how big ur partions are. if its not there u can get it at applications > add and remove > and just type in Partition Editor. you'll probably find it.

(for "maruthi_s@infosys.com" u can download it at [www.ubuntu.com](www.ubuntu.com), read all about it there. Its easy to find so that wont be a problem.)

---

### Post by Average Joe on 2008-10-06
I am pretty sure it is not the partitioning. I have four partitions on my hard disk:
sda1: 10 GB, containing a new fresh installation of Ubuntu 8.04.
sda2: 10 GB, containing my messed up Ubuntu 8.10.
sda3: 1 GB, swap
sda4: 140 GB, home, containing all my files.

If I do an```
sudo fdisk -l
```on Ubuntu 8.04, it says that my hard disk is 160 GB. If I do the same on Ubuntu 8.10 it says the hard disk is only 137 GB. That doesn't make sense.

Also, I upgraded from Ubuntu 8.04, that did recognize my full disk. Then I upgrade, while leaving all partitions untouched, reboot, and suddenly my hard disk is 137 GB. This gives a problem, because it cannot find my full sda4 any longer.

I am not talking about available space here, but total size.

---

### Post by Average Joe on 2008-11-03
In case somebody is still interesting in this topic and stumbles upon it: I "solved" my problem by doing a fresh install of Ubuntu 8.10.

Strangely enough I didn't encounter the problem then. Maybe it is because I did the upgrade before the final release of 8.10, and there was still a big in the release candidate. I don't know.

Anyway, the problem is solved now. My entire hard disk is properly recognized with Ubuntu 8.10.

---

