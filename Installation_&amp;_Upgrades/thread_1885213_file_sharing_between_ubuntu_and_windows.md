---
title: "file sharing between ubuntu and windows"
date: 2011-11-22
forum: Installation &amp; Upgrades
---

### Post by sudodus on 2011-11-22
Hi everybody,

I'm running desktop Ubuntu and would like to share files between ubuntu and windows in a LAN at home. At work I heard about samba and ssh. Is there a better alternative?

What should I select and why? Which is easier to run, and which is more secure? Ssh means secure shell, but maybe samba can be configured to be secure too.

What software should I install?

---

### Post by darkod on 2011-11-22
1. In a home LAN you don't need to worry that much about security.

2. SSH is a secured shell all right but mostly used to log into a server that sits in a corner somewhere in your house, without monitor, keyboard, etc.

3. Samba is the common link for sharing between windows and linux in a home LAN. Setting up the shares is real easy, and it all depends whether you want it to be open for all, or some folders will be only for particular users, etc. The more special stuff you want, the more complicated the configuration is.

Creating shares open to all is a peace of cake.

---

### Post by collisionystm on 2011-11-22
Just right click on your folder and hit share.
Nautilus has a sharing feature built in and will take care of it for you.
Like darkod mentioned, you can configure samba to be as complex as you want. It is just the compatibility layer that allows communication between *nix and windows.

If you want to try SSH... i suggest a program like WinSCP to connect to your linux box from the windows machine.

---

### Post by sudodus on 2011-11-22
Thanks darkod and collisionystm

I understand that samba is simpler if I make it an open system. I am behind a router with a nat firewall. So I can use Nautilus file browser to configure it just like that :P

I will come back and tell how it works for me (maybe not tonight)

---

### Post by collisionystm on 2011-11-22
> **sudodus said:**
> Thanks darkod and collisionystm

I understand that samba is simpler if I make it an open system. I am behind a router with a nat firewall. So I can use Nautilus file browser to configure it just like that :P

I will come back and tell how it works for me (maybe not tonight)


Look in the software center for samba. I am sure you can find some programs in there that will help you with it, if you decide to go that route!

---

### Post by sudodus on 2011-11-23
Samba works :D

---

