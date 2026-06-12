---
title: "need help installing over network"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by bchan90 on 2008-02-27
i'm trying to install ubuntu to one of my laptops with a broken cd drive.
the tutorial for installing over the network requires a dhcp server, which i don't have.
can someone help me out?  thanks

p.s. i have one computer running 7.10 linux and another running windows vista, the target computer has windows xp (but it cant boot anymore cause of .dll corruptions)

---

### Post by dstew on 2008-02-27
If you have a Linux computer on your network, you can set it up to be a DHCP server. There is a synaptic package called dhcp3-server. What tutorial are you using? I have installed Ubuntu successfully on two headless servers using a PXE-BIOS based network install. Is that what you are trying to do? If your laptop has a functioning bootable USB port, the easiest way to network install is over the internet using [unetbootin]("http://lubi.sourceforge.net/unetbootin.html").

---

### Post by bchan90 on 2008-02-28
im using the [this]("http://help,ubuntu.com/community/Installation/Netboot") tutorial to try to install this.

hehe, i wish i knew about that unetboot before my windows xp stop booting on my laptop.

but i installed dhcp-3.0.6...but i dont really know how to set it up (<-- still linux nub).

---

### Post by dstew on 2008-02-28
See [this thread]("http://ubuntuforums.org/showthread.php?t=690483&highlight=powervault") about my experience. I used the same tutorial as you mention as a starting point, but I found it was not complete. (By the way, the link in your post is broken: you have a comma instead of a dot in the URL). Also, it didn't seem to make a difference to have the service set up in the etc/xinet.d/tftp file. I tried to make it as simple as possible. I took what I thought were the best ideas from the different tutorials I listed there, and it worked first time with no problems.

---

### Post by bchan90 on 2008-02-28
hey dstew, i checked out that forum and it looks like exactly what i need, i'll give it a try first thing tomorrow morning (i left my laptop at work hehe), i'll let u know how it goes after i give it a try

---

