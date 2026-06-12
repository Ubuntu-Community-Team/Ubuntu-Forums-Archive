---
title: "Do I have Dapper installed?"
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by TheBigGeeUK on 2006-07-20
Probably a really stupid question but I've updated from Badger to Dapper using the Update manager and everything seemed to go well. It said your system has been updated.

I've rebooted and there doesn't seem to be any difference, is this right?

Is there a way of finding out which version of Ubuntu I have?

Obviously I'm a relative noob to this! lol

Gee

---

### Post by zxee on 2006-07-20
In a shell type > uname -a That should get you some info. The default look of dapper is different from breezy so either gnome didn't update or there's something else going on?

---

### Post by TheBigGeeUK on 2006-07-20
I did that and I got

> Linux gee-laptop 2.6.12-10-386 #1 Tue Jul 18 22:08:27 UTC 2006 i686 GNU/Linux


Once I've downloaded them and update manager has installed them (I presume) is there anything else I have to do?

Gee

---

### Post by jujoje on 2006-07-20
If you go to the 

system menu -> about gnome 

If gnome upgraded happily then you should be running 2.14. I think the breezy version was 2.13. Also it will tell you in the about ubuntu documentation on the first page.

Hope that helps

---

### Post by aysiu on 2006-07-20
```
cat /etc/issue
``` will tell you.

---

### Post by TheBigGeeUK on 2006-07-21
Well System - About Gnome said 2.12.1

and cat /etc/issue said

> Ubuntu 5.10 "Breezy Badger" \n \l

So what do I do now, to upgrade to Dapper?

Gee

---

### Post by Thirsteh on 2006-07-21
Change all your apt-get repositories to the respective Dapper Drake reps, then do apt-get dist-upgrade or update

---

### Post by madmetal on 2006-07-21
an usefull  guide
[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

---

### Post by TheBigGeeUK on 2006-07-21
cheers guys, I've followed that guide (should of read the guide before acting on update manager telling me to update!).

Doing it's download/upgrade now, so lets see what happens!

Gee

---

### Post by TheBigGeeUK on 2006-07-21
Okay I everything seemed to download properly but then I got this:

> Get:1076 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main slocate 3.0.beta.r3-1 [30.1kB]
Fetched 483MB in 1h11m54s (112kB/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/x/xkeyboard-config/xkeyboard-config_0.8-7_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xkeyboard-config/xkeyboard-config_0.8-7_all.deb)  Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.182 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


If I run apt-get update like it says would having already changed my repositories to the dapper ones affect my pc in a bad way?

Gee

---

### Post by tseliot on 2006-07-21
> **TheBigGeeUK said:**
> Okay I everything seemed to download properly but then I got this:



If I run apt-get update like it says would having already changed my repositories to the dapper ones affect my pc in a bad way?

Gee

I guess not. try with this again:
```
sudo apt-get update
```

---

### Post by TheBigGeeUK on 2006-07-21
Had a look at synaptic package manager, did an update and guess what....

Top tip take the tick out of "Dowload packages only"! lol

What a muppet!

Dapper is now installed....yippeee

Thanks everyone for you help!
a
I had to redo all my wifi bits and bobs like commenting out the make_reslov.conf paragraph in /etc/dhcp3/dhclient-script and then disabling ipv6 gain jas mylaptop was far to slow.

But I can now connect to the internet.

The only thing now is my wlan0/rausb0 does not automatically start when booting up, I have to manually do it. 

Anyone know how to sort this?


Gee

---

