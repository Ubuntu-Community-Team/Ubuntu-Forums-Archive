---
title: "Can't reinstall common files -- URGENT help please"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by galfly on 2010-08-10
Hi everyone,

I ran this line: aptitude purge x11-common and all common files,  all the tools I need are gone from my desktop. I have an amd64 with ubuntu +gnome on it.

Is there a way to reverse this --other than installing 1gb of packages one by one? 

An urgent help is greatly appreciated .

maya--

---

### Post by snowpine on 2010-08-10
Hi Maya,

```
sudo aptitude install ubuntu-desktop
```

...would be my suggestion. This will get you back to the default install's set of packages.

---

### Post by galfly on 2010-08-10
Thanks a bunch!

I ran it and it installed some of the tools I needed.

Here's what I don't understand though: when I first purged all the stuff it said about 1.3gb of disk space would be removed. When I reinstall it says 800mb is needed. What happened to the other .5gb? 

Say it goes back to default and the rest is the stuff i installed myself.

But why would purge remove things that don't come with x11-common package at the first place?

maya-- still experimenting and crashing systems to figure things out

---

### Post by snowpine on 2010-08-10
ubuntu-desktop is a "metapackage" that depends on xorg.
xorg depends on x11-common.

So removing x11-common removes ubuntu-desktop and everything that comes with it.

[http://packages.ubuntu.com/lucid/ubuntu-desktop](http://packages.ubuntu.com/lucid/ubuntu-desktop)

---

