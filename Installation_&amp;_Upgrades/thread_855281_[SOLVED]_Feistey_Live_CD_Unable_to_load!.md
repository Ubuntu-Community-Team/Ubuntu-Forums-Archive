---
title: "[SOLVED] Feistey Live CD Unable to load?!"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by sp0nge on 2008-07-10
Hello people! 

I am here today faced with something I have not encountered before. 

My sister came in town with a desktop she said that is just super slow and the web browser crashes on a regular basis. When I turned it on, good 'ol windows give me a BSOD:

```
*** STOP: 0x0000007B (0xFD903BB0,0xC0000032,0x00000000,0x00000000
INACCESSILE_BOOT_DEVICE
```

To which I made every effort to resolve (there has been no new hardware added to the machine, all hardware is compatible, and even starting in safe mode brings back the BSOD)

After selling my sister on ditching windows and trying Linux out, I popped the live Feisty live CD in and started 'er up. First I get a message:

```
UNABLE TO LOCATE RSDP
```

and that passes, the install continues. 

we get down to: 

```
* Starting DHCP D-Bus daemon dhcdbd      [ OK ]
* Starting Network Connection manager NetworkManager      [ OK ] 
* Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon

```

We lock up here for a good 5-7 minutes, where I get:

```

Timeout reached while waiting for return value
Could not receive value from daemon process.

```

Why can I not even get the live CD to work?! I know it's good. I've run it on all 3 machines currently on the network.

---

### Post by wpshooter on 2008-07-10
First if you are getting to this point, have you checked the integrity of the Ubuntu Cd by running the verification function that is found on the initial Ubuntu boot screen menu.  I would do this even though you say you have used this CD on other machines, to make sure that you do not have a CD drive reading problem.

P. S. - if it were me I would not bother with Feisty but would try to install either Gutsy or Hardy instead.  IMO, at this point it would probably be Gutsy.

---

### Post by sp0nge on 2008-07-10
Thanks for your input. I did run the verification on the CD with no problems. This time we get down to : 

```

Starting GNOME Display manager...

```

Where we hang indefinitely. 

As far as booting to Feisty, I know I probably should, but at this point I really just want to get the machine running. Do you think it's a show stopper to be using Feisty? In theory, the machine should still be able to load the OS from the Live CD, right?

---

### Post by wpshooter on 2008-07-10
Have you tried the safe graphics mode ?

---

### Post by sp0nge on 2008-07-11
I did. 

In fact, I restarted in safe graphics mode and let the machine run, just to see what would happen. After about 2 hours, it passed the line it was stuck on and then went to the next line (something about cupsd) where it hung all night. The RAM was upgraded in this thing not too long ago, I suppose it's possible the RAM is bad somehow. Otherwise, I don't see any reason the Live CD isn't working.

---

