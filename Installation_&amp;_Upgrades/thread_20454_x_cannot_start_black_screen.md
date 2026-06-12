---
title: "x cannot start black screen"
date: 2005-03-16
forum: Installation &amp; Upgrades
---

### Post by newbie user on 2005-03-16
i just started using linux as of about 3 days ago. the installation wasn't too hard. and  i can see how linux is better than windows.  that is once poeple can start to get the hang of it...but  as i just said it confusing to me. it was working fine then i was trying to install and use 3ddesktop and i was following the directions on one of the forums and when it told me to reboot i did. so now it comes to black screen with nothing on it. when i press ecscape or enter, a back ground pops up saying "i cannot start x "something i can't read the rest... the screen is cut off..but  it takes me to a command promt where it asks me to log in, which i can... but i don't know what to do after that... the last thing i remember doing is the command _sudo something nvidia-enable_. then rebooting it takes me to that screen. i dont' know what to do or how i can fix it.  please help.

---

### Post by afroman on 2005-03-17
My opinion would be that this is a graphics card (driver) problem
Try disable the nvidia driver and login, you can then proceed from
there!
I.e. boot up if it cums to a black screen press Ctrl + Alt + F1 ( maybe F2 )
  then disable the nvidia driver!

---

### Post by alastair on 2005-03-17
You need to look in the X logs i.e. the file :

/var/log/Xorg.0.log (hoary) OR
/var/log/XF86Config.0.log

Perhaps post the errors at the end (and some context perhaps).

Also, check the X config file :

/etc/X11/xorg.conf (hoary) or
/etc/X11/XF86Config (warty)

Perhaps post the log and the config file.

---

### Post by alastair on 2005-03-17
You could also try :

sudo dpkg-reconfigure xserver-xorg (hoary) or
sudo dpkg-reconfigure xserver-xfree86 (warty)

---

### Post by pugrit on 2005-03-17
i gad similar problems.

x server cant load.

the best solution for me is read the logs. usaully it tells what is the error.

---

### Post by newbie user on 2005-03-17
thanks guyz. i'll try it and see what i can do with yalls advice

---

