---
title: "installation of ubuntu karmic in windows 7"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by arturieto on 2009-11-22
i have installed an windows 7 ultima evaluation copy in my laptop. after that I wanted to install Karmic 9.10 for dual booting.  there is a problem in initializing installation.  the CD installer is read and I went to full ubuntu karmic installation.  After I click the icon, initially it reads, and then seconds after the video turns into black.  i waited quite few minutes, and turn off the computer. I tried again, but again i see no video in my screen.

I don't know what happened.  Please help!, anybody please. ! !

---

### Post by Mze on 2009-11-22
Try this [guide]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")...

---

### Post by Mark Phelps on 2009-11-23
Make sure you follow the advice in the guide and use the Win7 Disk Management utility to shrink the OS partition to make room for Ubuntu.  Don't rely on the Ubuntu installer to do that or you'll run the risk of corrupting the Win7 OS partition, and if you haven't made a Win7 Recover CD, you won't then be able to boot into that to repair Win7.

Also, would advise against using Wubi to do a side-by-side install inside Win7.  Lots of folks have reported that it doesn't work when done and none have posted any solutions yet.

---

