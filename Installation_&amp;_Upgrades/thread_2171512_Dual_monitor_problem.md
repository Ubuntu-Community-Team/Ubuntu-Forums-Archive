---
title: "Dual monitor problem"
date: 2013-08-31
forum: Installation &amp; Upgrades
---

### Post by barabba2005 on 2013-08-31
Hello
I installed the 13.04 on a Packard bell Easy note laptop.
The video card is an Intel ® 945 GM x 86/MMX/SSE2 in standard experience.


At login the monitor remains black.

I must to disconnect and reconnect the second monitor to get the login screen.

You probably don't have the correct drivers.




Thank you in advance.

---

### Post by GwL3eNC on 2013-08-31
Hi,

possibly screen 0 and sceen 1 in /etc/X11/xorg.conf are interchanged so that your second display is set to
your primary device. it may be true, that you can also change this in the display system-settings. I'm not
good with xorg.file, you may post it here if you cant solve your problem.

---

### Post by barabba2005 on 2013-08-31
HI GwL3eNC
Thanks for the help


I think its a driver problem because if the second monitor is connect

the computer goes into freez and not responding to commands,
but when only PC' monitor works all is fine

---

### Post by GwL3eNC on 2013-08-31
ok, sadly i'm not the best in driver and hardware trouble. If you want to try another driver you can use this repositorys

[B]ppa:ubuntu-x-swat/x-updates (stable but older)
[/B]**ppa:xorg-edgers/ppa  (newes)**

You can try for example

sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

Hope it helps you.

Ps: stupid smilys is a : and a x

---

### Post by barabba2005 on 2013-08-31
i can not add the repositorys

---

### Post by GwL3eNC on 2013-08-31
Dear barabba2005, a bit more information would be fine? I have tested adding the edgers repo and it seems
to work. I dont want to press Enter, but i think the ppa is ok. Do you get an error message or something
like that.

Here you can see the ppa without the smily [http://www.ubuntuupdates.org/ppa/xorg-edgers](http://www.ubuntuupdates.org/ppa/xorg-edgers)

---

