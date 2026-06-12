---
title: "live-build ?"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by cccc on 2011-05-08
hi

I've installed **live-build** package using synaptic on maverick and I 'd like to create my own live usb-hdd according to:

[http://omnsproject.org/?p=831](http://omnsproject.org/?p=831)

but lb commands like "lb config" or "lb build" etc. don't work!```

# lb clean
lb: command not found

```

Even man page for live-build doesn't work:```

# man live-build
No manual entry for live-build
```

What's wrong and howto solve this problem?

---

### Post by wojox on 2011-05-08
Try running:

```
sudo updatedb
```

Or reboot and see what happens.

---

### Post by cccc on 2011-05-08
> **wojox said:**
> Try running:

```
sudo updatedb
```

Or reboot and see what happens.

I've tried and still doesn't work.

---

### Post by wojox on 2011-05-09
> **cccc said:**
> I've tried and still doesn't work.

Maybe the [Live-Build PPA]("https://launchpad.net/ubuntu/+source/live-build") will work better.

---

### Post by cccc on 2011-05-09
Thx, I've tried to install live-build_2.0.12-2_all.deb, but get the following error:

---

### Post by wojox on 2011-05-09
Download this [live-build]("http://np.archive.ubuntu.com/ubuntu/pool/universe/l/live-build/live-build_3.0~a16-1_all.deb") and open your termnal and go into the directory it's in and run 

```
sudo dpkg -i live-build_*
```

---

### Post by cccc on 2011-05-09
Thx a lot, I've installed and now "man live-build" and "lb config" works well!

---

### Post by cccc on 2011-05-10
I try to build now live usb-hdd and get the following problem:```

# lb build
...................................................................
...................................................................
...................................................................
Removing 'local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
update-initramfs: deferring update (trigger activated)
Setting up libplymouth2 (0.8.2-2ubuntu5.1) ...
Setting up plymouth (0.8.2-2ubuntu5.1) ...
update-initramfs: deferring update (trigger activated)
Setting up sudo (1.7.2p7-1ubuntu2.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
P: Begin executing preseed...
P: Begin executing local preseeds...
P: Begin queueing installation of package lists...
P: Begin queueing installation of local package lists...
P: Begin queueing installation of packages...
P: Begin queueing installation of local packages...
P: Begin installing packages...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B][COLOR="Red"]E: Unable to locate package live-config
E: Unable to locate package live-config[/COLOR][/B]
P: Begin unmounting filesystems...
```

So I've installed: 

**live-config_3.0~a18-1_all.deb** 

and 

**live-config-systemd_3.0~a18-1_all.deb**

from:

[http://np.archive.ubuntu.com/ubuntu/pool/universe/l/live-config/](http://np.archive.ubuntu.com/ubuntu/pool/universe/l/live-config/)

```
# dpkg -l | grep live
ii  live-build                           3.0~a16-1                                         Debian Live - System Build Scripts
ii  live-config                          3.0~a18-1                                         Debian Live - System Configuration Scripts
ii  live-config-systemd                  3.0~a18-1                                         Debian Live - System Configuration Scripts (systemd backend)

``` but it doesn't help and still get the same problem.
Howto solve this?

---

