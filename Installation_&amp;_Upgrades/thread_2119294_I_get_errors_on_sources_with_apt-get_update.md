---
title: "I get errors on sources with apt-get update"
date: 2013-02-23
forum: Installation &amp; Upgrades
---

### Post by daaxwizeman on 2013-02-23
Hi,

I don't know why, but I got these erreors on sources when I updated them : 

```
Err http://ppa.launchpad.net precise/main Sources
  404  Not Found
Err http://ppa.launchpad.net precise/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages
  404  Not Found

```

What happened ? I didn't do any modifications to sources.list.

Thans in advance.

---

### Post by QIII on 2013-02-23
Unless I'm missing it, I don't see "Precise" in the index for [http://ppa.launchpad.net/](http://ppa.launchpad.net/) right now.

Might be taken down for updates or removed.  Give it a few hours and see what's up later.

---

### Post by sudo san on 2013-02-23
Did you upgrade recently?
If you did, what was it from and to?

---

### Post by daaxwizeman on 2013-02-23
Nope, no upgrade recently.

I didn't see precise in the index too, this is weird no ?

So I'll wait and see.

---

### Post by sudo san on 2013-02-24
If you want to, you could temporarily disable these repositories so you can update the other parts of your system. You can do that by using this command:
```
sudo nano /etc/apt/sources.list
```

When the editor opens, place a '#' in front of the repositories that won't download.
Hope it helps.

---

### Post by matt_symes on 2013-02-24
Hi

As they are ppa's you may also find the in the directory

```
/etc/apt/sources.list.d/
```

Kind regards

---

