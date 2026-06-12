---
title: "downgrade firefox to 3b4 from 3b5?"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by pbhj on 2008-04-28
Hey,

The upgrade to 8.04 (Hardy Heron) was abysmal for me, my first upgrade on Ubuntu (with kubuntu-desktop) since switching from Slackware. Now it's up and running the main problem is as follows:

Firefox 3 beta 5 (3b5) takes literally 10 minutes to start for me; I get nothing in console. Then if I click a drop-down, in menubar / toolbar, it locks up.

I've tried reinstalling, I've tried removing "libflashsupport.so" as suggested elsewhere. I've tried a new profile, I've tried opening in safe-mode.

FF 3b4 worked fine for me ... how do I now downgrade? I can't find the package anywhere.

Thanks,

pbhj
[posting from Konqueror]

---

### Post by pbhj on 2008-04-28
So I've had a go by using synaptic to remove firefox-3.0 (3beta5). I found the old 3beta4 package at [http://gb.archive.ubuntu.com/ubuntu/pool/universe/f/firefox-3.0/](http://gb.archive.ubuntu.com/ubuntu/pool/universe/f/firefox-3.0/) and installed it using gdebi.

Wouldn't then run due to ```
Could not find compatible GRE between version 1.9b4 and 1.9b4.
``` problem, of course I needed to downgrade xulrunner too. Doesn't work in synaptic, apt-get or aptitude (they're too clever!) instead I ended up doing:

```
dpkg --remove --force-depends xulrunner-1.9
```

Then again using the xulrunner at [http://gb.archive.ubuntu.com/ubuntu/pool/universe](http://gb.archive.ubuntu.com/ubuntu/pool/universe) and installing with gdebi.

Firefox ran, but no better, probably a little worse. Maybe the issue is elsewhere ..?

---

### Post by pbhj on 2008-04-28
Ok, think I've sorted this one.

```
strace firefox
```

Tried an strace of firefox and the app was reporting

```
EAGAIN (Resource temporarily unavailable)
```

and hanging for several minutes on

```
connect(50, {sa_family=AF_INET, sin_port=htons(16001), sin_addr=inet_addr("127.0.0.1")}, 16
```

Some searching led me to look at hosts and DNS issues. I tried altering hosts, hosts.allow and nsswitch.conf without any joy.

Then I tried pinging localhost and 127.0.0.1 ... wouldn't ping. Checked Iptables wasn't causing problem by doing iptables -F and -X. So, have you guessed yet?

Local loopback interface hadn't been brought up.

Running 

```
ifconfig lo up
```

gets me back to a usable firefox, with only some hanging due to dodgy flash support(!) but I can live with that for now. Posting from firefox 3 beta 5 now, hope this helps someone.

---

### Post by tristan@Ubuntu on 2008-07-10
Add exactly the same problem following a recent upgrade. Starting lo fixes the problem. Why NetworkManager does not start lo? ???

---

