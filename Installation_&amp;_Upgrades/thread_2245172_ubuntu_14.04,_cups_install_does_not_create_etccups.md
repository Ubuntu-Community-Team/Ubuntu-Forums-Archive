---
title: "ubuntu 14.04, cups install does not create etc/cups/cupsd.conf?"
date: 2014-09-21
forum: Installation &amp; Upgrades
---

### Post by giggler2 on 2014-09-21
Hi,

Following for install:

[https://help.ubuntu.com/10.04/serverguide/cups.html](https://help.ubuntu.com/10.04/serverguide/cups.html)

I'm using 14.04 trusty.  Actually tried package install combinations like:

apt-get install cups-pdf splix printer-driver-splix printer-driver-gutenprint cups-client cups-common cups-ppdc cups-bsd cups

After install:

ls /etc/cups
interfaces  ppd  raw.convs  raw.types

Where's my cupsd.conf?  where's my cups-files.conf?

Can't start cups, no configure file?

Which aptitude package should I install to get the config files?

Regards,

dc

---

### Post by ian-weisser on 2014-09-24
Let's ask dpkg that question:

```
~$ dpkg -S /etc/cups/cups-files.conf 
cups-daemon: /etc/cups/cups-files.conf
```

/etc/cups/cups-files.conf is provided by the cups-daemon package.

Now let's see which packages will automatically install the cups-deamon package, so you don't need to specify it.

```
$ apt-cache rdepends cups-daemon
cups-daemon
Reverse Depends:
  cups-browsed
  cups-dbg
  cups-core-drivers
  cups-browsed
  cups
  cups-dbg
  cups-core-drivers
  cups-browsed
  cups
```

So installing the normal 'cups' package will do what you seem to want.

---

