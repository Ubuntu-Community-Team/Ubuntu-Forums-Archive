---
title: "Great, great, great"
date: 2006-05-25
forum: Installation &amp; Upgrades
---

### Post by Cysman on 2006-05-25
Well, here it is.  I was trying to upgrade from Breezy to Dapper 6.06 and while it was installing the updates, it froze up on me during the network interface config.  I had to shut it down manually and when I turn the computer on, th OS stops loading up and the detectecting network interfaces and then freezes.  Can someone tell me how to get into some sort of failsafe mode and what command to type to get back in and get to some of my local files?  Please??](*,)

---

### Post by Lord Illidan on 2006-05-25
Press control c when it freezes

---

### Post by Cysman on 2006-05-25
[QUOTE=Lord Illidan]Press control c when it freezes[/QUOTE]

Ok, let me revise what happens.  I tried to boot into an older kernel version....and it did, sort of.  I got to the gnome log in screen but when I try and log in, all I get is a brown screen.  Help

---

### Post by NoUse on 2006-05-25
Start the machine in recovery mode via the grub menu and then you can use apt-get to continue the upgrade:
```

apt-get -f install
apt-get dist-upgrade

```

---

### Post by Cysman on 2006-05-25
[QUOTE=NoUse]Start the machine in recovery mode via the grub menu and then you can use apt-get to continue the upgrade:
```

apt-get -f install
apt-get dist-upgrade

```[/QUOTE]

Thanks, try it now....

---

