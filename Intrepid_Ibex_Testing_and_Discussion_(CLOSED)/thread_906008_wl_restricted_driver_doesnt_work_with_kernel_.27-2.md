---
title: "wl restricted driver doesnt work with kernel .27-2"
date: 2008-08-31
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by vishalrao on 2008-08-31
i have an hp tablet tx1302au with broadcom wifi chipset. installed intrepid alpha4 (amd64) and updated it to get the latest and greatest kernel .27-2

by default the wl restricted driver is installed enabled but does not show up in network manager.

doing "lsmod | grep wl" only shows:

```
wl              1085520 0
ieee80211_crypt   14596 1 wl
```

shouldnt it also show some "mac80211" line in there somewhere?

note: i tried wl on hardy (amd64) with this thread and it worked well for me: [http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

but in any case if i disable/blacklist wl and install b43 driver with firmware my wifi works very well with networkmanager and all :)

---

### Post by gnomeuser on 2008-08-31
probably safe to say.. maybe. The best option would be to tell HP that their hardware is not supported by your OS of choice, the more polite complaints they hear of this sort the more likely it is they will use their sway to get us specifications to write an open driver or simply change their chip vendor to a more friendly supplier.

The buttomline is, we can't do anything to fix your driver, we don't have the source code and the question if it will be compliant is largely up to Broadcom not the Linux community as they are the only ones with the power to make it work.

The good news is that an open replacement for many Broadcom chips is in development, I don't know if it supports the model in your machine yet but with your bugreports I am sure it can be done. Then this will never be an issue again. In the meantime I am sorry, but it is very likely it will suck, however please remember who did it to you..

---

### Post by vishalrao on 2008-08-31
wl actually works fine with Hardy proposed kernel update. and for intrepid b43 works fine for me... i just wanted to know what will work most seamlessly (avoid command line tinkering) with intrepid, wl or b43?

---

### Post by Slug71 on 2008-08-31
wl is working fine for me with 2.6.27-2, my WPA wouldnt allow it to connect at first though. A few people had the same prob with WEP. I used a wired connection to the router and disabled the WPA(connected with wireless) and then enabled it again and did a restart and it worked. Make sure youre allowed to use wireless in Admin-Users and Groups.

---

### Post by Mazza558 on 2008-08-31
Upgrading from Hardy, the broadcom ndiswrapper driver still works in 27.2, which is pretty impressive (considering Gutsy > Hardy broke the wireless).

---

### Post by drfox on 2008-09-07
I just did a fresh install with Alpha 5 using the AMD64 kernel, and wl does not work for me on an HP laptop with Broadcom 4311 wireless.
I have wl "checked-enabled" and "in use," and I have the Broadcom 43 "in use." I have also tried it with Broadcom 43 not enabled.

I was previously using ndiswrapper successfully in Hardy.

Any suggestions, other than wait for the next kernel?

---

