---
title: "Samba4 Domain Setup with two DCs"
date: 2015-10-19
forum: Installation &amp; Upgrades
---

### Post by Dave_Whapham on 2015-10-19
Hi all. I'm an old Microsoft guy who is fairly new to Samba4, and a Linux hack, so please forgive my newbness. 

After many failed attempts I've finally been able to setup a Samba4 domain controller and also join a second controller to the domain. Most things seem to be working ok and the DCs appear to be replicating. However, when I use Domain Users and Computers to try to connect to my second domain controller it tells me the controller is offline (but it still replicates). So my question is, should I be able to connect directly to it or is does Samba4 only support the management of a single DC? Thanks!

---

### Post by lingpanda on 2015-10-20
> **Dave_Whapham said:**
> Hi all. I'm an old Microsoft guy who is fairly new to Samba4, and a Linux hack, so please forgive my newbness. 

After many failed attempts I've finally been able to setup a Samba4 domain controller and also join a second controller to the domain. Most things seem to be working ok and the DCs appear to be replicating. However, when I use Domain Users and Computers to try to connect to my second domain controller it tells me the controller is offline (but it still replicates). So my question is, should I be able to connect directly to it or is does Samba4 only support the management of a single DC? Thanks!

You should be able to directly connect to any DC in your forest. How have you confirmed replication is working?

---

