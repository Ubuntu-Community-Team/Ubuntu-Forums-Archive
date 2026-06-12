---
title: "How to re-install Windows 7"
date: 2018-02-05
forum: Installation &amp; Upgrades
---

### Post by christon74 on 2018-02-05
Good evening fellow Ubunters, Zoriners, Debianers, etc...:lolflag:
Silly me! I have at last successfully installed Ubuntu 16.04 on this second hand PC:D (Fujistu-Siemens Esprimo E 5731). When I bought it, it had Windows 7 pre-installed. Now this evening I thought I had carefully chosen the partition to install Ubuntu. Wrong! I was probably not paying enough attention, and I have wiped out Windows 7. And just like so many people, I am accustomed to both worlds.:biggrin:
Now, when the Grub is displayed, there is a line which says this: 
Windows recovery environement (loader) (on/dev/sdc1)
Another important thing to mention is that I have saved an image of my Windows 7 on an portable external hard drive, and I think I have burnt an image of the windows MBR to a CD, using Macrium Reflect. 
All of this can help re-install Windows, right?  All I need is a step by step guide to do it. 
Thanks in advance.

---

### Post by RobGoss on 2018-02-06
I haven't installed Windows for some time, but I would think it's best to install **Windows 7 **first then, if everything goes well I would then install Ubuntu and create a partition for the Ubuntu installation. I've heard they have Windows ISO's you can download but I don't think you'll find a Windows 7 ISO

---

### Post by yancek on 2018-02-06
If you need a step by step guide to re-installing windows, I would think you would be better off at a windows forum or looking at the microsoft support site.

---

### Post by Mark Phelps on 2018-02-07
Problem is that now, you are stuck in a catch-22 as you need some media to boot your PC to run Macrium Reflect to do the restore from the external drive, and you can't run Macrium Reflect to create that boot media.

You would need another Windows PC, download Macrium Reflect onto it, and choose the option to create Rescue Media.

Then, you could boot your PC from that Rescue Media, connect the external drive, and use the Restore function.

For details, your best source is the Macrium Reflect website:  [http://www.macrium.com/]("http://www.macrium.com/")

---

### Post by christon74 on 2018-02-08
Good morning Mark Phelps, Yancek, RobGoss. Well, Mark, I have both. I have burnt an MBR to a DVD, Macrium lets you do that, and I have saved an image to this portable external hard drive. But when I tried, Macrium told me to choose another disk destination (not C, nor D). I had imagined that Macrium would simply "re-write" the complete Windows 7 on the hard disk. Wrong guess, things are not done this way. Anyway, I am marking this thread as solved, simply because I have changed my mind. I have at last successfully installed Ubuntu, it runs as good as I can possibly dream. And I really want to spare myself the frustration of once again losing too much data, all the softwares I have already installed, wipe out Ubuntu, wait for hours (I have been told it takes a mighty long time) to re-install windows 7 and then finally re-install Ubuntu. So goodbye Windows_ at least for some time_ and if some day I really want it back, I have a complete windows installation CD here with all versions.

---

