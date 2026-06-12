---
title: "[SOLVED] Upgraded to 7.10, cant send/receive email."
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by badmotor on 2007-10-20
Upgraded to Gutsy today, and when I press send/receive (Evolution email client), it just waits... and waits... and times out. Weird.

I haven't changed any settings, my ISP support has closed for the day (when you say you are using Linux, they throw their hands up and say "we don't support that" anyway).

Has anyone else experienced this?

---

### Post by Arenlor on 2007-10-20
I had a similar problem, try installing sendmail and see if that fixes it for you, it did for me but I use Thunderbird.

---

### Post by mybunche on 2007-10-20
Check your email settings first if you haven't done so.
At times I've had timeout problems too, could be ISP, next day it worked fine.

---

### Post by badmotor on 2007-10-20
OK, and now I've discovered I can't download anything to install from "Add/Remove"... there's a bit of a theme going on here.... :confused:

---

### Post by Arenlor on 2007-10-20
Can you ping anything?
```
ping security.ubuntu.com
```

---

### Post by badmotor on 2007-10-20
sorry, yeah and can browse the WWW fine...

---

### Post by Arenlor on 2007-10-20
Can you sudo apt-get update?

---

### Post by badmotor on 2007-10-20
No.... it seems to have just timed out while connecting.

---

### Post by Arenlor on 2007-10-20
Can I see the contents of your /etc/hosts file just to make sure?

---

### Post by badmotor on 2007-10-20
Sure, whats the best way to get to that? (sorry, newbie here)

---

### Post by badmotor on 2007-10-20
Wait, think I found it:

127.0.0.1 localhost
127.0.1.1 todd-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by badmotor on 2007-10-20
Anybody got any ideas?

---

### Post by Arenlor on 2007-10-20
What type of router do you use?

---

### Post by badmotor on 2007-10-21
A Netcom NB5 ADSL Router (hope this is what you mean), has a built in firewall.

---

### Post by Arenlor on 2007-10-21
Try this [https://www.opendns.com/start?device=ubuntu#step1](https://www.opendns.com/start?device=ubuntu#step1)

---

### Post by badmotor on 2007-10-21
Hey!, that did it. Thankyou so much. I was having all these nightmares about having to do a fresh install.
I don't fully understand what I've done here, but it has worked. thanks again Arenlor.):P

---

