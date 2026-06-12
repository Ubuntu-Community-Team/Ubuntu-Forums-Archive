---
title: "wubi 10.04 installation fails on 64-bit Windows 7 PC"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by corona79 on 2010-07-20
[IMG]http://i26.tinypic.com/osy834.jpg[/IMG]

[IMG]http://i26.tinypic.com/dceern.jpg[/IMG]



There is no *appdata* folder, and no error log could be found in the *ubuntu *folder.

The first time wubi.exe (from [http://wubi-installer.org/](http://wubi-installer.org/)) was executed, Windows refused to run it, with a compatibilty error.  It was then downloaded from  [http://wubi.sourceforge.net/](http://wubi.sourceforge.net/) - after about an hour, this error occurred on two separate installation attempts.

---

### Post by corona79 on 2010-07-21
It's been a day, so I'm bumping.

Anyone seen a similar problem?

---

### Post by bcbc on 2010-07-21
You can get to the log file by opening explorer and entering %temp% in the address bar.

wubi.exe has to be run as an administrator and you need internet access.

It is better to [download]("http://www.ubuntu.com/desktop/get-ubuntu/download") the 10.04 cd image separately because then you don't have to download it each time you try and install wubi. You can also use it to create an install CD which you can use to try Ubuntu without installing (to see if it works properly on your computer).

If you do download it separately and want to use wubi (without burning a cd) place wubi.exe and the .iso file in the same directory. (As long as you select the desktop corresponding to the .iso e.g. don't download Ubuntu and then select Kubuntu), it will use the image. It still needs the internet to check that it is a valid image.

If you burn the CD you can just run wubi.exe off the CD.

---

### Post by JustinR on 2010-07-22
Turn off all Security software on your Windows installation. And make sure your not in safe mode.

---

### Post by najmisaufi on 2011-06-14
corona,
 
I face the same issue too..
Before that I allow the pyrun.exe to access through firewall.
 
Try to find the solution in other thread but not yet solved.
The steps I had tried but not yet solved:
1) Run as admin and make compatible to vista (no service pack).
2) Turn off all virtual drive
3) Other solution are more on installing ubuntu..not the wubu.
 
Anyone can helps?

---

### Post by uRock on 2011-06-14
This thread is almost a year old. Please start a new thread on your issue.

Thread Closed.

---

