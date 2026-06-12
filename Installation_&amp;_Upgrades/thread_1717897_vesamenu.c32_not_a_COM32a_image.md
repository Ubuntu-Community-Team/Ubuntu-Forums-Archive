---
title: "vesamenu.c32: not a COM32a image"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by lapor on 2011-03-30
I want to install lubuntu 10.04 on my AMD 1,14 GHz, 256 MB and Nvidia GeForce FX 5500. But it doesn't boot from USB. It writes:
vesamenu.c32: not a COM32a image
boot:

So, something's wrong.
I tried to install lubuntu 10.10, but it just freezes. It shows that something crashed (timezones, layouts of keyboard,...).

Help!

---

### Post by coffeecat on 2011-03-30
Did you use the 10.10 version of usb-creator-gtk (that's Startup Disk Creator) to write a  10.04 ISO to USB? That's a known bug (or pair of bugs).

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/686041](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/686041)
[https://bugs.launchpad.net/ubuntu/maverick/+source/usb-creator/+bug/645818](https://bugs.launchpad.net/ubuntu/maverick/+source/usb-creator/+bug/645818)


You need to use the 10.04 version of Startup Disk Creator for a 10.04 ISO or use unetbootin. Or try one of the workarounds suggested in those two bug reports.

---

### Post by lapor on 2011-03-30
Yes, I used Ubuntu 10.10 to create liveUSB.  
There is diffrence in versions of syslinux. 10.04 have 3.63 and 10.10 have 4.01.
Now, I am trying lubuntu 10.10 alternate install.  For now it's looking promising.

But at least I learned some new stuff about linux :)

Thanks

---

### Post by lapor on 2011-03-30
I managed to install lubuntu 10.10, but now there is another problem. I get to the point where I have to write username and password, then it sudenly restarts. After that I get to the same point (log in), but it just frezzes.
Any idea, what could be wrong?

---

### Post by coffeecat on 2011-03-30
Sorry, no. I have no experience of Lubuntu. Or this could be a problem with 10.10 on your particular hardware.

I suggest you start a new thread with a descriptive title. The title of this thread may not attract people who would be able to help you with this. Good luck!

---

### Post by lapor on 2011-03-30
Thanks. I'll try 10.04, but tommorow. And after that experience I will see, will I need more help or not.

---

### Post by Dutch70 on 2011-03-30
When you get to the part that says boot: ...Try typing in "live" without the quotes, and hit enter. Let us know if it works please.

---

### Post by lapor on 2011-03-31
I managed to install 10.04 and it works like a charm. Lxde has a lot of bugs, but it will do for what is ment (playing music in a rock bar).
I read about "live" on the link coffeecat gave me. Some say it works, some it doesn't. They also mention word "help". But I didn't try it. I made liveUSB on my brothers computer with Ubuntu 9.10, so it worked well.

Here is the link again:
[https://bugs.launchpad.net/ubuntu/maverick/+source/usb-creator/+bug/645818]("https://bugs.launchpad.net/ubuntu/maverick/+source/usb-creator/+bug/645818")

---

