---
title: "New Ubuntu Server 18.04.2 LTS install - unable to connect to network"
date: 2019-07-21
forum: Installation &amp; Upgrades
---

### Post by frankhovin on 2019-07-21
I'm trying to install a new Ubuntu Server 18.04.2 LTS system, but already at the network connection I'm having problems.

My network router has a pretty standard, no extra security, DHCP server. Other clients connect to it regularly, by wlan and wired.

My computer is a Dell Optiplex 160 with a wired network card. It seems completely unable to connect to my LAN.

When I get to the Install Ubuntu part of the installation, after specifying language and keyboard, I make sure that the IPv4 setting is set to automatic/DHCP. But the listing of the network interface says "no address was supplied", and when I click on the "Don" link and try to continue, it fails after several minutes with a timeout configuring the network.

Just for fun, I tried creating a bond, with the one network card. Then I went to the network interface and set it back from "disabled" to "enabled". Then when I selected "Done", it finished and went through the rest of the installation. However, even though the system was issued an IP address as per the DHCP setup, it was unable even ping the gateway of the LAN, and no other clients on the land could ping it. So, that obviously didn't work.

So I went back and restarted it, but still got the timeout every time. Also, when attempting the "bond thing" again, this time it didn't work.

So, the installation part is completely unable to get an IP and configuration from the DHCP server. Where do I go from here? I'm about to try anyther Linux distro, but I really wanted Ubuntu.

---

### Post by uRock on 2019-07-21
Have you tried powering the router down or clearing the dhcp cache, it you have that ability.

---

### Post by frankhovin on 2019-07-22
Yup - restarted it. Also, that's a bit far-fetched since there are no settings that should cause this.

---

### Post by frankhovin on 2019-07-22
I've been searching a bit, and it seems that this is a fairly common problem, with no solutions or help from Ubuntu itself. As with most other non-vanilla Ubuntu problems in my experience, there are lots of threads asking for help and no answers. So moving away from Ubuntu seems a good choice. This thread can be closed or deleted.

---

### Post by Morbius1 on 2019-07-22
Since you have had basic networking problems [for 11 years now]("https://ubuntuforums.org/showthread.php?t=835589&p=5227765#post5227765") it's probably time you moved on.

---

### Post by uRock on 2019-07-22
> **frankhovin said:**
> Yup - restarted it. Also, that's a bit far-fetched since there are no settings that should cause this.

Really? I've watched in wireshark and have seen the packets the router sends when attempting to reconnect. The DHCP reply is different when the MAC address is already in MAC address table on some routers. I had the same problem when I installed Debian on my production machine a few days ago.

---

### Post by rsteinmetz70112 on 2019-07-24
If you boot to a live session does the network work?

---

### Post by gevensen on 2019-07-24
> **frankhovin said:**
> I've been searching a bit, and it seems that this is a fairly common problem, with no solutions or help from Ubuntu itself. As with most other non-vanilla Ubuntu problems in my experience, there are lots of threads asking for help and no answers. So moving away from Ubuntu seems a good choice. This thread can be closed or deleted.
I just had the same problem I rebooted the router cleared the cache ect so i had an older copy of LTS.1 and used that and like MAGIC it worked...
It was nothing to do with your abilities the installer must be screwed up

---

