---
title: "i try to install Ubuntu 10.04 - and i can't log in"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by maz.basha on 2010-05-03
hello

more than 50 times i try to set up the new ubuntu 10.04 but after i finish i cant log in
only i get log in screen with my name and when i press enter the screen is stop and nothing work:(.

please any one know what is the problem and how can i fix it:confused:
my pc hardware is
mb: asus p5q
gc: nvidia 9800 gtx
ram: 1 g


thanks

---

### Post by blakdogg on 2010-05-05
I have the same problem. I installed 10.04 from scratch about three days ago, it had worked fine since then. I have been using it constantly, including installing programs, rebooting and even tweaking desktop. As I said it worked fine.

A few minutes ago, I rebooted and now I cannot login or rather login does not reach to the desktop. 

There are no failure messages, it just returns to the prompt. If I enter the wrong pw I do get an error, so thid is dufferent

will keep  u posted.

---

### Post by blakdogg on 2010-05-05
If you use the install CD to boot ubuntu, you can turn off gdm by removing the gdm entry in /etc/X11/default-display-manager.  This file only has one line so this should be relatively easy, keep a backup.

Once you remove the line you can boot to the bash password prompt and from there you can login. I've found that boots and reboots are non-deterministic, sometimes they go to the prompt sometimes they don't. I have yet to figure out under what condition what happens. 

From the command line startx does not work. It pops up a black screen with a pointer and does nothing more.

Will keep you posted

---

### Post by blakdogg on 2010-05-05
Sorry dude, I bit the bullet and reinstalled this time no nvidia drivers. Wish me luck.

---

### Post by lightnb on 2010-05-06
I'm having the same issue. Was working fine, did an update, and now no login. switching to the terminal (ctrl+alt+F1), I can login fine. So the issue is not PAM or authenication related. 

If I enter:

```

sudo stop gdm
startx

```

I can get in just fine. So not an X configuration problem either.


This is probably a bug in the login script itself.

---

