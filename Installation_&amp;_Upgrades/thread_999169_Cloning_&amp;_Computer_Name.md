---
title: "Cloning &amp; Computer Name"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by DIGGER_NZ on 2008-12-01
Hi There,

We are looking at deploying Edubuntu onto laptops for our school clients. I will be using an imaging method to push one generic image out to many units (all the same). I have limited experience with Linux, but how do computer names work? With Windows you need to regenerate the SID otherwise you encounter issues when you go to connect the machines to a network. Is this the same in Linux and is there a tool/way to get around this?

Thanks

---

### Post by lemming465 on 2008-12-02
> I will be using an imaging method to push one generic image out to many units 
An option you should look into is PXE-based network boots, assuming your ethernet chips support that and your network is fast enough.  You may have options even easier than disk cloning.

> how do computer names work
On Ubuntu it's controlled by /etc/hostname, which is typically set during the initial system install.
> With Windows you need to regenerate the SID
No SIDs in Linux; this won't be an issue.  In an environment with DHCP the hostname can either be controlled by the client or by the DHCP + DNS infrastructure, depending on how you want to set it up.

---

