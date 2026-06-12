---
title: "Install 7.0.4 on new harddrive"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by SteveMallen on 2007-09-09
I have a windows XP laptop which I have replaced the harddrive. There is currently no OS on the HD. I have the install version of Ubuntu on a CD when I turn on the computer, the Ubuntu desktop loads after a few minutes. I press on the upgrade/install icon on the desktop and the disk starts spinning and the HD is spinning, but nothing happens other than a window with a install header. Then it becomes a large grey box and nothing happens for a 1/2 hour. I there an alternative way to install the OS or instuctions for new HD's?

Steve

---

### Post by trvr on 2007-09-09
There is an "alternate install cd" iso that you can download and burn. It can be found [here.]("http://releases.ubuntu.com/7.04/")

Just curious, what are the specs on the laptop?

---

### Post by SteveMallen on 2007-09-09
Thanks, I will try the other install. The laptop is a Compaq Presario R3000 (AMD) Notebook PC.

---

### Post by Pumalite on 2007-09-09
If it's a new hard drive; use Gparted, make one large partition of the hard drive formatted ext3, then install. Ubuntu will not install on 'unallocated space'

---

### Post by SteveMallen on 2007-09-09
I have setup gparted and when it finally opens the gui, and the GParted app states there are not devices detected.:confused:

---

### Post by Pumalite on 2007-09-09
Make sure everything is OK in the BIOS, check connections,etc. If everything fails, try rescuecd: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page), it has a partitioner that often times succeeds where Gparted fails.

---

### Post by merlinus on 2007-09-09
If it is a new hdd, you may have to do a low-level format first.  Did it come with a utilities disk?

---

### Post by SteveMallen on 2007-09-13
The HD works fine now. The install disc ran for hours with little progress. I think I was able to answer 2 of the 7 questions. Is there a way to install either from a usb or a ghost image?

---

### Post by Pumalite on 2007-09-14
You have hardware or graphics problems or both. Post your specs.

---

### Post by louieb on 2007-09-14
> **Pumalite said:**
> try rescuecd: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page), it has a partitioner that often times succeeds where Gparted fails.

Ditto. That laptop come w/256MB memory. Sometimes thats not enough to run the live CD. Use  GParted to create  a swap partition or use the alternate CD.

---

### Post by SteveMallen on 2007-09-15
Thanks to all that helped. I installed the alternate text only install and it loaded without issues. I am up and running on Ubuntu.

---

