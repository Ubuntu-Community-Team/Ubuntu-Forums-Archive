---
title: "a new comer is trying to find out steps to download and install NTP package"
date: 2013-04-18
forum: Installation &amp; Upgrades
---

### Post by ubmagic on 2013-04-18
I have some REDHAT exp., but never worked on Ubuntu before.
Now, I need to find out where I can download ntp package, and steps how to install, as well as configure it.
Would you please help me out?

Much appreciated.

Thanks,

---

### Post by steeldriver on 2013-04-18
Hello and welcome

What exactly are you trying to do? what version and flavor of Ubuntu do you have?

The **ntpdate **package should have been installed and configured at install time, I think - that's usually all that's needed on the client side for setting up timezones / managing daylight savings / syncing to 'internet time'

If you really need the ntp package - that's just called ntp, you could install it via the regular GUI package management tools or

```
sudo apt-get install ntp
```

---

