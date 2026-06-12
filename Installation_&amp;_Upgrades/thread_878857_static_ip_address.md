---
title: "static ip address"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by sawatdee on 2008-08-03
I installed the desktop version of ubuntu, but I also need to use the system as a local web server, name server, etc. The desktop installation never asked for an ip address; it just assumed I wanted DHCP. I've been reading man pages and documentation, but I am very new to ubuntu coming from Fedora and still have no idea how to change it to use a static ip address on my local network. Someone must know how to do this....

---

### Post by robotman5 on 2008-08-03
you should have downloaded the Server Edition if u were doing a Server:guitar:

---

### Post by sawatdee on 2008-08-03
I use the system as a desktop system and development system with test servers for the local network only. I was told that it would be easier to install the desktop and add the server packages, rather than the other way around. There is no installation that offers both.

---

### Post by robotman5 on 2008-08-03
hmmm wait till the Experts come to help you i am new to Linux ..

---

### Post by sawatdee on 2008-08-03
For anyone else wanting to set up a static ip address after doing a desktop installation, I found this which seems to have worked.
[http://codesnippets.joyent.com/posts/show/319]("http://codesnippets.joyent.com/posts/show/319")

If you want to change your host name and identify it with your static ip address, you can edit /etc/hosts.
```
man hosts
```

To test your configuration, the following commands are helpful:
ifconfig
ping

If you set up a local name server, these commands will help with testing:
dig
host

---

