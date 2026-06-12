---
title: "lost user log out/shutdown button on panel next to time."
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Slug71 on 2009-09-26
After some updates yesterday or day before i lost the button with the user name which allows you to log out, restart, shutdown etc.

Is there a way to restore that?

---

### Post by philinux on 2009-09-26
I had two volume controls, no network icon. 

A shutdown and startup sorted it out.

---

### Post by drs305 on 2009-09-26
> **Slug71 said:**
> After some updates yesterday or day before i lost the button with the user name which allows you to log out, restart, shutdown etc.

Is there a way to restore that?

There are actually 3 different icons you might be talking about. All can be restored by right clicking the panel, Add to Panel, and selecting one of the following. (A reboot might restore it as well, as philinux mentioned):

Shut Down:  Red icon, Shutdown/Restart/Suspend/Hibernate
Log Out: Person with Right Arrow: Log Out/Switch User
User Switcher: Displays the username: Acct Info/System Info

---

### Post by philinux on 2009-09-26
I think the one he means is called "indicator-applet-session 0.1"

---

### Post by Slug71 on 2009-09-26
> **philinux said:**
> I think the one he means is called "indicator-applet-session 0.1"

Yeh i think thats the one. It was default. Had the user name with a cloud type thing on the left of the name.

---

### Post by ajgreeny on 2009-09-26
Don't forget that the icons you see may be very different to those described, depending on your theme, so look for the name rather than the icon.

---

### Post by raqball on 2009-09-26
I had the same issue... Add the indicator applet session and after a few moments you will get an error... Click refresh when it pops up and it's added back...

Good luck :)

---

### Post by philinux on 2009-09-26
> **Slug71 said:**
> Yeh i think thats the one. It was default. Had the user name with a cloud type thing on the left of the name.

Yep well it has been crashing a bit. Rebooting or logout then back in seems to restore it.

---

### Post by raqball on 2009-09-26
> **philinux said:**
> Yep well it has been crashing a bit. Rebooting or logout then back in seems to restore it.

I tried rebooting and it was not added back... I had to add it back to panel and then after getting an error click refresh.. It's added back for now, but I don't know for how long :)

---

### Post by Slug71 on 2009-09-26
Yeh thats the one. How do i get it back to the corner on the left of the clock now? 

ps. didnt get the error yet. :)

---

### Post by drs305 on 2009-09-26
> **Slug71 said:**
> Yeh thats the one. How do i get it back to the corner on the left of the clock now? 

ps. didnt get the error yet. :)

Right click on it, Move, then drag it where you want. If it bumps up against another and won't go past it you may have to "unlock" the other icon first by unticking "Lock to panel".

I've never had that one on my panel until I just added it. Now I'll have to see how long it stays.

---

### Post by raqball on 2009-09-26
> **Slug71 said:**
> Yeh thats the one. How do i get it back to the corner on the left of the clock now? 

ps. didnt get the error yet. :)

Right mouse click on the applets to the right of it and un select *lock to panel* then move them to all to the left. Next, move them all in the place where you want them and lock them back to panel...

---

### Post by Slug71 on 2009-09-26
> **raqball said:**
> Right mouse click on the applets to the right of it and un select *lock to panel* then move them to all to the left. Next, move them all in the place where you want them and lock them back to panel...

Awesome Thanks! :):)

---

### Post by Guruji on 2009-09-26
i have the same issue, the indicator applet crashes every now and then. When it crashes... the options "lock screen, log out, shutdown" appear in the system menu..  weird..

---

### Post by novafluxx on 2009-09-26
> **philinux said:**
> Yep well it has been crashing a bit. Rebooting or logout then back in seems to restore it.

Mine crashes on the new kernel -11, but when I boot with -10 it works fine!

---

### Post by LKjell on 2009-09-26
> **Guruji said:**
> i have the same issue, the indicator applet crashes every now and then. When it crashes... the options "lock screen, log out, shutdown" appear in the system menu..  weird..
Assume you do not delete that applet when it ask to, do a reinstall of ubuntu-desktop package will hopefully fix it.

---

