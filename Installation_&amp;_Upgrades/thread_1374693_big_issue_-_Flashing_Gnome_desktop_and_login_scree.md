---
title: "big issue - Flashing Gnome desktop and login screen"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by carlosgs on 2010-01-07
I'm having this problem with Ubuntu 9.10, it has happened the three times I have tried to install it.

I have made a video showing the problem:

[http://www.youtube.com/watch?v=G4NkALmkJ6A](http://www.youtube.com/watch?v=G4NkALmkJ6A)

After upgrading and rebooting, the flashing login screen appears and it is not possible to use the GDM.
I have tried to install KDM and it works, but when trying to load gnome I get the blinking bars again.

I have also tried this (and got the same problem); installing the Nvidia driver (manufacturer), installing the Nvidia driver (repositories) and installing no screen driver.

I think the problem is with GNOME, and not with the graphics card.

Now I have installed windows xp :-/, for the first time in a whole year, cause it is not possible for me to use Ubuntu 9.10 at all.

I hope this only happens to me.
Hopefully, this will get fixed soon, since the new functions of Ubuntu 9.10 are awesome.

Thanks for your help.

P.S.: If you have the same problem please post it here.

Edit: This is NOT the same problem here: [http://ubuntuforums.org/showthread.php?t=1305459](http://ubuntuforums.org/showthread.php?t=1305459)

---

### Post by dstew on 2010-01-07
That is a strange problem, I have not seen it before. Did you try to reconfigure gdm?```
sudo dpkg-reconfigure gdm
```You could also try to reconfigure the gnome session manager the same way```
sudo dpkg-reconfigure gnome-session
```

By the way, you say kdm works fine. How do you select kdm vs. gdm? Do you have different grub menu items?

What computer do you have, and what monitor?

---

### Post by carlosgs on 2010-01-07
Thanks for replying :-)

> That is a strange problem, I have not seen it before. Did you try to reconfigure gdm?     Code:
     sudo dpkg-reconfigure gdm 
Yes, i had tried that with no result :(

> You could also try to reconfigure the gnome session manager the same way     Code:
     sudo dpkg-reconfigure gnome-session 
I think i have tried that also, but i'm not sure, i'm going to install 9.10 again in a new partition and check that.

> By the way, you say kdm works fine. How do you select kdm vs. gdm? Do you have different grub menu items?I installed kdm by apt-get install kdm, that shows a dialog that lets you select gdm or kdm. (that dialog also appear when dpkg-reconfigure gdm -or kdm-).

> What computer do you have, and what monitor?     The computer is an Acer Aspire X1700, the monitor is a PROVIEW 700p

I'm going to try the dpkg-reconfigure gnome-session

Thanks for your help ;)

---

### Post by carlosgs on 2010-01-09
Ok so sudo dpkg-reconfigure gnome-session did not worked :-(

Waiting for more help

---

### Post by dstew on 2010-01-09
I'm sorry I don't have more ideas for you. You might try posting on the Multimedia & Video or the Desktop Environments forums. They are pretty active and people that troll those forums may have more expertise in strange video problems.

---

### Post by carlosgs on 2010-01-10
OK thanks anyway :-)
I'm going to try to re-download and burn in a CD ubuntu 9.10, just in case it was a problem with the CD.

Thanks again

---

### Post by carlosgs on 2010-01-10
Ok, I have reinstalled it (finally I did not made a new cd)
-now using it-
tried to reboot a few times with the fresh install with no problems
now updating&upgrading (without installing anything else -no screen drivers-)

if it fails again, the problem will be in the xorg server update probably :-S

cheers ;-)

---

### Post by carlosgs on 2010-01-10
OK, now I rebooted and it went fine
maybe the problem was that I installed the nvidia drivers before upgrading, no idea :-S

Im going to reboot a few more times and then install the nvidia drivers from System->Administration->Hardware Drivers.

hope it works now :-)

BTW, the migration assistant for firefox (from Windows) didnt worked, maybe because there is a password in the windows partition and it wasnt mounted

---

### Post by carlosgs on 2010-01-10
Ok, so rebooted 2 times and it worked OK
now downloading and installing the nvidia drivers... [-o< xD

---

### Post by carlosgs on 2010-01-10
Rebooted and... works!
Let's see if it survives 2 more reboots lol (I think i'm a bit paranoic with this lol)

---

### Post by dstew on 2010-01-10
Thanks for finishing off the thread.

---

### Post by vitiate on 2010-01-11
I had this exact same problem but I was able to resolve it without reinstalling everything. After looking at this thread [http://ubuntuforums.org/showthread.php?p=6103702](http://ubuntuforums.org/showthread.php?p=6103702) I looked in /usr/local/lib and realized I had installed freetype's libraries that I had compiled the day before. These were conflicting somehow and now that they are gone the log in screen works fine.

---

### Post by carlosgs on 2010-01-16
Damn!
the problem is back :-(
Updated this morning, rebooted and then again a flashing white rectangle instead of the login box.

I don't know what to do now (I didn't disabled the nvidia drivers before the update :-S)

Please help me with this :-(

---

### Post by carlosgs on 2010-01-16
Switching to Debian
Hope it is useful
Thanks for your help anyway ;)

---

### Post by carlosgs on 2010-02-10
Ok so I tested Ubuntu Studio 9.10 and didn't have the problem until installing a newer linux image & headers.
After that it was just the same...

---

### Post by noabody on 2010-07-16
Thanks vitiate, I had compiled freetype from source because it is required to compile OpenPS2Loader.  The computer worked fine for several days and then all of a suddent this cropped up.  

After I deleted (sudo rm /usr/local/lib/freetype*.*) the problem was gone.  The only thing is, I have Ubuntu Lucid installed and booting from an external hard disk so I don't know if moving from one computer to another affected it somehow.  The last program I used before everything went to crap was Firefox.  Maybe a web page prompted a freetype library to be loaded and that touched everything off.

---

