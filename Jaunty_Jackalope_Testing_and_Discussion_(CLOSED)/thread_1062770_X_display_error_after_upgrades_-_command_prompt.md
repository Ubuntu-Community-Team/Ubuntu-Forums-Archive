---
title: "X display error after upgrades - command prompt"
date: 2009-02-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-02-07
Just downloaded and installed the latest updates to Kubuntu A4 with
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
Did a reboot and wished I hadn't. I can log-in but just get the default (grey, not blue) background and then nothing, no icons, panel.  The display just sits there. Tried to do a recovery and repair packages but still nothing. I've found the .xsessions-error file and there seems to be a few problems (attached), including X Error: XSyncBadAlarm 167.
How can I run  
```
ubuntu-bug -p xorg  
```
to report the problem as I'm running several distributions of Ubuntu/Kubuntu ?

---

### Post by minisori on 2009-02-07
Look this post, probably is the same bug.

[http://ubuntuforums.org/showthread.php?t=1061919](http://ubuntuforums.org/showthread.php?t=1061919)

---

### Post by Kevbert on 2009-02-07
Thanks for the link, but it looks like it's a different bug as I'm not using compiz. I'll try re-doing my xorg.conf and see if that helps.
Edit... it looks like xorg.conf is fine.

---

### Post by minisori on 2009-02-07
kwin is also affected with effects enabled.

---

### Post by Kevbert on 2009-02-07
> **minisori said:**
> kwin is also affected with effects enabled.
Kwin seems to cause part of the problem with NO effects as well.
The post mentioned previously helped, thanks.  I logged in as before and then pressed Ctrl-Alt-F1 and entered the command
```
ps ax | grep compiz.real
```
Compiz was not running at all (I've yet to install it in Kubuntu).
I then tried 
```
top
``` and it seems that xorg and kwin was using 100% of my processors (hence nothing worked).
I then rebooted into recovery mode and even though xorg.conf was fine I ran xfix. 
Yippee, I can use Kubuntu again.

Update...It seems there is a conflict between the latest updates and the Nvidia 180.27 driver. As soon as I re-install this the problem starts all over again. I'll have to put up with the display offset (no Nvidia restricted driver) for now.

---

### Post by minisori on 2009-02-07
The problem is not compiz, is nvidia + xserver. So if you are using any compositing manager compiz, kwin or whatever will result in the same behavior. So still even if you are not using compiz your problem seem to be the same one as the post i told you, i think there was a workaround for kde in that thread.

So just disable desktop effect by the moment.

---

