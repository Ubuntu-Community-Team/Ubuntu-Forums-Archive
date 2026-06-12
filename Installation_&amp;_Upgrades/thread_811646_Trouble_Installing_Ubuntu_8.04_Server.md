---
title: "Trouble Installing Ubuntu 8.04 Server"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by jrm213 on 2008-05-29
Hi,

I am trying to setup Ubuntu 8.04 LTS Server and I keep running into a problem. I get about 1/2 way through the install. It installs the core system and everything ok, but it gets hung up on Software Installation where you can choose to install things like DNS Server and LAMP etc... I get through the menu for that and hit continue, and it sits at 8% for a long time then jumps to 85%, it then says removing files at the bottom and then throws an error on the screen and I get sent back to the installation steps menu. 

It doesn't really say at all what actually happened. Does anyone know what might be wrong?

Is it a problem that there is no NIC in the machine? The one that was in it is not functioning so I took it out and haven't had the chance to replace it yet. Other than that the machine is solid.

I read the documentation on the site for installing but it doesn't give a way to tell what the problem is. Should I just skip this part of the install and use the utility to install them later? sudo tasksel...?

I have never installed Linux before, just used it.

Thanks for your help.

---

### Post by jrm213 on 2008-05-30
Well, 

I installed a network card and re-ran the install. Everything worked fine. So apparently you need a network card or the software installation of those packages will fail.

---

