---
title: "Disappointing boot speed with Feisty - 54 seconds"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by hal8000 on 2007-05-08
I know Feisty 7.04 uses upstart in the boot process, but after installing bootchart, my boot time is a disappointing 54 seconds, how long to reach the desktop for evryone else?

System spec:
Intel P4 2.8G
Maxtor 160G ATA100 HD
Asus P4P800E motherboard

by contrast, the fastest system without any boot acceleration on same hardware is Pardus Linux at 27 seconds, but
knoppix  with initng loads in a blistering 18 seconds. To be fair performance may be a trade off against speed versus stability and with Knoppix, I do get periodic firefox crashes.

---

### Post by floke on 2007-05-08
you could try commenting out your unused connections in /etc/network/interfaces

Mine looks like this:

steve@steve-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

# auto eth0
# iface eth0 inet dhcp

# auto eth1
# iface eth1 inet dhcp

# auto eth2
# iface eth2 inet dhcp

# auto ath0
# iface ath0 inet dhcp

# auto wlan0
# iface wlan0 inet dhcp
--
I used to have a long boot delay while it tried to configure unused networks. Now it boots very snappily.

Hope this helps

** EDIT ** Agree with you about Pardus btw - it goes like a rocket!

---

### Post by trackerbishop198x on 2007-05-08
also internet lags more in ubuntu as opposed to windoze

---

### Post by NilsE on 2007-05-08
Took me 28 seconds to the login screen and total desktop was at 36 seconds including the time it took me to click on my name in the list and enter the password. And that also includes my WPA wireless connected.

I never complained or even thought of the boot up speed since I also boot up XP (when I have no choice) and that takes a few minutes.  

System Dell D620 - Centrino Duo

XP on an internal 80G SATA drive
Ubuntu on a 40G IDE in a carrier that replaces my CD drive

---

### Post by kelvin spratt on 2007-05-08
does it really matter as long as its not excessive its not a race to much speed loading can lead to unreliability 
in the long run

---

