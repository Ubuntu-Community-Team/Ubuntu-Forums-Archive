---
title: "cli cloning tool suggestions needed"
date: 2014-01-14
forum: Installation &amp; Upgrades
---

### Post by J_Me on 2014-01-14
I need some suggestions for a secure cloning and partitioning tool that works over a local network for a headless box. The drives are on two separate machines behind my router. Thanks

---

### Post by tfrue on 2014-01-14
As far as secure, you will need to encrypt the data on one machine then send it over the network. I don't believe there is anything like SSL for transfering data over the network, unless you did transfer the files through apache with a web browser, maybe then. But there are several ways to transfer files one of which being '*dd*', I don't really know the syntax of the command but a Google search for dd in Linux would probably do the trick or reading the MAN page for dd in Linux. Another would be set up a Samba server on the headless machine which works great! I love using Samba actually and here is a pretty good site that explains how to set one up, but I will give you some examples if you want. ([Samba]("http://bit.ly/1d1hx0R")).

Good luck,
Chris

---

### Post by J_Me on 2014-01-15
Thanks for the reply but copying files isn't the problem, I need to clone the whole OS to another drive. Anyway you mentioned ssl, have a look at secure copy from the terminal 'man scp' maybe interesting. DD is a powerful tool which I use but some people call it 'destroy disc' not recommended for the faint of heart.  What I'm looking for is a straight forward CLI alternative to clonezilla and gparted. Thanks anyway

---

