---
title: "Mini.iso install help"
date: 2013-02-26
forum: Installation &amp; Upgrades
---

### Post by secuono on 2013-02-26
So I'm going through a heck of a lot of trouble getting all this to work! 
Back to trying the 12.04 version, it does everything in auto, all I do is pick keyboard, time zone, how much HD to use and then it's all 'done'. 
But then, after restart, I get a text menu where I can log in and....then what do I do? There is no common screen, nothing that I'm expecting that is usually used/seen. Is there more to install or program


[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
I put in the CD, there is no place to be typing "cli", since it's visual, not text...

---

### Post by MAFoElffen on 2013-02-26
With the Minin ISO install disk, you "have" to select a desktop package to install when the TASKSEL popup comes up asking you for what applications to install. That comes up about 3/4 of the way through the install process of that disk. Otherwise you end up with a text tty console vanilla install.

If you have installed from one of the distribution disks (Ubuntu, Kubuntu, Xubunut, Lubuntu) it would have automatically installed that distribution's desktop as part of it's install process. The mini.iso disk is more "flexible" and "adaptable," as you can install various distro's from the same disk, but not much of those programs are stored on that disk // it downloads each of them... therefore being an install image that is small in size, it was named "mini".

But from a running console, you could install a desktop package without reinstalling the system again.

If you entered your loggin user_name, then password... and logged into the system... Then do this command:
```

sudo apt-get update

```
That will update the system's resource list.

Then look at this command:
```

sudo apt-get install desktop_name

```
You would type in that command, but substitute "desktop_name" for one of the following, depending on what desktop you want to install:
```

ubuntu-desktop
kubuntu-desktop
xubuntu-desktop
lubuntu-desktop

```
Is that enough info to get you going?

---

### Post by secuono on 2013-02-26
Thanks!!

---

### Post by MAFoElffen on 2013-02-26
> **secuono said:**
> Thanks!!
You are welcome. If there are problems, will continue here. 

If it installs successfully and comes up fine, please return to this thread to mark this as "Solved."

---

### Post by secuono on 2013-02-26
Pictures in order, having issues again...I checked all of the options, other than the different 'flavors', just Ubuntu. 

So first after the reboot, this screen shows. Screen never goes away.
[IMG]http://i34.photobucket.com/albums/d101/secuono/DSC_0472.jpg[/IMG]

Then after another reboot, this screen. 
[IMG]http://i34.photobucket.com/albums/d101/secuono/DSC_0474.jpg[/IMG]

Rebooted 3rd time, this now shows.
[IMG]http://i34.photobucket.com/albums/d101/secuono/DSC_0475.jpg[/IMG]

And then later, I got to this screen, 4th reboot. It only ended in it saying it will write over stuff or the first option, it ended with more lines of text that didn't stop, like in the picture above... 
[IMG]http://i34.photobucket.com/albums/d101/secuono/DSC_0476.jpg[/IMG]

---

