---
title: "ssh failing to start"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by daihard on 2007-05-12
Hi.

This is my first post to this forum. I have installed Ubuntu for the first time. (I've been using Red Hat and Fedora Core.) What comes naturally to me over in the RH world isn't all that obvious with Ubuntu. I'm hoping the hurdle isn't too high.

Now, the problem I need your help with is how to configure SSH. I have managed to install it by running the following command:
```
$ sudo apt-get install ssh
```
Then without knowing any GUI way of doing it, I attempted to start the service by typing the following command:
```
$ sudo /etc/init.d/ssh start
```
... which gave me this error:
```
 * Starting OpenBSD Secure Shell server...                               [fail]
```
Do I need to do anything other than intalling the necessary packages in order to start ssh? If it matters, I am using DHCP to connect to an in-house router. LAN and WAN both work.

Thanks!
Dai

---

