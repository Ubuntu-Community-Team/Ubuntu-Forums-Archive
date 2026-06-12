---
title: "down loading and burning problem"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by pdlethbridge on 2011-08-09
I've downe loaded 4 versions of Ubuntu and Kubuntu but I've had no success in making a CD. Downloading them at the same time should not have been the problem as I've done it before. This was done after a fresh install of 9.04 Jaunty I had a problem with previous installs I have of an upgraded lucid 10.04 Could several partitions cause a file corruption, I know I had a file problem with Ubuntu one across several partitions

---

### Post by gpost3 on 2011-08-09
> Could several partitions cause a file corruptionNo. Unless your partition table is messed up or your hard drive has too many bad sectors that were not reallocated automatically. In that case, you could get a CRC error. I would suggest [you scan your disk for bad sectors]("http://ubuntuhelpportal.blogspot.com/2011/06/scan-for-and-fix-bad-sectors.html") and also run MemTest86+ for 1 hour to make sure your RAM is ok. If that passes, then try a different mirror - download the iso then burn it to a good quality CD-R.

---

### Post by pdlethbridge on 2011-08-09
Thanks I'll try that

---

### Post by pdlethbridge on 2011-08-09
Is it normal to have the down loads in 2 pieces in the download folded or on the desk top like this
/home/paul/down loads/kubuntu-11.04-desktop-i386.iso
/home/paul/down loads/kubuntu-11.04-desktop-i386.iso.part
/home/paul/down loads/ubuntu-11.04-desktop-i386.iso
/home/paul/down loads/ubuntu-11.04-desktop-i386.iso.part

---

### Post by pdlethbridge on 2011-08-09
When you suggested down loading from a different mirror I thought that if the wireless connection I have is corrupted by software the hospital uses to stop people from browsing porn maybe that would cause a problem as well??? my previos connection was wired to Time warner

---

### Post by gpost3 on 2011-08-10
Kubuntu and Ubuntu are different. Ubuntu comes with gnome graphical user interface whereas Kubuntu comes with KDE. It is a matter of choice. The .part is the temporary file firefox makes when downloading a file.

---

### Post by pdlethbridge on 2011-08-11
I'm pretty sure I know what the problem is. I have a wireless connection in a nursing home that is connected to a local hospital's network They have software to prevent anyone from looking at porn at work or down load a virus.With the tight quality control that Ubuntu uses to protect its down load integrity mp5 sums. if even a comma is missing from the download the cd will not work. Has any one else had a problem with down loads from a wireless connection

---

### Post by Hakunka-Matata on 2011-08-11
Have you checked the MD5SUM?  That will check the integrity of the download?

---

