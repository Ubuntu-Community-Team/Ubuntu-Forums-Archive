---
title: "Can't detect network adapter in Hyper-V"
date: 2010-04-20
forum: Installation &amp; Upgrades
---

### Post by smay84 on 2010-04-20
Hi

I'm trying to setup a virtual machine running Ubuntu server 9.10 in Hyper-V on a windows 2008 server.

However it can't detect the network adapter (Virtual NIC uses Broadcom NetXtreme Gigabit Ethernet).

After doing some research on a Windows forum i was told to try using the legacy network interface.  Annoyingly 64bit edition doesn't seem to have this.

Anyone know how i can get around this?

Simon

---

### Post by smay84 on 2010-04-20
nevermind turns out you can create a legacy network interface in 64 bit afterall.

---

### Post by pin2d2 on 2010-07-19
You can't in windows 2003 server 64, it's possible to do it in 2008
[http://technet.microsoft.com/en-us/library/cc732470%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/cc732470%28WS.10%29.aspx)

---

