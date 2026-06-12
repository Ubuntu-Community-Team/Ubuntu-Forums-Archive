---
title: "starting X with parameters"
date: 2010-07-29
forum: Installation &amp; Upgrades
---

### Post by wil on 2010-07-29
Hi 

I would like gdm to start X with the -ac parameter how would I do that.
see [http://www.x.org/archive/X11R6.8.1/doc/Xserver.1.html](http://www.x.org/archive/X11R6.8.1/doc/Xserver.1.html)


Thanks

---

### Post by dino99 on 2010-07-29
as said, use whith care:

-ac
    disables host-based access control mechanisms. Enables access by any host, and permits any host to modify the access control list. [COLOR="Red"][SIZE="3"]Use with extreme caution[/SIZE][/COLOR]. This option exists primarily for running test suites remotely.

---

### Post by wil on 2010-07-29
I know I have to use with care but I would like to use it.

I can bypass the -ac if I can somehow get the host permanently in the xhost file. 

so at start up I want
xhost +myremotemachine

How would I do that? there must be some kinda startup script for the user.

---

### Post by wil on 2010-07-29
Ok

I added xhost +myremoteserver to the end of ~/.profile and is now working fine

Thanks

---

