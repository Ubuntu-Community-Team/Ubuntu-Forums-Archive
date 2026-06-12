---
title: "Network install constantly failing"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by gillespiea on 2010-09-04
Hi all,
I am thinking of rolling out Ubuntu on several computers on a network. I have my Server set up, running a dhcp,dns and tftp. It also is running apache 2, php5 and mysql.

My problem is that, i am currently testing out the network install on a virtual machine. The virtual machine is using the network card on the local machine, so it connects to the dhcp and dns, gets an IP and is then forwarded to the install media.

Once i have set a few things up the installation gets to the Select and Install software stage. Gets a few percent through it and fails.
It appears to be on "post-installation trigger fontconfig" at 6%  goes to 10% and says cleaning up and then gives me the error.

All computers go through the server for the internet connection, it is not using a proxy, just a gateway, so the connection to the sources should be fine (i can update and upgrade my host computer fine and gain access to all different ports through the internet).

VM Machine is using 1 core of the hosts CPU (2.4Ghz per core) 2048MB RAM (host has 6GB) 8GB hard drive (and in writing this i'm wondering if there is enough swap space etc?) 32mb Video and 3d video enabled.

---

