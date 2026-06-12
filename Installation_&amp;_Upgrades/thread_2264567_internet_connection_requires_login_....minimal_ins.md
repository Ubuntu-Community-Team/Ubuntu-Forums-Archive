---
title: "internet connection requires login ....minimal install"
date: 2014-10-24
forum: Installation &amp; Upgrades
---

### Post by legendaryman on 2014-10-24
iam trying to install linux on my computer 512mb ram ,p4 3.8 ghz

first
 i have tried bootable usb and standard iso and got error and make thread here[http://ubuntuforums.org/showthread.php?t=2247667](http://ubuntuforums.org/showthread.php?t=2247667) 
from that thread i got reply that to use alternate iso 

secound 
i have bootable usb from unetbootin 
and guess what i get error that cdrom detection error, can't mount or something like that
i search on net and found solution here [http://ubuntuforums.org/showthread.php?t=1750464](http://ubuntuforums.org/showthread.php?t=1750464) and tried all suggestion but it doesn"t give me name of my pendrive like sda or sdb  when typing  following tail -n 100 /var/log/sys and also i tried mount using sda,sdb,sdc,sdd but it always says "'no such file in etc/fstab'''' 

third 
i tried wubi install of ubuntu 14 desktop it goes smooth till ''copying files'' but reboot after apt error no cdrom detect{or something like that]]

fourth
now after vasting one in above stuff i decided to  make bootable cd of lubuntu alternate 14  ....but guess what ..........you guess it right .i got error on ''loading additional components from cd rom '''  error is ''çant detect cdrom '''basically it is saying to check the integraty of cd  which i have done with no errors....



update:for some reason i cant use my dvd rom so now i have only option for usb....

---

### Post by mörgæs on 2014-10-24
Please keep experimenting. What about the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall")?

---

### Post by legendaryman on 2014-10-25
> **mörgæs said:**
> Please keep experimenting. What about the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall")?
ok i think that it requires cd or dvd which ,for now i cant use my dvd rom.......and morever it also requires internet connection ,and mine is very slower

---

### Post by Bucky Ball on 2014-10-25
Just a note: Don't use Wubi. Even though it is available, it is an oversight, as it is no longer supported by Canonical or these forums. See [HERE]("http://ubuntuforums.org/showthread.php?t=2229766"). 

With 512Mb of RAM you won't get Ubuntu running (the desktop environment Unity will doubtful run on that little). The minimal install, as suggested by morgaes, is definitely your best option, but Lubuntu may work. If you can throw 2 or 4Gb of RAM in the machine you should have no issue, though. P4 CPU fine. Good luck.

PS: As you are running a P4 it is probably 32bit. You are using the 32bit ISO, yes?

---

### Post by mörgæs on 2014-10-25
The minimal install runs from CD and USB. 
You should use wired internet connection during install no matter how fast it is.

---

### Post by legendaryman on 2014-11-14
> **mörgæs said:**
> The minimal install runs from CD and USB. 
You should use wired internet connection during install no matter how fast it is.
):Pmy wired internet connection requires login before using internet means when you try to open google.com ,it wil redirect you to login page ....hence i cant download components using minimal install .....please help me,how to enter login details during minimal  installation [[[step by step]]]

and how much megabytes of needs to be downloaded ..................
my internet speed is six megabytes per minutes ......so how  much time it will take for installation

---

### Post by mörgæs on 2014-11-14
Bringing the computer to a place where you get free internet access?

---

### Post by legendaryman on 2015-02-08
my wired internet connection requires login before using internet means when you try to open google.com ,it wil redirect you to login page ....hence i cant download components using minimal install .....please help me,how to enter login details during minimal installation [[[step by step]]] ...i think while installing the proxy part has something  to do with these

and how much megabytes of needs to be downloaded ..................
my internet speed is six megabytes per minutes ......so how much time it will take for installation

---

### Post by mörgæs on 2015-02-08
Threads merged. 
We appreciate if you keep all posts related to a problem in the same thread.

---

