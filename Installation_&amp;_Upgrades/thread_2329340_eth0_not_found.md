---
title: "eth0 not found"
date: 2016-06-30
forum: Installation &amp; Upgrades
---

### Post by S.User on 2016-06-30
Hello,

I've just installed Lubuntu 16.04.
So far so good but eth0 is not found.

```
lsmod
``` lists ... nothing.
correspondingly /etc/modules is also empty.

consequently ```
ifconfig eth0
``` won't work either.

I booted in recovery mode, enabled the network there and then continued with normal boot.
But that didn't help either.

On top of it it also won't find the USB mouse but I haven't gone into this one yet. I'm suspecting a similar issue though.

Does this sound familiar to anyone perhaps?

Stephan

---

### Post by kansasnoob on 2016-06-30
It's systemd/udev mumbo-jumbo. Basically eth0 has been replaced with [Predictable Network Interface Names]("https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/"). It all makes little sense to me other than being a pain in the nether regions but you can find info googling systemd/udev eth0 ubuntu:

[https://www.google.com/?client=ubuntu#channel=fs&q=systemd%2Fudev+eth0+ubuntu](https://www.google.com/?client=ubuntu#channel=fs&q=systemd%2Fudev+eth0+ubuntu)

I've managed to stumble through things a couple of times and got things working but I couldn't explain it if my life depended on it :(

---

### Post by grahammechanical on 2016-06-30
Three new commands to get used to using.

```
 nmcli general status
```

> graham@sda8-Lub1604:~$ nmcli general status
STATE      CONNECTIVITY  WIFI-HW  WIFI     WWAN-HW  WWAN    
connected  full          enabled  enabled  enabled  enabled 

```
nmcli connection
```

> graham@sda8-Lub1604:~$ nmcli connection
NAME                UUID                                  TYPE            DEVICE 
Wired connection 2  6eef5b8e-55a2-459a-bd6e-9dcf8c8cd3db  802-3-ethernet  enp2s0 
Wired connection 1  d6d5e52b-6096-4eda-a4ca-a75b2646b917  802-3-ethernet  --  

```
nmcli device
```

> graham@sda8-Lub1604:~$ nmcli device
DEVICE           TYPE      STATE         CONNECTION         
enp2s0           ethernet  connected     Wired connection 2 
wlx0015af0e9be0  wifi      disconnected  --                 
enp6s4           ethernet  unavailable   --                 
lo               loopback  unmanaged     --    

They work on Lubuntu 1604 as well as Ubuntu 16.04. If anyone is not happy with this then complain to RedHat for it is their employees that have pushed systemd in Linux and they think all this is logical

> Two character prefixes based on the type of interface:
 *   en -- ethernet
 *   sl -- serial line IP (slip)
 *   wl -- wlan
 *   ww -- wwan
 *
 * Type of names:
 *   b<number>                             -- BCMA bus core number
 *   ccw<name>                             -- CCW bus group name
 *   o<index>[d<dev_port>]                 -- on-board device index number
 *   s<slot>[f<function>][d<dev_port>]     -- hotplug slot index number
 *   x<MAC>                                -- MAC address
 *   [P<domain>]p<bus>s<slot>[f<function>][d<dev_port>]
 *                                         -- PCI geographical location
 *   [P<domain>]p<bus>s<slot>[f<function>][u<port>][..][c<config>][i<interface>]
 *                                         -- USB port number chain

[https://cgit.freedesktop.org/systemd/systemd/tree/src/udev/udev-builtin-net_id.c#n20](https://cgit.freedesktop.org/systemd/systemd/tree/src/udev/udev-builtin-net_id.c#n20)

[https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)

Regards.

---

### Post by kansasnoob on 2016-06-30
> If anyone is not happy with this then complain to RedHat for it is their employees that have pushed systemd in Linux and they think all this is logical

True, but Debian could have chosen to remain systemd free but chose otherwise. The decision was contentious enough that a few Debian devs jumped ship and created Devuan. At any rate that part of the conversation belongs in Linux and OS Chat.

---

### Post by S.User on 2016-06-30
I found the solution.

Was easier than expected:

Booting with Kernel 4.4.0-21: no mouse, no eth0

Booting w. Kernel 3.13.0-91: Everything works.

Just need to get rid of the newer Kernel and make sure it won't come back with the next upgrade.

Shouldn't newer/updated software be an improvement instead of a step back?


Stephan

---

### Post by kansasnoob on 2016-07-01
From a security standpoint I don't think it's wise to use an outdated kernel that will not receive automatic security updates.

---

### Post by S.User on 2016-07-01
> **kansasnoob said:**
> From a security standpoint I don't think it's wise to use an outdated kernel that will not receive automatic security updates.

Well true but what then?
There is clearly a fault with the newest kernel. It's unusable.
I'd have a secure machine without network and mouse...

St

---

### Post by kansasnoob on 2016-07-01
> **S.User said:**
> Well true but what then?
There is clearly a fault with the newest kernel. It's unusable.
I'd have a secure machine without network and mouse...

St

I'd begin by booting the older kernel and running:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

That should update you to linux kernel 4.4.0-28 which may or may not be helpful.

---

### Post by kansasnoob on 2016-07-01
I'm just curious, how did you install kernel 3.13.0-91? Was this an upgrade from Trusty to Xenial? Or a fresh install as indicated in your original post?

---

### Post by S.User on 2016-07-02
> **kansasnoob said:**
> I'd begin by booting the older kernel and running:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

That should update you to linux kernel 4.4.0-28 which may or may not be helpful.


Nope, it returned that everything is up to date.

> **kansasnoob said:**
> I'm just curious, how did you install kernel 3.13.0-91? Was this an upgrade from Trusty to Xenial? Or a fresh install as indicated in your original post?

Yes this was a new install.

I actually opened another thread on the kernel issue, just in case moderators might complain as I marked this one as solved already.

[http://ubuntuforums.org/showthread.php?t=2329403](http://ubuntuforums.org/showthread.php?t=2329403)

---

### Post by S.User on 2016-07-02
Now this has found a solution to the kernel problem as well: [http://ubuntuforums.org/showthread.php?t=2329403&p=13512266#post13512266](http://ubuntuforums.org/showthread.php?t=2329403&p=13512266#post13512266)

Something to be aware of: newer kernels sometimes don't seem to come though update/upgrade commands.

Stephan

---

