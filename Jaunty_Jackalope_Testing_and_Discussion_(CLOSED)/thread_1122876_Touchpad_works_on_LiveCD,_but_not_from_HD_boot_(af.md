---
title: "Touchpad works on LiveCD, but not from HD boot (after Jaunty upgrade)"
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by camason on 2009-04-11
Hi all,

I updated my Asus Eee 901 today to 9.04 from 8.10. The only problem is my touchpad doesn't work. However, it works fine when I boot from the LiveCD.

I assume there is a configuration file out of place somewhere. I tried deleting my synaptics.fdi file in `/etc/hal/fdi/policy` but that hasn't helped.

Many thanks

---

### Post by camason on 2009-04-11
I've also completely removed `xserver-xorg-input-all` and reinstalled, and that has no effect.

I'm wondering whether I'm going to have to reinstall from scratch :(

Any thoughts on what I can check to try and troubleshoot this?

Many thanks

---

### Post by notoriousdbp on 2009-04-11
I find that sometimes happens on my laptop and I think it's caused by static.  I normally cure it by shutting down, removing the battery, booting up on AC Power which is the point at which the touchpad normally works again.  Then you can shut down and load the battery back on.

---

### Post by camason on 2009-04-11
Thanks, I tried that but it didn't work!

The little blighter is being formatted as we speak :)

---

