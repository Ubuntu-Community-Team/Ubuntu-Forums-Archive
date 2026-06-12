---
title: "Black &amp; White Welcome Screen"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by natedawg03 on 2011-09-21
Fairly green when it comes to Linux OS, but I'm learning.  I have a Dell Inspiron 5150 that I have tried to upgrade to 11.04 from 10.10 a couple of times.  Each time that I upgrade, whether it's from a boot disk or from the update manager, after I restart the welcome screen comes up and it has black pinstripes going down a white screen.  Sometimes it will power through the welcome screen and get to the desktop, but then a window will flash up on the screen and then disappear and then flash again in a different location and disappear.  It will flash up and disappear indefinitely and nothing else loads.  No top panel or any of the control icons up there.  The other times when it doesn't power through the welcome screen it will go to what almost looks like a terminal.  But again the characters are in black on a white screen and none of the characters can be read.  They are just pixels.  

Is it a graphic conflict with unity?  

Sorry I can't provide more technical information than the visual I am provided.  If there is any information that you would like me to try to get from my machine to tell you more about what is going on please let me know.  

Thanks for the help.

---

### Post by vinterkind on 2011-09-21
I'd guess this is a driver problem.

you could try <CTRL><ALT><F2> to get to another terminal

then invoke

```
sudo X -configure
cd /etc/X11/
nano xorg.conf
```

look out for the section "device"

there you could try

```
driver "vesa"
```

do you have some nvidia graphics adaptor ?

---

### Post by vinterkind on 2011-09-21
sorry 
```

sudo nano xorg.conf
```

in the upper post

---

### Post by natedawg03 on 2011-09-21
thanks for the suggestion.  i'll give it a go tonight.

---

### Post by vinterkind on 2011-09-21
Another mistake :(  

First you should only invoke  
```
sudo X :1 -configure 
``` 
if you haven't got a /etc/X11/xorg.conf ( the :1 is important )

If so, this should place a file xorg.conf into your/roots home directory.
then copy this file into the /etc/X11/ folder and modify the driver line as described.
Or test your configuration with 

```
X -config <path-to-your-xorg.conf>
```

Afterwards you should invoke : 

```
sudo invoke-rc.d gdm stop && sudo invoke-rc.d gdm start
```you could do a restart, but here it fails for me :-| 
The other try is a restart.

If that shouldn't help, please try to post the /var/log/Xorg.0.log and your /etc/X11/xorg.conf file here. Lets hope you haven't got an /etc/X11/xorg.conf.d/* configuration ^^
And check out which driver is in use by your graphics adaptor.
If you need any help ...

---

