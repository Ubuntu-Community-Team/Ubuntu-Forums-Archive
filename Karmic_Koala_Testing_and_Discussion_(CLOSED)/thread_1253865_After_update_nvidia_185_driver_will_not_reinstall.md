---
title: "After update nvidia 185 driver will not reinstall"
date: 2009-08-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by thegodsquirrel on 2009-08-30
I did the most recent update for Karmic 9.10, after reboot I get the error no screens found.  I was able to fix this once by dropping into the networking root and doing an update and then reinstall the nvidia-185-kernel-source.

However, after the next update same problem, but now reinstalling the driver no longer works.

Please help, dead in the water.

---

### Post by overdrank on 2009-08-30
Moved to Karmic Koala Testing and Discussion

---

### Post by trulan on 2009-08-30
I've had similar issues with the latest real time kernels (2.6.31-*-rt) (Ubuntu Studio), in this case it is due to a known bug.  There is another thread dealing with that:
[http://ubuntuforums.org/showthread.php?t=1248507](http://ubuntuforums.org/showthread.php?t=1248507)
If you are not using the RT kernel, disregard this.

For a temporary workaround, I do this: (log in to the TTY.  Omit sudo if doing this from a root terminal)
```
sudo nano /etc/X11/xorg.conf
```
Find the line that says driver=nvidia and change nvidia to vesa.  Ctrl+x to exit nano, y to save, etc.
```
sudo reboot
```
This should at least get x working again, so you can get to working on the real problem.

---

### Post by thegodsquirrel on 2009-08-31
That is great advice, but I have only been using ubuntu for about a year and a half, and I upgraded to Karmic to try to force myself to learn using trial by fire.  That being said I have used nano to open the xorg.conf and there is never anything there.  Do I need to do something once nano opens?


Your help is appreciated.

---

### Post by trulan on 2009-08-31
That's right xorg.conf is blank sometimes in Karmic, I forgot.  I'm not sure why, except that everything is supposed to be automatic.  There's a command to run which generates xorg.conf but I'll have to go look for it.  If I find it before you post back, I'll add it here.

Edit:  Found this, hope it helps.
> **wayne_cat said:**
> If no xorg.conf file is present , Xorg will probe the system to autoconfigure itself. You can run:
```

 Xorg -configure 
```to generate an initial xorg.conf  ... copy it to /etc/X11 ... change your settings ... done


By the way, which kernel are you using?  I'll assume it's 2.6.31-rc8.

---

### Post by thegodsquirrel on 2009-09-01
Dude, you are a life-saver.  Thanks for the help!!!!  That worked perfectly.  Now I can install the new Nvidia files!!!

---

