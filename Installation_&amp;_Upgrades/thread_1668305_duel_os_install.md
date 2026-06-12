---
title: "duel os install"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by gudurukarthik on 2011-01-16
hello,
hi im now currently having ubuntu10.10 in my sony fw series (6gb ram and 512mb vram ati mobility radeon graphics). now im going to install windows 7 and also parallel ubuntu in my laptop. but i dont know how to do that , will be really thankfull if u can give me the clear steps to follow to install both os's in my laptop.

---

### Post by CCoder on 2011-01-16
1) Boot Ubuntu up via LiveCD
2) Delete all partitions via GParted
3) Create a Windows partition (NTFS) for Windows for about 90 GBs
4) Boot up Windows installer
5) Install Windows
6) Install Ubuntu

& there you go.
I've installed every computer this way. I hadn't any problem till now.

Without wax,
CCoder.

---

### Post by gudurukarthik on 2011-01-16
oh, its simple. but i really dont know any of the steps, so can u please give me any link or details of how to do all that . 
sorry for thr trouble .
think green
thank u

---

### Post by CCoder on 2011-01-16
> **gudurukarthik said:**
> 
think green
thank u
Think green? :D I don't really get it :D

Whatever..
[CENTER][http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")[/CENTER]
You can check Kevin Purdy's lifehacker article about dual-booting W7 and Ubuntu.

Have a nice day.
Without wax,
CCoder.

---

### Post by kansasnoob on 2011-01-16
Do you have any data in Ubuntu that you wish to save?

What disc(s) are you using to install Win7?

I ask the latter because I've had no real problem installing Win7 alongside Ubuntu if I'm using "unbranded" OEM Win media. Branded media, like HP or Dell, is a different story because it often wants to create 4 primary partitions.

I'm also curious why you're installing Windows after installing 10.10? Did 10.10 wipe your Windows out?

The 10.10 installer has a problem. Basically if you choose the option to "Install alongside" it displays the options "Use entire partition" and "Use entire disc". Selecting either of those is likely to wipe out everything on your drive! Look here at posts #1 and #15:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

You need to know about that even if you do decide to wipe the drive and start over with Win7 first.

I recently tried to explain to someone how to install XP after Ubuntu here:

[http://ubuntuforums.org/showpost.php?p=10356856&postcount=3](http://ubuntuforums.org/showpost.php?p=10356856&postcount=3)

There's actually little difference as long as the Windows installation media is willing to live with the allowable number of primary partitions, but if it's a "branded" restore disc all bets are off.

---

