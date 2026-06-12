---
title: "root access from live CD?"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by frankdn on 2008-05-04
Hello all, my first post!

It's been a few years since I used a linux distro regularly (it was red hat 9, if that's a clue) and I figured I'd give ubuntu a try.

The 8.04 live CD boots my newish Dell laptop (a D830) successfully, and the network tool recognizes my wireless device (Intel PRO/Wireless 3945ABG).

I cannot activate the wireless however.  It fails to get an IP address.  I immediately rebooted into windows to verify that the router was still working, and it was.  Under windows, connection was automatic and immediate.

Do I need to be root, to activate the connection?
- If not, how do I debug this?
- If so, why isn't the activation button grayed out?  (and what's the root password?)

thanks!

---

### Post by Pumalite on 2008-05-04
Wireless is usually configured after the installation. Some cards are recognized right away. The best is to have a router providing you with DHCP at boot with dynamic IP.

---

### Post by lemming465 on 2008-05-04
> Do I need to be root, to activate the connection?
If it wasn't configured automatically, probably.

> If so, why isn't the activation button grayed out?
Most of the GUI administrative dialogs have an *unlock* button which is required to actually change things.

> (and what's the root password?)
Ubuntu uses sudo; the first account created is put in the admin group, which has privileges in /etc/sudoers.  There is no root password; by default the root account is locked and can't be used for interactive logins.

You could set a root password (via sudo passwd root), which would prompt for your password, but there isn't usually a reason.  Run command line stuff as root with sudo, and GUI stuff as root with gksu instead.

If you are running on the live CD, there is no password for the desktop user either, and I think the live CD user can run stuff as root without being further prompted.  It may have a NOPASSWD: clause in /etc/sudoers.

Wireless is one of the touchier areas under Linux at present; to figure out why things weren't working we'd need more information.  E.g. is the unprotected wireless, or is there WEP or WPA2 or something turned on to protect it?  Is the SSID being broadcast, or hidden.  I use WPA2 with a hidden SSID on my home wireless, and I had to do some configuration work with wpa_supplicant before it would work.  There are directions for that on the wireless threads.

---

