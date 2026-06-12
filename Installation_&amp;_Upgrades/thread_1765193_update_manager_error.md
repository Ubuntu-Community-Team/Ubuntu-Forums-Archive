---
title: "update manager error"
date: 2011-05-22
forum: Installation &amp; Upgrades
---

### Post by thingsdontwork on 2011-05-22
Sorry if this is the wrong place for this but I'm kind of a little bit stuck. Update manager keeps giving me this error

''E:Type ‘ain’ is not known on line 1 in source list /etc/apt/sources.list.d/team-xbmc-ppa-natty.list''

I'm not very experienced at all this and slightly confused.

---

### Post by matt_symes on 2011-05-22
Hi

> **thingsdontwork said:**
> Sorry if this is the wrong place for this but I'm kind of a little bit stuck. Update manager keeps giving me this error

''E:Type &#8216;ain&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/team-xbmc-ppa-natty.list''

I'm not very experienced at all this and slightly confused.

The file /etc/apt/sources.list.d/team-xbmc-ppa-natty.list is corrupted somehow.

You can either delete the file......

Open a terminal and copy and paste or type

```
sudo rm /etc/apt/sources.list.d/team-xbmc-ppa-natty.list
```Enter your password it will not be echoed to the screen. This is normal.

You can then type

```
sudo apt-get update
```....Or you can try to fix it. Post the results of 

```
cat /etc/apt/sources.list.d/team-xbmc-ppa-natty.list
```back here if you want to do that.

Kind regards

---

