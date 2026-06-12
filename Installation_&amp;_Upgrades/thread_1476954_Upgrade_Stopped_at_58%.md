---
title: "Upgrade Stopped at 58%"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by bkuberek on 2010-05-08
Ubuntu Desktop Upgrade from 9.10 to 10.04 LTS

Last night I ran the upgrade via the Update Manager. Took several hours downloading, calculating changes, preparing, unpacking... then at 58% just stood there. It has been 14 hours total since I started the upgrade and it still says 58%.

The terminal says:

```

Preparing to replace javascript-common 6 ...
Unpacking replacement javascript-common...

```The system is still on and seems to be working. I wonder if I can interrupt the upgrade and try again. I am afraid to stop it and then be locked out after a reboot.

Please advise

Thanks

---

### Post by bkuberek on 2010-05-08
I just opened System » About Ubuntu, and it says I am using Ubuntu 10.04 LTS. However the upgrade window is still stuck at 58%...

---

### Post by bkuberek on 2010-05-08
so I tried running apt-get check to make sure everything was installed and I get:

```

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Any one can help me?

---

### Post by bkuberek on 2010-05-08
I did a <ctrl + c> and sotpped the javascript-common, the upgrade continued from there... let see if it will complete.

---

### Post by frantid on 2010-05-08
before you reboot do a 

sudo apt-get check

and possibly

sudo apt-get update

if you see errors, please post before rebooting.

---

### Post by kansasnoob on 2010-05-08
> **frantid said:**
> before you reboot do a 

sudo apt-get check

and possibly

sudo apt-get update

if you see errors, please post before rebooting.

+1! I'd also run:

```
sudo dpkg --configure -a
```

When the upgrade is complete before rebooting, and consider any error messages before rebooting.

---

### Post by bkuberek on 2010-05-08
Thank you all. It seems like javascript-common was the problem.

Twice I had to crtl+c on javascript-common and upgrade is going well. I may have to install javascript-common manually after.

I'll post updates.

---

### Post by bkuberek on 2010-05-09
So the upgrade seems to have gone successful. I removed and reinstalled javascript-common just to make sure, but it also seemed fine.

So far 2 things bother me:

* bluetooth keyboard is not working. I tried unpairing and pairing a few times.
* Apache2 also isn't working saying: "no listening sockets available, shutting down"

---

### Post by bkuberek on 2010-05-10
This is the error I get while trying to start apache2:

```

 * Starting web server apache2
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
   ...fail!

```

did a little search and looks like there is something else listening on port 80. I just don't know what or how to find it.

I also wonder if the upgrade modified anything in the apache configuration, or perhaps didn't while it should have.

please advise.

---

### Post by bkuberek on 2010-05-10
ok so I did this:

```

# lsof -i :80
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
apache2 1207 root    4u  IPv6   5511      0t0  TCP *:www (LISTEN)

```

HA! for some reason apache was running. I killed that process and was able to start normally.

I still have trouble with bluetooth.

---

