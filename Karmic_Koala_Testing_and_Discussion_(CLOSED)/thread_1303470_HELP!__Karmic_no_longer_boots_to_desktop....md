---
title: "* HELP! * Karmic no longer boots to desktop..."
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by c_martini on 2009-10-28
All I did this morning was launch the ATI Catalyst Control Center and setup multi monitors. I restarted and got this (photo attached). I just installed Karmic 9.10 rc this past weekend. All was more or less fine though I was trying to enable both my lcd monitor and an external larger monitor that I use for work. It was the first time I had used the Catalyst Control Center. Though the messages that display during boot do not indicate that this is the problem. They point to a problem with VirtualBox. I have had this installed for a couple of days and it was running fine so I don't know what could have caused this...

Any help to get me back into the KDE desktop would be much appreciated! I am stuck working in Windows for now :(

---

### Post by grizato on 2009-10-28
Put in you username
wait for the next promt put in your pswd
then try Ctrl-ALT-F7;)

I'm a bit of a noob but I remember reading something about thi in the ubtunu pocket guide

---

### Post by c_martini on 2009-10-28
> **grizato said:**
> Put in you username
wait for the next promt put in your pswd
then try Ctrl-ALT-F7;)

I'm a bit of a noob but I remember reading something about thi in the ubtunu pocket guide

Thanks for the suggestion, but that doesn't do anything for me. Is that supposed to be a keyboard shortcut to start the KDM?

---

### Post by c_martini on 2009-10-28
bumping this as its fairly urgent :sad:

---

### Post by philinux on 2009-10-28
At the login prompt login like you would at the GDM, then type startx and press enter.

---

### Post by c_martini on 2009-10-28
> **philinux said:**
> At the login prompt login like you would at the GDM, then type startx and press enter.

Thanks for the suggestion. I have now tried this also and this is what I get (photo attached). It appears that there is a weird character in the xorg.conf. I think I just need to either delete the xorg.conf or rename the backup and replace the broken one.

Do you remember the commands for doing this?

---

### Post by phillw on 2009-10-28
[http://ubuntuforums.org/showthread.php?t=972590](http://ubuntuforums.org/showthread.php?t=972590)

should help..

Phill.

---

### Post by jward3010 on 2009-10-28
Do the following in this order:

First login and type:
```
sudo gdm
```
If nothing:
```
sudo /etc/init.d/gdm start
```

Nothing still...

Finally, this will reset your xorg.conf to a default state:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Restart afterwards.

---

### Post by c_martini on 2009-10-28
> **jward3010 said:**
> Do the following in this order:

First login and type:
```
sudo gdm
```
If nothing:
```
sudo /etc/init.d/gdm start
```

Would the fact that I am running KDE mean that I should type instead:
```
sudo kdm
```
If nothing:
```
sudo /etc/init.d/kdm start
```
?

> **jward3010 said:**
> 
Nothing still...

Finally, this will reset your xorg.conf to a default state:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Restart afterwards.

Have tried all the above, but the same error is returned...

---

### Post by jward3010 on 2009-10-28
Yes, sorry, you're correct about the kdm stuff.

In regards the last point, did you restart after running the "dpkg-reconfigure" command? This is needed to completely bring down X.

---

### Post by c_martini on 2009-10-28
> **jward3010 said:**
> Yes, sorry, you're correct about the kdm stuff.

In regards the last point, did you restart after running the "dpkg-reconfigure" command?

Yes, restarted after trying that. I was again presented with the terminal login prompt. I again logged in and tried to startx, which returned the same error (as photo above). Again I tried your sequence of commands to no avail. I keep getting the same error no matter what I try.

I do have a backup copy of the xorg.conf file in the same directory. Should I try to copy the backup over the original? Not sure the syntax of the command for this?

---

### Post by jward3010 on 2009-10-28
At this stage it will do no harm. Simply type:
1. This renames your current one to something else.
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.problems
```

2. Now rename your backed up one to "xorg.conf" (For example):
```
sudo mv /etc/X11/xorg.backup /etc/X11/xorg.conf
```

---

### Post by c_martini on 2009-10-28
I was able to remove the corrupted xorg.conf and reboot back into KDE. It appears the Catalyst Control Panel had generated the corrupt xorg.conf!

Anyways, now kwin is messed up and continuously crashes on startup! I have attached a screenshot.

---

### Post by ranch hand on 2009-10-28
I am assuming, and hoping, that you did file the bugs on this.

I do not use 2 monitors but I do use an ATI card and we need all the bugs filed we can get.  The squeaking wheel gets the grease (I hope).

---

