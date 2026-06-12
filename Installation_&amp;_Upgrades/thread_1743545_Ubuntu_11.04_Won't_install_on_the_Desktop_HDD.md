---
title: "Ubuntu 11.04 Won't install on the Desktop HDD"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by empyrec on 2011-04-29
Hello, first off let me just say that i am new to ubuntu and the forum system. I apologise in advance if i am in the wrong area. Okay to start off, i downloaded Ubuntu 11.04 to make a live usb. It booted correctly and everything seemed fine. I explored Ubuntu a little further and liked it very much. satisfied with Ubuntu i began to tried the installation process.The Ubuntu installer opened up and asked what language i would like i chose english, then the next screen popped up, Which was titled "Preparing to install ubuntu".  followed by, for best results, please ensure that this computer:

(xmark)Has at least 4.4 GB available drive space
(check)Is plugged into a power source
(check) is connected to the Internet  

I want to use the HDD that windows is installed on, it won't show up at all.

I even went through  System>administration>GParted Partition  Editor.  and the only thing that is there is the USB which is a 2gig. Why won't it let me install on the HDD?

---

### Post by mörgæs on 2011-04-29
Hi, welcome to the fora.

This is just guessing, since I do not have Windows myself:

You could 
-delete everything unneeded in Windows, also in the trashcan
-defragment the drive a couple of times
-shrink the Windows partition from within Windows
-boot a couple of times to confirm that everything works

and try again. Now there should be open space for Ubuntu.

---

### Post by punkybouy on 2011-04-29
Gparted has a drop down box at the top where you would have to select your hard drive, probably hda or some such.

---

### Post by empyrec on 2011-04-30
> **mörgæs said:**
> Hi, welcome to the fora.

This is just guessing, since I do not have Windows myself:

You could 
-delete everything unneeded in Windows, also in the trashcan
-defragment the drive a couple of times
-shrink the Windows partition from within Windows
-boot a couple of times to confirm that everything works

and try again. Now there should be open space for Ubuntu.

Did all of that and still nothing.

---

### Post by empyrec on 2011-04-30
> **punkybouy said:**
> Gparted has a drop down box at the top where you would have to select your hard drive, probably hda or some such.

I have tried the drop down box, the only thing that shows up is the USB. Would this be giving me problems because it's a desktop and not a laptop?

---

### Post by mörgæs on 2011-05-01
If you download a 10.10 ISO (preferably from a torrent) and try the same, do you see any difference?

---

