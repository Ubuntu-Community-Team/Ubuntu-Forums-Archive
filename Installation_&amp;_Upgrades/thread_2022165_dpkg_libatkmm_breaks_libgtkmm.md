---
title: "dpkg: libatkmm breaks libgtkmm"
date: 2012-07-10
forum: Installation &amp; Upgrades
---

### Post by evolutionator on 2012-07-10
I've got a problem about installing libgtkmm-2.4-1c2a, this seems to be the thread more similar to what I'm trying to achieve.

On a vmware 8 machine (running on seven) I've just installed a copy of Xubuntu 12.04 32 bit, I'm trying to get [seq24]("http://seq24.wikispaces.com/") to work.
The pc (and so the vm) is not connected to internet, never has been, and never will be. This means, in my knowledge, that I had to discard the ubuntu software center and apt-get, and tried to install it with dpkg.

Doing a "./configure" on seq24 it tells me it needs libgktmm-2.4, so I downloaded [libgtkmm-2.4-1c2a]("http://packages.ubuntu.com/lucid/libgtkmm-2.4-1c2a") and executed a "sudo dpkg -i blablabla" to install it. It stops with the following line:
```
libatkmm-1.6-1 (2.22.6-1ubuntu1) breaks libgtkmm-2.4-1c2a (<< 1:2.22.0) and is installed.

```

I tried adding --force-all in dpkg to finish the installation, but the package remains in 'broken' status (no surprise, I suppose) and it doesn't get acknowledged by seq24's "./configure", so I removed it with "sudo apt-get install -f".
I tried using the libgtkmm package with gdebi-gtk (had to install it), but it doesn't work, it remains 'broken' again.

I checked (manually) for all the dependencies of libgtkmm-2.4-1c2a, all the needed packages seems to be installed (I checked searching them with synaptics). I found another user that had a similar problem, but from what I know it wasn't the same. Is there something I could do? What does that error means?

Thanks for the help.

PS one of the websites about seq24 suggested using "autoreconf" as the first passage before installing seq24: should I do it?

---

### Post by evolutionator on 2012-07-12
Is there a repository or something for old versions of the packages? Maybe with a previous libgtkmm the problem would go away...

---

### Post by dino99 on 2012-07-12
launchpad source is a possible way to get these packages

for example:

[https://launchpad.net/ubuntu/lucid/+package/libgtkmm-2.4-dev](https://launchpad.net/ubuntu/lucid/+package/libgtkmm-2.4-dev)

[https://launchpad.net/ubuntu/+source/atkmm1.6](https://launchpad.net/ubuntu/+source/atkmm1.6)

---

### Post by evolutionator on 2012-07-23
> **dino99 said:**
> launchpad source is a possible way to get these packages

for example:

[https://launchpad.net/ubuntu/lucid/+package/libgtkmm-2.4-dev](https://launchpad.net/ubuntu/lucid/+package/libgtkmm-2.4-dev)

[https://launchpad.net/ubuntu/+source/atkmm1.6](https://launchpad.net/ubuntu/+source/atkmm1.6)
Thanks, I will try them. I hope one of those at least will change something.
I admit I thought there was more compatibility between versions and distros of linux.

---

