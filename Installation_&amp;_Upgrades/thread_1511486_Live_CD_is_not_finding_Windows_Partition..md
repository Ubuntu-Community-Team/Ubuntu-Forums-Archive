---
title: "Live CD is not finding Windows Partition."
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by MoonlitFate on 2010-06-16
I'm trying to set-up a dual-boot (Windows XP and Ubuntu 10.04), but whenever I start the installation from a Live CD and get to the partition section it is showing that my hard-drive is has no operating system, when it in fact does.  Has anyone else encountered this issue, when trying to set-up dual-booting on their system? And, if you have had this issue, what did you do to resolve it?  I find it very strange, since I've never had a problem like this with any of the older releases. :(  

Thanks for reading, and I hope that whatever this is that it can be fixed.

---

### Post by wilee-nilee on 2010-06-16
> **MoonlitFate said:**
> I'm trying to set-up a dual-boot (Windows XP and Ubuntu 10.04), but whenever I start the installation from a Live CD and get to the partition section it is showing that my hard-drive is has no operating system, when it in fact does.  Has anyone else encountered this issue, when trying to set-up dual-booting on their system? And, if you have had this issue, what did you do to resolve it?  I find it very strange, since I've never had a problem like this with any of the older releases. :(  

Thanks for reading, and I hope that whatever this is that it can be fixed.

If you don't have a preformatted partition for Linux to use the custom install or any fee space that is what you get.

You will need to shrink XP and leave a open space, but shrink it after defragging, and reboot it and make sure it's working before proceeding. The auslogics defragger is fast and has a optimizer.
[http://www.auslogics.com/en/software/disk-defrag/download/](http://www.auslogics.com/en/software/disk-defrag/download/)

If you clicked on the custom section or looked at gparted I am quite sure you XP shows up.

---

### Post by MoonlitFate on 2010-06-18
> **wilee-nilee said:**
> If you don't have a preformatted partition for Linux to use the custom install or any fee space that is what you get.

You will need to shrink XP and leave a open space, but shrink it after defragging, and reboot it and make sure it's working before proceeding. The auslogics defragger is fast and has a optimizer.
[http://www.auslogics.com/en/software/disk-defrag/download/](http://www.auslogics.com/en/software/disk-defrag/download/)

If you clicked on the custom section or looked at gparted I am quite sure you XP shows up.

Thank you! :)  That fixed the problem, too bad that I'm having other ones.  Makes me sad. D:

---

