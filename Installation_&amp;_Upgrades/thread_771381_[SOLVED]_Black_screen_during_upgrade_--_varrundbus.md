---
title: "[SOLVED] Black screen during upgrade -- /var/run/dbus missing"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by andguent on 2008-04-27
I did my upgrade from Gutsy to Hardy last night. It took some hacking and the recovery console, but I eventually got it up. I'm sharing the info in case it is useful to anyone else. Also, if anyone can comment on whether I should post this as a bug or not, please let me know.

**The problem**
Half way through the upgrade from Gutsy to Hardy, the screen went black. I let it sit for a while, but the hard drive light stopped blinking. Eventually I did a Ctrl-Alt-Del and it actually shutdown gracefully (Ubuntu logo and shrinking bar).

**Attempted fix**
I started up in recovery mode, entered my password, and did an apt-get update. On the end of that output, it said something like "Previous install not complete, run dpkg --configure -a". I did that, and got too many lines to see even in my scrollback buffer.

I did a "dpkg --configure -a > /tmp/dpkg.dump 2>&1" to dump the whole output into a text file. The top of that output showed:
```
Setting up dbus (1.1.20-1ubuntu1) ...
Warning: The home dir /var/run/dbus you specified can't be accessed:
No such file or directory
The user `messagebus' already exists. Exiting.
chown: cannot access `/var/run/dbus': No such file or directory
dpkg: error processing dbus (--configure):
 subprocess post-installation script returned error exit status 1
```

**Ultimate fix**
In recovery mode, I did the following:
```
mkdir /var/run/dbus
dpkg --configure -a
apt-get upgrade
apt-get dist-upgrade
```

**History**
Possibly related, but this Compaq laptop had Fiesty beta installed, then upgraded to Gutsy, now Hardy. Not sure if this means anything. I also downloaded the entire Hardy CD via bittorrent, added it as a repository, and then did the upgrade just to avoid hitting the mirrors.

I attached my full dpkg output that was from the dpkg --configure -a while within recovery console.

At this point, I'm booting up fine. I havin't had time to fix my wifi yet, but most everything else looks same/normal/good.

Does anyone recommend submitting this as a bug report? Thanks.

---

### Post by bprof on 2008-10-28
Many thanks to you for this great post which solved my problem.

---

### Post by bprof on 2008-10-28
Forget to add I agree that this should be submitted as a bug.

---

### Post by andguent on 2008-10-28
Glad to know it helped.

---

### Post by bgiannes on 2008-11-19
Yes, thank you for the post....

---

### Post by andguent on 2008-11-19
Is anyone having this issue going from Hardy to Ibex? My issue was only with Gutsy to Hardy. If anyone can post additional information about what you were going from and going to, maybe we can find a pattern. Thanks.

---

