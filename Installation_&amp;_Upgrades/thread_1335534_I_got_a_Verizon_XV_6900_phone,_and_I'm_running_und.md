---
title: "I got a Verizon XV 6900 phone, and I'm running under Linux Ubuntu 9.04. Help please?"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by pango-a-go-go on 2009-11-23
I wanted to install the software but I have no idea how to go about it. I have Sun Virtualbox for XP, as well as WINE.

Any help??

Tell me what specs or whatever you'll need. I'm a noob at Linux and while I can do some things, installing windows-based things from CD are confusing and difficult for me.


Thank you!!!

---

### Post by lemming465 on 2009-11-24
Given that the XV6900 is a windows mobile device, and their *VZW Access Manager* is a windows app, trying to tether Linux to the phone is looking hard.  I don't know if you can get WINE to share a USB connection with a host Linux well enough to send IP packets from Linux out the phone.  This is a case where using windows as the host OS and running Linux as a guest OS would actually be easier.

---

### Post by raymondh on 2009-11-24
Would virtualization (linux as host, windows as guest) work in this case?

---

### Post by lemming465 on 2009-11-24
Maybe.  The issues I forsee with a Linux host are:
1) the proprietary windows client access software probably doesn't run under WINE
2) if a windows virtual guest sets up a tunneled network connection to a USB device, the host linux system probably has no way to to hook into it

If insane luck obtains, the EVDO tether would accept plain IP packets after it had authenticated, and talk some USB wire protocol that Linux supports, so that you just have to configure the Linux ip stuff to match whatever windows got.

The converse setup, where windows is the host OS and Linux the guest, doesn't have any of those problems.  Linux could just use whatever NAT or bridge networking was appropriate to its guest situation, and let windows run the proprietary network code.

I usually prefer to have windows guests on linux hosts, because I get better stability, disk performance, and CPU scheduling from the linux hosts.  But in this situation I'd go the other way.

---

### Post by raymondh on 2009-11-25
> **lemming465 said:**
>  let windows run the proprietary network code.


Thanks 'lemming.  This is good learning :)

---

