---
title: "removed network manager"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by vdtdriver on 2008-07-16
Oops

Anyway, now I can't use the network.  And apt-get seems to
not function well without a network connection.

I tried modifying the standard 
/etc/network/interfaces file to say that eth0 can use
dhcp but when I enable it there is no DHCP response.
(another ubuntu machine I have has a DHCP IP address so
I know there is a server on the network).

I've tried downloading the wpasupplicant package (networkmanager
depends on it) and installing from a flash drive.
gdebi says "Dependency is not satisfiable: libc6).  When
I used Synaptic Package Manager it says libc6 is installed.  I 
suspect that someone can't find libc6 status over the network.
I tried modifying /etc/apt/sources.list to include the
line:
deb file://localhost/media/disk-1 gusty main restricted
.  This is where I have the wpasupplicant package.  Doesn't
seem to find it.

So I am looking for ideas.  Thanks

---

### Post by mikewhatever on 2008-07-16
How did you remove it? Have you uninstalled by 'accidentally' typing <sudo apt-get remove network-manager-gnome>, or have you just removed the icon from the panel?
I assume that the latter is the case, since the former seems unlikely. If so, alt+f2 and nm-applet should bring the icon back.

---

### Post by vdtdriver on 2008-07-16
I am cramped for space so I removed it with apt-get with thinking it through

---

### Post by Joshuwa on 2008-07-16
You've completed step 1 towards replacing it with Wicd, in my opinion :)

Whether you choose Wicd or network manager, you ought to be able to download a .deb of either since you're using the new now, and install it on Ubuntu later on.

---

### Post by mikewhatever on 2008-07-16
> **vdtdriver said:**
> I am cramped for space so I removed it with apt-get with thinking it through

You should be able to reinstall it from your installation CD. Just make sure you have the CD added to repositories and reload the list.

---

### Post by vdtdriver on 2008-07-16
> **mikewhatever said:**
> You should be able to reinstall it from your installation CD. Just make sure you have the CD added to repositories and reload the list.

wpasuplicant is not no the Live CD for what ever reason and as I stated above when I tried to install from a flash driver I got the message about libc6 missing when in fact it is installed.

---

### Post by vdtdriver on 2008-07-16
If I moved lib6c.deb (of course it is a longer name) to 
/var/cache/apt/archives would that help?  Have to hold off on testing
that for a while because of other tasks.

---

### Post by vdtdriver on 2008-07-16
> **vdtdriver said:**
> If I moved lib6c.deb (of course it is a longer name) to 
/var/cache/apt/archives would that help?  Have to hold off on testing
that for a while because of other tasks.

No, that didn't help.

Also got around to reading the man page for sources.list and
tried to follow the syntax, but somehow I am not getting it
right.

deb file:/home/dave/archive gutsy main restricted universe

---

### Post by alphaniner on 2008-07-16
One of the first things I do when installing a new system is remove the network manager.  For DHCP, entry in /etc/network/interfaces should be

```
auto eth0
iface eth0 inet dhcp
```

then I do a network restart with

```
/etc/init.d/networking restart
```

---

### Post by vdtdriver on 2008-07-16
> **alphaniner said:**
> One of the first things I do when installing a new system is remove the network manager.  For DHCP, entry in /etc/network/interfaces should be

```
auto eth0
iface eth0 inet dhcp
```

then I do a network restart with

```
/etc/init.d/networking restart
```

Thanks for the reply.

I tried part of the same (no auto, used ifup/ifdown).  Get
DHCPDISCOVER...
No DHCPOFFERS received.

---

