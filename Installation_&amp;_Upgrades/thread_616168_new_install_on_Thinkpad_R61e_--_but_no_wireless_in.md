---
title: "new install on Thinkpad R61e -- but no wireless interface!"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by bodhidharma on 2007-11-17
Hey folks,

Any insight would be a delight....

No wireless interface offered to me to use, when I boot to a
freshly installed Gutsy, on a Thinkpad R61e.

I just bought a new Thinkpad R61e, shrank the Windoze partition
(that was odd -- fresh out of the box, I had to do a major de-frag
before it was possible to shrink) and installed the new Ubuntu.  A
bit ugly at first, then got all my files onto the machine, now it is
very comfortable.  But this is weird: there is no wireless interface
offered in the network connections gnome applet thingy.  I am
using the other OS at the moment, so the hardware is there and
there is no security issue.  It just doesn't even offere to look for
wireless networks, nothing!

Any ideas?

Thanks!

---

### Post by wjp.reg on 2007-11-18
> **bodhidharma said:**
> Hey folks,

Any insight would be a delight....

No wireless interface offered to me to use, when I boot to a
freshly installed Gutsy, on a Thinkpad R61e.

I just bought a new Thinkpad R61e, shrank the Windoze partition
(that was odd -- fresh out of the box, I had to do a major de-frag
before it was possible to shrink) and installed the new Ubuntu.  A
bit ugly at first, then got all my files onto the machine, now it is
very comfortable.  But this is weird: there is no wireless interface
offered in the network connections gnome applet thingy.  I am
using the other OS at the moment, so the hardware is there and
there is no security issue.  It just doesn't even offere to look for
wireless networks, nothing!

Any ideas?

Thanks!

What do you mean about "a bit ugly at first"?

please post the output for the following command:

```
lspci
```

---

### Post by bodhidharma on 2007-11-18
Thanks, that's a fun command I didn't know.

Anyway, I think the relevant line is:

03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)


I will hunt around on the net using these as keywords, maybe someone
else has a solution... although of course if you know right away what to
do, I would be endlessly grateful.


(Oh, the "a bit ugly" was too provocative, I agree: I just meant how
when I upgrade or reinstall or something, I have to spend weeks doing
things on the new machine and finding them not what I want because I
had not set some config file the way I am used to it being....  I think this
is an issue with all versions of all OSes: every time you do it anew, you
have to make all the settings to be what you expect, no package
management system takes care of it all (or even a particularly large
fraction, it seems to me).

---

### Post by wjp.reg on 2007-11-18
Apparently [this thread]("http://ubuntuforums.org/showthread.php?t=512828&highlight=acer+aspire+3680") has the solution for your wireless card.

good luck!

---

### Post by bodhidharma on 2007-11-18
Thanks for the pointer, wjpg.reg, I will work on that....

I will post on this thread the results of my labours, in the
next few hours (hopefully).

---

### Post by bodhidharma on 2007-11-18
In case anyone has this problem in the future and finds this thread while searching:

As was suggested, there is plenty of discussion on this topic around, if you know what
to look for.  I have ended up getting the ndiswrapper approach to work.  The discussion
at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) was quite good.  In
the end I used almost exactly what they suggested, and am now on the 'net through
this troublesome wireless interface!  (There was only about one choice to make, of
which Windows driver to use, but there is a link (from the place suggested in the previous
posting on this thread, some acer ftp site in europe) to a place with zip files and I just
got the only one which made any sense at all (the only one which had anything about
drivers, and was for 32bit machines), and it worked fine.)

Thanks for the pointer, wjp.reg -- it was a lifesaver!

---

### Post by wjp.reg on 2007-11-18
Glad things worked out for you; and so fast! :guitar:

---

### Post by grybi on 2008-04-28
Re: new install on Thinkpad R61e -- but no wireless interface! [solved] 

I have similar problem  R61e model similar to 3000 N100


Intel Corporation PRO/Wireless 3945ABG Network Connection.
Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express.


Maybe you know how resolve this problem

---

### Post by bodhidharma on 2008-04-30
grybi -- did you try the ndiswrapper approach?  It's what
worked for my TP R61e....

bodhidharma

---

### Post by anantshri on 2008-04-30
for broadcam ndiswrpper approach works best

and for athros 

try madwifi experimental version.

---

