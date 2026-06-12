---
title: "Upgrade/Full Install 8.04 no gui after login"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by lordfly911 on 2008-04-30
I am installing on an older PowerEdge 2400 server using the desktop version of 8.04.  I installed 7.10 yesterday and everything worked great.  I did all the upgrades and then proceeded to upgrade to 8.04.  When the computer rebooted, all went good, and I was able to login.  But, the next screen is just the brown screen with the cursor, which I can move.

Okay, I thought, maybe there was an issue.  So I downloaded 8.04 and installed it.  And again I have the same issue.

I think it has to be a screen settings issue since originally the desktop was full screen and now the screen is just a little narrower, as if I need to adjust the monitor.

I am still a little green here.  I have 7.10 upgraded to 8.04 installed on my laptop under Virtual PC 2007 and all is working great (except for the annoying screen size issue).

Thanks for any help

---

### Post by dstew on 2008-04-30
I think the command to reconfigure the display in Hardy is```
gksudo displayconfig-gtk
```From the command line, try```
sudo dpkg-reconfigure xserver-xorg
```but I have heard this doesn't work in Hardy...

---

### Post by iJaffa on 2008-09-20
Hi there,

I have the exact same problem, except with mine it is a Dell PowerEdge 750. I managed to get the gnome started under root by doing:

```
sudo su
password
startx
```

but trying to get gnome started under my regular user will not work and just gives me the 'poo screen' - the brown screen with mouse ;)

I hope someone can help me with this one.

Cheers,

---

### Post by manishtech on 2008-09-20
> **dstew said:**
> From the command line, try```
sudo dpkg-reconfigure xserver-xorg
```but I have heard this doesn't work in Hardy...
It works for me in Hardy

---

### Post by iJaffa on 2008-09-20
> **manishtech said:**
> It works for me in Hardy

I just tried it under a failsafe terminal, and the configuration utility worked, however it didn't actually fix any problems, and just went through the keyboard layout setup :S

---

### Post by manishtech on 2008-09-21
> **iJaffa said:**
> I just tried it under a failsafe terminal, and the configuration utility worked, however it didn't actually fix any problems, and just went through the keyboard layout setup :S
I tried it in single user mode.

---

### Post by iJaffa on 2008-09-21
> **manishtech said:**
> I tried it in single user mode.

I have tried that also, still only gives me keyboard options and finishes the configuration utility.

---

### Post by tastybrains on 2008-10-06
any luck fixing this? i'm experiencing the same issue. if anyone has fixed this, please post!

---

