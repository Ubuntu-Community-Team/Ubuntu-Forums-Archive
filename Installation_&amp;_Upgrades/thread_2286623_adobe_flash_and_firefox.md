---
title: "adobe flash and firefox?"
date: 2015-07-13
forum: Installation &amp; Upgrades
---

### Post by Camilia on 2015-07-13
Since I upgraded to Ubuntu 15.04 adobe flash drive out of date and firfox shown out of date. Unable to view videos. How do I upgrade them?

I tried upgrading from the internet. I downloaded it and then extracted it. No success.

---

### Post by sudodus on 2015-07-13
The best way to get flash is via the repositories

```
sudo apt-get install flashplugin-installer
```

or if you want a whole package of non-free packages (including flash)

```
sudo apt-get install ubuntu-restricted-extras
```

Depending of what you have done (installed) now, you may have to remove the current flash software.

---

### Post by Camilia on 2015-07-13
Thanks!! Fixed!!

---

### Post by sudodus on 2015-07-13
You are welcome :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by Camilia on 2015-07-13
> **sudodus said:**
> You are welcome :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED
Oops!! Forgot about that.

---

### Post by Camilia on 2015-07-13
Now I have an error message: Broken Count > 0 

Tried the ubuntu software. Opening got option to fix it. Didn't seem to work. Message for sometime saying waiting for apt-get to exit. Tried the software updater. It too gives message waiting for apt-get to exit. Tried sudo apt-get. Did not understand how to perform the options shown.

ran sudo ps ax | grep apt and got this:
 8582 ?        S      0:00 sudo apt-get install ubuntu-restricted-extras
 8586 ?        S      3:30 apt-get install ubuntu-restricted-extras

Restarted and now all seems to be working. For upgrades working.

---

### Post by sudodus on 2015-07-13
You should run only one instance of ***sudo apt-get*** and ***software-center*** (apt-get should be run with sudo). I hope the current upgrades will finish nicely :-)

---

