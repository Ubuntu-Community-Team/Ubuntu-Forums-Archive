---
title: "Xsplash not working"
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sashin on 2009-09-18
For some reason, after I installed alpha 6 xsplash doesn't work.

At first its just text, and later its the ugly brown theme of it. How do I get the real theme working. This problem is on a real computer as well as a virtual box.

Anyone know how to fix this?

---

### Post by blakamin on 2009-09-18
Do you get some error messages about default rules? Wait until next week, it's apparently a udev issue that is being worked on.
[http://bugs.launchpad.net/bugs/430654]("http://bugs.launchpad.net/bugs/430654")

Either that or it has been disabled until this issue is sorted.

(I could be entirely wrong though, in which case someone with more knowledge than me will correct me shortly) ;D

---

### Post by Sashin on 2009-09-18
Well I am using Karmic 64 bit.

---

### Post by Sashin on 2009-09-18
Actually it works now, all I had to do was install ubuntu-xsplash-artwork and xsplash from packages.ubuntu.com

---

### Post by Giwex on 2009-09-18
At least it works for me. After the mess up last few days I've been waiting today to download and install Alpha 6 and after a huge set of errors during the boot all I have is a black screen with no option other than brutally switch it off. :(

---

### Post by GokuH12 on 2009-09-18
Same here! warning udev and black screen, no xsplash :(

---

### Post by Technoviking on 2009-09-18
Mine does display, but not very quickly. Get tones of udevs errors first.

T-V

---

### Post by dinxter on 2009-09-18
> **Technoviking said:**
> Mine does display, but not very quickly. Get tones of udevs errors first.

T-V
scott james remnant mentioned that the udev errors are harmless and should be fixed next week

---

### Post by Keyper7 on 2009-09-18
> **Technoviking said:**
> Mine does display, but not very quickly. Get tones of udevs errors first.

Same here. After the messages it works, but they are scary.

As a side note, booting to GDM is now hilariously much, much faster (the xsplash animation barely finishes one cycle) than logging from GDM to the desktop.

---

### Post by dinxter on 2009-09-18
> **Keyper7 said:**
> Same here. After the messages it works, but they are scary.

As a side note, booting to GDM is now hilariously much, much faster (the xsplash animation barely finishes one cycle) than logging from GDM to the desktop.
the plan seems to be,
- boot the upstart dependencies of gdm as fast as possible
- start gdm 
- then boot any dependencies that we can leave after gdm
pretty much a reversal of the boot process up til now, remember, the target for karmic+1 is 10s to the desktop with no hard drive activity on a reference machine, quite some work, i always imagined substantially changing the init process would be like opening pandora's box :)

---

### Post by Slug71 on 2009-09-18
Maybe we can have Plymouth for Karmic +1 now since there is no 10sec boot.

---

### Post by ft_ on 2009-09-18
If you get a black screen, ctrl-alt-del should restart.

Try to do like me (and others, although the majority get a console instead black screen) :

login
passwd
sudo start dbus
sudo start hal
sudo start network-manager
sudo kdm (or sudo start gdm)

When you're typing all that stuff, you can't see anything.

---

### Post by dinxter on 2009-09-18
> **Slug71 said:**
> Maybe we can have Plymouth for Karmic +1 now since there is no 10sec boot.
the init merge only started this week, give it time, theres still 7 months before the 10s target

---

### Post by Slug71 on 2009-09-18
> **dinxter said:**
> the init merge only started this week, give it time, theres still 7 months before the 10s target

7 months! :shock::shock:

I though 10s boot was targeted for Karmic release.:confused:

---

### Post by MacUntu on 2009-09-18
You thought wrong: [https://lists.launchpad.net/ubuntu-boot/msg00016.html](https://lists.launchpad.net/ubuntu-boot/msg00016.html) ;)

---

