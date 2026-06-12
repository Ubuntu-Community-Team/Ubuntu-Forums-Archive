---
title: "VIA Unichrome Pro not displaying correct resolution."
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by derrick.anderson on 2010-12-29
I have an Everex Step Note that is running the S3 Unichrome Pro integrated graphics card.  I cannot despite my hardest efforts find a fix already existing for this.  My desktop will only display with 1600 X 1200 resolution. My monitor and video are supposed to run natively at 1200 x 800 .. Any time I try to change the resolution my screen gets choppy and garbled and i have to wait for it to automatically change back.  My screen is cutting off the right and bottom portions.  

When i run lspci i get the following 
```

01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)
```I have tried to edit my xorg.conf file but it doesn't exist in the ect/x11/ folder.  I've tried to reboot into recovery mode and create it.  It will create but when i try to copy it to the new folder, it tells me that no such folder exists.

EDIT: I have discovered that I can use 
```
sudoedit /root/xorg.conf.new
```
to get to and edit my xorg file. But it does show openchrome as the driver.

VIA does have open source drivers but when i tried to install the only driver they provide it crashed my X console... I was only able to load into the text interface.

Has anyone had any luck getting the OpenChrome to work with this card?  I know that I have OpenChrome installled and working but DANGIT  why doesn't this work?!:mad:

---

### Post by kansasnoob on 2010-12-29
What version of Ubuntu are you running? You can check by running:

```
lsb_release -a
```

The reason I ask is because I've built a lot of desktops that use the VIA P4/M800 chip and I've had no problem since about Intrepid or Jaunty, but they're desktops, not Stepnotes, so that may be somewhat like comparing apples and oranges :)

Anyway you can see if an xorg.conf exists by running:

```
ls /etc/X11
```

If one already exists I think it would be wise to begin by running:

```
sudo dpkg-reconfigure -phigh xserver-xorg

```

Then either reboot or restart X. If the desired resolution still does not exist and if you're using the Gnome desktop I've found the following procedure preferable to creating an xorg.conf:

[http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/)

Actually you might find this thread to be helpful:

[http://ubuntuforums.org/showthread.php?t=1462350](http://ubuntuforums.org/showthread.php?t=1462350)

In that case I'm using Intel graphics but it still may be helpful.

---

### Post by derrick.anderson on 2010-12-30
Right now i'm running Version 10.10

There is no Xorg.conf file in the /ect/x11 folder.

And it's not that the desired resolution isn't there it's that the only one that works is 1600x1200 and it's too big for my screen. Every time i try to use 1200x800 it jarbles the screen.

---

### Post by meddyuk on 2011-04-05
Ive got the same problem with mine, sorry to jump in on the post, but ive another thread detailing my problem.

I looked into the Xorg file and a couple of searches on Google, stated that in recent editions of Ubuntu, they've done away with the xorg file. Unless you have a Nvidia card and in that case it will create its own xorg file. Because you have onboard video card, the xorg file will be empty.

I'll keep an eye out for this thread to see if anyone offers a solution. Ive tried downloading the VIA drivers from the internet but they state they are for pre Ubuntu 8. I doubt very much that 10.10 supports it.

---

### Post by cinikal on 2011-05-11
sorry to bump but theres no solution yet. i have an mx3225 also with same resolution problems. ive tried other threads advice by creating and changing the xorg.conf file to say 1280 x768 but to no avail. I too can only see my screen in 1600x1200. Any Ideas?

---

