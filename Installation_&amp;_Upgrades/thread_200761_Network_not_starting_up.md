---
title: "Network not starting up"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by s1gnAl on 2006-06-20
Just did a new 6.06 server only install and my adapter was previously starting on it's own at boot time when I had it assigned using DHCP. 

Following the intstructions here [https://help.ubuntu.com/ubuntu/serverguide/C/network-configuration.html](https://help.ubuntu.com/ubuntu/serverguide/C/network-configuration.html) I set my adapter to a static IP and also installed SSHD.

Now whenever I reboot, my adapter doesn't come up on it's own and I have to issue sudo ifup eth0 from the CLI to get it going. 

I see this in /etc/rc0.d(which Im assuming is the default runlevel at boottime?):

```
lrwxrwxrwx  1 root root   20 2006-06-19 17:09 S35networking -> ../init.d/networking
```

Yet, the only interface that comes up is lo.  ](*,)

---

### Post by s1gnAl on 2006-06-21
Bump, 21 views and no one knows!!??? Throw me a bone if you can :D

---

### Post by ape on 2006-06-21
Can you post your /etc/network/interfaces file by any chance?

---

### Post by s1gnAl on 2006-06-21
Sure thing:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface eth0 inet static
        address 192.168.1.50
        netmask 255.255.255.0
        gateway 192.168.1.1

```

---

### Post by ape on 2006-06-22
You need to modify the following line in your /etc/network/interfaces file:


   **auto lo**

to read

   **auto lo eth0**


This will cause the interface to be activated automatically on bootup.

---

