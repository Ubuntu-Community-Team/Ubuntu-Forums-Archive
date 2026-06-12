---
title: "Ubuntu Studio 11.10 Broken Network"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by Regele IONESCU on 2011-10-19
Hi!
I downloaded Ubuntu Studio 11.10 64 bit ISO image from:

[http://cdimage.ubuntu.com/ubuntustudio/releases/11.10/release/]("http://cdimage.ubuntu.com/ubuntustudio/releases/11.10/release/")

the exact ISO file is:

[http://cdimage.ubuntu.com/ubuntustudio/releases/11.10/release/ubuntustudio-11.10-alternate-amd64.iso]("http://cdimage.ubuntu.com/ubuntustudio/releases/11.10/release/ubuntustudio-11.10-alternate-amd64.iso")

I setup network during install, TCP/IP v4 with fix IP, gateway, DNS etc. During install I had no problems, it even downloaded certain files. After reboot I found that I have installed Ubuntu Studio Xfc and have no network access. I opened the network manager and manually setup the network again but it was useless. 

**How could I find what is wrong with my network and sort it ou? **Thanks in advance!

---

### Post by Regele IONESCU on 2011-10-19
I reinstalled the system and noticed that immediately after install the network works fine but as soons as I update Ubuntu it gets broken. So, one of the updates is broking the network.

---

### Post by Regele IONESCU on 2011-10-19
The problem is that system restart deletes resolv.conf 

Here is the solution I found on the net to prevent the system delete resolv.conf:
```
# chattr +i /etc/resolv.conf
```

---

