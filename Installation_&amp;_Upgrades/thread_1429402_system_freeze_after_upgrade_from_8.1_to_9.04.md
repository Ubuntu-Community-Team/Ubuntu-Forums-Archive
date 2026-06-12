---
title: "system freeze after upgrade from 8.1 to 9.04"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by nafihsus on 2010-03-14
After successfully upgrading from 8.04 to 8.1 (where even my wireless worked for the first time) I got a system freeze when I tried to upgrade to 9.04. 

I suspect the graphics driver but don't know how to upgrade without X running. After booting in generic mode (kernel 2.6.28-18) I can log in the shell but am lost without the GUI.

Can someone help?

---

### Post by zvacet on 2010-03-15
```
nano /etc/apt/sources.list
```

and see if entries are replaced from intrepid to jaunty.If they are not exit nano with **ctrl+x** and then type

```
sudo cp /etc/apt/sources.list /etc/apt/sources.lis.bak
```

Then again open sources list with nano ( as above) and replace intrepid with jaunty in every line.Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```

If still something is wrong try with 

```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by nafihsus on 2010-04-14
Just to close this thread I post what I finally did. 
I started with a LiveCD of 9.1 and just installed it from scratch without formatting the disk. Installation went through perfectly easy, even my WLAN worked right away.
The best of it - all my data still was there under /home/home/<name>. 

Sometimes things that start badly turn out nice. :P

---

