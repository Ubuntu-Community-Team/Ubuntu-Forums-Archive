---
title: "Ubuntu install turned to edubuntu - help please"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by orbit1979 on 2006-12-02
Hello
I recently installed Ubuntu 10. Everything went great. However, I installed the automatic updates and somehow, my install is now edubuntu! What happen and how can I get Ubuntu back? Can I get it back without having to go through hassle of re-installing? 
Any help would be appreciated, my desktop looks like a cartoon!

---

### Post by Sef on 2006-12-02
> I recently installed Ubuntu 10.

Do you mean Edgy 6.10?

> However, I installed the automatic updates and somehow, my install is now edubuntu! What happen and how can I get Ubuntu back? Can I get it back without having to go through hassle of re-installing?

Sounds like you installed Edubuntu by mistake.   There is no way that automatic updates will change you operating system.  To reinstall would be the best way to get [Ubuntu]("http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download").

---

### Post by orbit1979 on 2006-12-03
> Do you mean Edgy 6.10?

Yes.

> Sounds like you installed Edubuntu by mistake. There is no way that automatic updates will change you operating system. To reinstall would be the best way to get Ubuntu.

No, I downloaded Ubuntu 6.10 iso in windows, burned it to disc, then installed it. The first evening I ran it, it was Ubuntu. When I installed the updates, first the splash-screen said Edubuntu, but everything else was normal. Then after re-starting for the second time, everything changed.

---

### Post by aysiu on 2006-12-03
If you accidentally installed Edubuntu, you don't need to reinstall. You can get Ubuntu by doing this:

Step 1. **Install Ubuntu or Make Sure Ubuntu is installed** by pasting this command into the terminal: ```
sudo aptitude update && sudo aptitude install ubuntu-desktop
```

Step 2. **Remove Edubuntu** by pasting this command into the terminal: ```
sudo apt-get remove -y atomix atomix-data denemo dia-gnome edubuntu-artwork edubuntu-artwork-usplash edubuntu-desktop gcompris gcompris-data gcompris-sound-da gcompris-sound-de gcompris-sound-en gcompris-sound-es gcompris-sound-fr gcompris-sound-it gcompris-sound-pt gcompris-sound-ru gcompris-sound-sv gnome-icon-theme-gartoon gpaint kalzium kalzium-data kanagram kbruch keduca khangman khelpcenter kig kino kmplot kpercentage kstars kstars-data ktouch ktuberling kturtle kverbos kvoctrain kwordquiz libboost-python1.33.1 libgcompris-1-0 libkdeedu3 libkdegames1 libsamplerate0 libsdl-mixer1.2 libsdl-ttf2.0-0 libsmpeg0 pessulus python-pysqlite2 student-control-panel ttf-dustin tuxmath tuxpaint tuxpaint-data tuxpaint-stamps-default xaos
``` Step 3. **Make sure you have the correct bootsplash** by following these instructions:
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

---

### Post by orbit1979 on 2006-12-03
Excellent. You post worked. Everything is fine now. I am still not sure how that happened, all I did was install updates. The update message is popping up again, but I am not so sure I trust it now.
Thanks for the fix.

---

### Post by anorexicpillow on 2006-12-04
Hello, i just reinstalled ubuntu and when i restarted for the first time on the new install it turned into edubuntu! I went threw all the steps here and the ones on the link you posted but when i restarted it booted as edubuntu again :S any ideas?

---

### Post by basketcase on 2006-12-20
My computer actually did this the other day.  I've had 6.06 on this box since it was released, and the other day I restarted after an update, and it now says Edubuntu.  

And to prove it is not Edubuntu

>  sudo apt-get remove -y atomix atomix-data denemo dia-gnome edubuntu-artwork edubuntu-artwork-usplash edubuntu-desktop gcompris gcompris-data gcompris-sound-da gcompris-sound-de gcompris-sound-en gcompris-sound-es gcompris-sound-fr gcompris-sound-it gcompris-sound-pt gcompris-sound-ru gcompris-sound-sv gnome-icon-theme-gartoon gpaint kalzium kalzium-data kanagram kbruch keduca khangman khelpcenter kig kino kmplot kpercentage kstars kstars-data ktouch ktuberling kturtle kverbos kvoctrain kwordquiz libboost-python1.33.1 libgcompris-1-0 libkdeedu3 libkdegames1 libsamplerate0 libsdl-mixer1.2 libsdl-ttf2.0-0 libsmpeg0 pessulus python-pysqlite2 student-control-panel ttf-dustin tuxmath tuxpaint tuxpaint-data tuxpaint-stamps-default xaos
Password:
Reading package lists... Done
Building dependency tree... Done
Package atomix is not installed, so not removed
Package atomix-data is not installed, so not removed
Package denemo is not installed, so not removed
Package dia-gnome is not installed, so not removed
Package edubuntu-artwork is not installed, so not removed
Package edubuntu-desktop is not installed, so not removed
Package gcompris is not installed, so not removed
Package gcompris-data is not installed, so not removed
Package gcompris-sound-da is not installed, so not removed
Package gcompris-sound-de is not installed, so not removed
Package gcompris-sound-en is not installed, so not removed
Package gcompris-sound-es is not installed, so not removed
Package gcompris-sound-fr is not installed, so not removed
Package gcompris-sound-it is not installed, so not removed
Package gcompris-sound-pt is not installed, so not removed
Package gcompris-sound-ru is not installed, so not removed
Package gcompris-sound-sv is not installed, so not removed
Package gnome-icon-theme-gartoon is not installed, so not removed
Package gpaint is not installed, so not removed
Package kalzium is not installed, so not removed
E: Couldn't find package kalzium-data


---

