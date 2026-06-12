---
title: "Network manager will not connect me"
date: 2009-03-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lcv on 2009-03-10
Have just upgraded from ubuntu 8.10 to Jaunty. All good but no network ability. No wireless, no ethernet, nothing. Keep clicking onto my network (wired and wireless) but just will not do the do.....

Kernel problem or NetworkManager Applet ?  I see this one is now 0.7.0.99.  My Linux Mint version is 0.7.0.  Deskto cd for Jaunty is 0.7.0.27 (I think)
and that works fine! 

Erm.... pretty stuck now.  Anyone hit this one and found a solution that is probably simple and straight forward but I am just too tired to see?!
Thanks

---

### Post by ubu-for on 2009-03-11
Try this and disable "work offline" in Firefox.

```
sudo pppoeconf
```

[http://ubuntuforums.org/showthread.php?t=1083934&page=2](http://ubuntuforums.org/showthread.php?t=1083934&page=2)

---

### Post by davehoz on 2009-03-30
Changed /etc/NetworkManager/nm-system-settings.conf to:

[main]
plugins=ifupdown,keyfile

no-auto-default=00:1e:8c:42:68:9f,

[ifupdown]

managed=true

but now I have 2 entries in the wired networking part of the Network Manager applet:

Wired Connection  1
ifupdown(eth0)

how to remove the second entry to make the Wired Connection 1 the defult for the ethernet port of my laptop?

---

