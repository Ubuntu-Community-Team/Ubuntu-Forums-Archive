---
title: "OpenStack with conjure-up (Landscape is missing)"
date: 2017-10-30
forum: Installation &amp; Upgrades
---

### Post by e.ms on 2017-10-30
Hello everybody,

I'm trying to install OpenStack on Ubuntu 16.04.3.
[https://www.ubuntu.com/download/cloud/build-openstack](https://www.ubuntu.com/download/cloud/build-openstack)


[LIST]
[*]sudo apt update OK
[*]sudo apt install maas OK
[*]Login to the MAAS UI at http://<maas.ip>/MAAS/ OK
[*]imported your SSH key OK
[*]check Gateway & DNS OK
[*]config DHCP OK
[*]Images Synced OK
[*]start first Node & Commisioning OK
[*]Node ist ready OK
[*]sudo snap install conjure-up --classic OK
[/LIST]

Now the big problem! If I run "conjure-up" last but not least "Landscape" should be available. But Landscape is not displayed!
The same problem with Ubuntu 17.10.

Can someone help me?

---

### Post by muthu883 on 2017-10-31
I am also facing the same problem 
When i did "sudo snap install conjure-up --classic"
2.3.1 version of conjure-up installed on ubuntu 16.04.03 by default which is missing landscape option for conjure-up

How to get landscape on Ubuntu 16.04.03?

Any suggestions?

---

