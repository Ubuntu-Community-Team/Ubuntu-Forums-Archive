---
title: "x.org fails after dapper upgrade"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by turnpin on 2006-06-02
Tried upgrading my laptop from breezy to dapper tonight.

On reboot x.org failed in GLcore: unable to locate nvidia or synaptics

have renamed nvidia to nv - seems to get pats tis
have commented out synaptics section - also seem to get past this

now have: "Cannot open device /dev/input/mice No such file or directory"

:confused: 
Help?

---

### Post by ubuntu_demon on 2006-06-02
first make sure your upgrade went well and you don't have a dependencies problem or something.

Go here : [http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

If you know the specs about your videocard do :
$sudo dpkg-reconfigure xserver-xorg
and choose the default/simple options as much as possible.

Do a reboot. 

If it still doesn't work post your /var/log/Xorg.0.log 
$gedit /var/log/Xorg.0.log

---

### Post by turnpin on 2006-06-02
Thanks Ubuntu_demon,

You were right, there was more configuration to do.  My upgrade must have stopped part way.  There was a dodgy package in there.

I had to reinstall the nvidia package afterward also.

Cheers :)

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=turnpin]Thanks Ubuntu_demon,

You were right, there was more configuration to do.  My upgrade must have stopped part way.  There was a dodgy package in there.

I had to reinstall the nvidia package afterward also.

Cheers :)[/QUOTE]
np :). I'm glad that you've solved it.

If you elaborate about how you have solved it you may help others.

---

### Post by turnpin on 2006-06-04
Mainly I followed the [instructions you posted]("http://www.ubuntuforums.org/showthread.php?t=186672") 

In particular restarting the package configuration did a lot:

$ sudo dpkg --configure -a

and changing the display driver in /etc/X11/xorg.conf from nvidia to nv

Once the computer rebooted properly into gnome I reinstalled the nvidia-glx driver.

My main problem was that I didn't realise that the upgrade had failed to complete.
:-k

---

