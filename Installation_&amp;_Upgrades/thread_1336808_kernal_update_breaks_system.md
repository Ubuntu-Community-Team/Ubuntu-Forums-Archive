---
title: "kernal update breaks system"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by hossdozero on 2009-11-24
OK, so I installed the updates that were released today, and I had to revert to the old kernal. When I try to run the new kernal (xx.xx.15 or something like that) the GUI won't start, it just takes me to a user login on tty1 which then sits there and flickers while my hard drive light does the same. 

What I would like to know is If anyone has filed a bug report, if there are any known workarounds that may have worked in the past with this issue, and if not, how do I select the old kernal (.14) by default.

At this point I have to start my computer, wait for the crash, press the reset button, and select the old kernal from the list that pops up. 

any help in this area would be appreciated

---

### Post by jjcv on 2009-11-24
I have not come across a new kernel version which sounds odd to me.

Anyway, if you are at a terminal login prompt after restarting and there is flickering then this is telling you that "X" is trying to start but is having problems.

Can you try Alt-F7 which will take you to the normal X screen if it is working and see any error messages?

Once it stops flickering you can also login at the login prompt with your usually login details.   The type "**startx**" and it will try and start an X session for you.   If it has problems it will leave a log file which will show what the problem is down near the bottom.  Usually this is 

/var/log/Xorg.log

type:   **less /var/log/Xorg.log** and scroll to the bottom looking for lines that start with **(E)** I think it is.

If when you try and run **startx** it says that a graphic session is already running then you might have to turn this off first.

/etc/init.d/gdm stop

or for kds

/etc/init.d/kdm stop

and try xtart again.

Remember, it is the error log you need to look in.

---

### Post by hossdozero on 2009-11-25
alt F7 won't work as my keyboard is left unresponsive at tty1, with no errors of any type, just nonstop flickering. 

pressing reset and choosing the older kernal from the list is the only way I've found to get the GUI up and running.

```
"less /var/log/Xorg.log"
```

returns 

```
/var/log/Xorg.log: No such file or directory
```.

I'm probably mistaken about the kernal update, but there was one for "linux image" that I remember, and I thought that included the kernal.

---

### Post by wojox on 2009-11-25
```
less /var/log/Xorg.0.log
```

Log into the 14-generic kernel and turn off your video driver if you have on activated. You may have to reset xorg.conf.

---

### Post by grafted_scion on 2009-11-25
This just happened to me new kernel update broke my video drivers.
Just install the driver again [http://ubuntuforums.org/showthread.php?t=990978&highlight=install+nvidia](http://ubuntuforums.org/showthread.php?t=990978&highlight=install+nvidia)

---

### Post by inevitable7 on 2009-11-25
this happened to me too

how do i revert back to the old kernel?

---

### Post by grafted_scion on 2009-11-25
Your old kernel should be listed in grub

---

