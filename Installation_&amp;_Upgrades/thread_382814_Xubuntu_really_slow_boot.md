---
title: "Xubuntu really slow boot"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by Netspeed on 2007-03-12
I just installed Xubuntu on my brand-new Pentium 805, 2gb RAM, 250gb computer. Nothing else is on it. When it boots up, it takes about 6-7 minutes while it "activates swap" and "checks system files". It takes about 10-11 minutes before it gets to the login screen. What am I doing wrong? Could it be that I don't have a graphics card yet? I can't believe it would take that long to boot with the most stripped-down version of Ubuntu and a really new computer with a lot ogf RAM.

Help!

---

### Post by taurus on 2007-03-12
Can you post the output of these commands from a terminal?

Applications -> Accessories -> Terminal
```
cat /etc/fstab
free
sudo fdisk -l
```

---

### Post by Netspeed on 2007-03-12
Unfortunately I don't have an internet connection on that box yet so I can't copy/paste the results. What should I be looking for?

---

### Post by kerry_s on 2007-03-12
The no internet will slow the system down, because it will spend alot of time looking for a connection. Try at boot hit "e" move down 1 line and add "nodhcp dhcp=off" and enter than "b" to boot. You can check your /var/log/boot.log to see where it's actually pausing.

looks like->

root=UUID=785d88e5-4a57-4d97-a852-85a73bcde479 ro nodhcp dhcp=off

(Yours will look slightly different from mine, i'm running a cut down fiesty)

---

### Post by Netspeed on 2007-03-12
Seeing that my boot process is 10 minutes, where in the process would i hit the "e"?

---

### Post by kerry_s on 2007-03-12
The very first screen where you select the boot. Where it has the 10 second count down.

---

### Post by Netspeed on 2007-03-14
I fixed the slow boot....go figure that a graphics card and a network cable will do! 
Now for the problem: I've lost my network connection. The network manager doesn't even see the pppoe(?) installed. I think it might have been because I added the "nodhcp dhcp=off" command. I can't get to the boot screen as mentioned above. I constantly hit "e" as the system starts but it keeps going to the desktop.

---

