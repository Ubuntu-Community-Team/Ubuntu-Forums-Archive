---
title: "CD error on first Installation"
date: 2006-04-10
forum: Installation &amp; Upgrades
---

### Post by Nigy on 2006-04-10
my friend has finally convinced me to try Ubuntu, and linked me to the athlon64 version (i have athlon 64 3700) livecd latest beta of ubuntu. I burn the iso onto a blanc cd-r. I run it, basic GUI comes up, I select to install ubuntu. 

view switches to a status-bar that doesnt move for a few seconds, then the now black screen is filled with lines of white text.

on the bottom of that text I am informed that a buffer I/O error DNS thingie has occured. and that is that

I burn onto a different brand of cd, at a slower rate, same problem.

---

### Post by Kapre on 2006-04-10
Nigy - if you download the latest LiveCD, you cannot install from it. It was meant for testing so you can have the look and feel of the OS. Try d/l the install version and burn it on slower speed (6-8X). 

K

---

### Post by Nigy on 2006-04-10
if i do that, will I able to have linux on one partition and windows on another like i had previously planned? would I  burn and install the same way? thank you

---

### Post by taurus on 2006-04-11
Yes, you can have your Windows on one partition while Ubuntu on another.  Just pay extra attention when you get to the partition screen and make sure you pick the right now; otherwise, it could wipe out your Windows if you tell it to install on the wrong partition!  Then, install GRUB on the MBR since it can handle booting both Windows and Ubuntu...

---

### Post by Nigy on 2006-04-11
OK, i did same thing with the install version, burned at 8x, but when I reach the point after partitioning, the install fails everytime

---

### Post by Kapre on 2006-04-11
nigy - try to check if the integrity/md5sum of your download is ok. This is the only thing that I can think of that is stalling your install. 

K

---

### Post by Nigy on 2006-04-11
how would I do that? I remember checking the integrity of  the disk and it coming out fine.

---

### Post by Sef on 2006-04-12
1. To md5sum:  Assumes you have downloaded the iso to your desktop.

cd ~/Desktop

sudo md5sum (name of program)

That number and the one from the their file should match.  If not, reburn.  Don't burn at more than 4x.

2. If you download with bittorrent, then it automatically md5sums.

---

### Post by PriceChild on 2006-04-12
[quote=Sef]1. To md5sum:  Assumes you have downloaded the iso to your desktop.

cd ~/Desktop

sudo md5sum (name of program)

That number and the one from the their file should match.  If not, reburn.  Don't burn at more than 4x.

2. If you download with bittorrent, then it automatically md5sums.[/quote]

Those are instructions for checking the md5sum on linux... i thought i'd point that out so you don't try it inside your windows install :P

Sorry i don't know how to check md5sums in windows

---

### Post by confused57 on 2006-04-12
Try downloading md5 checksum summer:

[http://www.md5summer.org/download.html](http://www.md5summer.org/download.html)

I downloaded the zip file since I have WinZip, but it looks like there is a self-extracting .exe file you can use.  Once you've downloaded and extracted, double click on the .exe file that is extracted & it's pretty self-explanatory from there.  It works great for me.

---

### Post by Nigy on 2006-04-12
Good news, it looks I have somehow fixes this. actually I know how, and hopefully IM not skrewing myself over once again. in NTFS file system, it failed, but in EX2 file system, it worked fine. 

Now Im having a problem with nvidia drivers that i have heard about before (I have a pci-e graphics card), and my commands of 

sudo install nvidia-glx..or something like that is failing, but i read something that leads me to believe this is due to the fact that my computer (not this one, the one im installing ubuntu on) is not connected to the internet.

---

### Post by Nigy on 2006-04-13
bump

---

