---
title: "Install takes forever without internet connection"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by OneSeventeen on 2008-10-13
I am installing Ubuntu-server 8.04 amd64 without an internet connection.  I have to manually set the IP to give it one that can access the internet.

Configuring apt and installing certain apps takes forever because it doesn't appear to time out when attempting to get online.  It looks like it keeps trying for about 20 minutes.

I was just wondering if there is a command I could pass it at startup to tell it either to use a specific IP or to skip steps requiring the internet.

**EDIT:** Could have sworn I chose ubuntu not kubuntu... weird... sorry about that.

---

### Post by cariboo on 2008-10-13
You could set a static ip address assuming you didn't install a gui, at the prompt type:

```
sudo nano /etc/network/interfaces
```

Edit the file so that it looks like this:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address	192.168.1.200
netmask	255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

You will of course have to substitute your own ip and gateway addresses.

Jim

---

