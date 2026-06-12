---
title: "Boot takes a long time because of &quot;waiting for network configuration&quot;"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by Chrix75012 on 2011-10-14
Hi,

I upgraded my 11.04 Ubuntu to 11.10 and now the boot takes a long time. I've the message "waiting for network configuration" and after the "wait up to 60 secondes..."
I read some posts about this problem but:

[LIST=1]
[*]I've the symlinks to /var/run and /var/lock
[*]I deleted all pid files in /var/run
[/LIST]
Unfortunately, the problem is always there :(
Someone could help me ?

Thanks.

---

### Post by Chrix75012 on 2011-10-15
I found.

This problem came from interfaces configuration.
Before, I had this in /etc/network/interfaces:
```

auto lo
iface lo inet loopback
iface eth1 inet dhcp wpa-ap-scan 2

```

I removed the last line and now, system boots very fastly :)
And my wifi works well.

---

### Post by NiklasFalk on 2011-10-15
> **Chrix75012 said:**
> [/CODE]I removed the last line and now, system boots very fastly :)
And my wifi works well.Thank you a lot! Mine started to work now (after commenting out all things after the loopback) :D

I know that running a system without backup and upgrading incrementally immediately when upgrades are available is asking for problems, but why should you NOT be able to?

The fix that you needed to perform to get going three upgrades ago is still there and messing up things now.

I guess i have colliding network manages somewhere in there (since one was better than the other in handling my 3G modem), but I have no clue what package to remove to make things "prudent" now...

I had the "waiting for network" in the beginning, but fiddling (without a plan) with network manager packages (and related things) made that go away, but then I even lost wired network...

Now it looks ok (System Setting/Network says managed and "conencted" now, and the widget is displayed)

---

### Post by baubas101 on 2012-01-01
nice ! mine is also booting faster now ;) thanks ;)

---

