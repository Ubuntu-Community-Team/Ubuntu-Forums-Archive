---
title: "Help setting up network ISA card 3Com"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by mig_l on 2007-02-17
Hi,

I'm having some problems with my network ISA card 3Com (3c509TP Etherlink III) it's not detected by ubuntu 6.10 and i don't no what to do...

I found a way to solve it in the comunity support
[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards3Com](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards3Com)

it says to: 

> Add 3c509 to /etc/modules & edit /etc/network/interfaces.

but i don't no how to do this???:( 

Thanks in advance! 
(and sorry for my bad english... )

---

### Post by alyoung on 2007-02-17
Right. Open up a terminal. Give the command:

```
sudo nano /etc/modules
```

Add this:

```
alias eth0 3c501
```

Save it.

Then:

```
sudo nano /etc/network/interfaces
```

Add:

```
iface eth0 inet dhcp

```

Save it.

Reboot. It should now work!

---

### Post by mig_l on 2007-02-19
Thanks for the tip alyoung!

I cheked in the Windows XP devices and i found that the module is 3c509 instead of 3c501
so i did:

```
sudo nano /etc/modules
```
and added this
```

3c509
alias eth0 3c509

```
and save it!

there was no need to edit /etc/network/interfaces since the file already ad the line
```
iface eth0 inet dhcp
```

reboot and is working fine!
Thank you!
(and sorry again for my english, sou Português!) :)

---

### Post by alyoung on 2007-02-19
It's fine; good to see I helped.

---

### Post by tiver on 2007-05-15
I have the same card and I did the steps described here. I now have Ubuntu 7. On my old Windows the card ran in legacy mode. Is it possible that that is the reason why it does not work yet?

---

