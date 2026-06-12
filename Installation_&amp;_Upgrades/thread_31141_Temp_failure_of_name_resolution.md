---
title: "Temp failure of name resolution"
date: 2005-05-02
forum: Installation &amp; Upgrades
---

### Post by grover77 on 2005-05-02
I have Warty installed on a wireless desktop on a separate physical drive, dual boot - Ubuntu or XP Pro.
During Ubuntu boot, Network Configuration seems to take a long time, and then I get the error:
"Temp failure of name resolution   [FAIL]"
and it continues to boot. But I can get no network connection. Other things appear to operate normally.
Q1. What is the 'name' to which the error refers, and where do I edit it to correct it?

Q2. In the Computer\Networking section, what should the "Host" be? The name of the computer on which Ubuntu is installed, the name of the gateway computer on my Wireless LAN, or the wireless router/access point? Ubuntu recognizes the wireless card and the wireless network name and parameters.

When I do an IPConfig on both the wireless computer and the wired gateway, I get:
"Connection - specific DNS suffix = myhome.xxyyzz.com,"
which is the wireless accesspoint/router.

---

### Post by Xerampelinae on 2005-05-02
name resolution is referring to domain name resolution.  That is, turning some.url.org into an IP address.  You can check your /etc/resolv.conf file to make sure it has the correct name servers in it, and perhaps try to ping those name servers to see if they're reachable.

The hosts section is a GUI tool for editing /etc/hosts.  It is just a file with a little table, where you list an ip address followed by the hostname that should resolve to that ip.  There's a man page with more info... man hosts
 
Also, if the only problem with your network connection is dns, you should be able to go to  216.239.37.99 in a web browser and see google.

---

### Post by matthieufecteau on 2005-05-03
Maybe, I say, maybe, your problem is with the loopback interface.

Read the second post of this thread to look further : [http://www.ubuntuforums.org/showthread.php?t=29637&highlight=loopback](http://www.ubuntuforums.org/showthread.php?t=29637&highlight=loopback)

---

