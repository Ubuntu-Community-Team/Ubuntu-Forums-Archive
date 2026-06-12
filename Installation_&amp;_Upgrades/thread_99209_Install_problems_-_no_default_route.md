---
title: "Install problems - no default route"
date: 2005-12-05
forum: Installation &amp; Upgrades
---

### Post by grw on 2005-12-05
I have tried installing 5.10 on my old Dell Laptop (for dual boot with Windows, which I would like to abandon eventually). I come to a screen that tells me that teh network autoconfig was succesful but "no default route was set". It advises me not to continue with the installation without a default route.

I can't access my network without user name and password. Could this be the problem? What do I do?

---

### Post by bwog on 2005-12-05
[QUOTE=grw]I have tried installing 5.10 on my old Dell Laptop (for dual boot with Windows, which I would like to abandon eventually). I come to a screen that tells me that teh network autoconfig was succesful but "no default route was set". It advises me not to continue with the installation without a default route. [/QUOTE]

My box has two network choices, etho and eth1, and the installer asked me wich one I wanted. Perhaps that is what you need to do too.

[QUOTE=grw] I can't access my network without user name and password. Could this be the problem? What do I do?[/QUOTE]

I didnt have to give that info during install and it just worked.

---

### Post by grw on 2005-12-05
I wasn't asked to specify eth0 or eth1. I was only told that no default route was set. I assume the installer is not getting the info from teh network it needs via DHCP. And I was wondering if this is because my computer is not allowed to access the network without username and password, which the installer doesn't ask for. ... ?

---

### Post by bwog on 2005-12-05
What I said only applies when there is more than one route to connect to the internet. I f there is, you see two lines on the screen,  for instance Gigabit nic 1 and nic 2.

I have a password for the router and for the internet provider, and didnt have to give them during install.

---

### Post by Hendry on 2005-12-05
[QUOTE=grw]I wasn't asked to specify eth0 or eth1. I was only told that no default route was set. I assume the installer is not getting the info from teh network it needs via DHCP. And I was wondering if this is because my computer is not allowed to access the network without username and password, which the installer doesn't ask for. ... ?[/QUOTE]
Does your DHCP server assign you a gateway ?

---

### Post by grw on 2005-12-05
I don't know if the DHCP server assigns a gateway. The entire message I got was this: 

 The network autoconfiguration was successful. However, no default route
 was set: the system does not know how to communicate with hosts on the
 Internet. This will make it impossible to continue with the installation
 unless you have the first official Debian CD-ROM, a 'Netinst' CD-ROM, or
 packages available on the local network.
 .
 If you are unsure, you should not continue without a default route:
 contact your local network administrator about this problem.

Well, I think the network administrator is not keen on me having a linux computer in teh firest place. What info could they give me? What is a default route? There were options for Name servers on previous screens of teh installer, if I remember, that I only got to by pushing teh 'back' button.

What happens if I just continue without the default route? Can I set things up later? Why do I need to connect to teh internet to do an install?

---

### Post by kenweill on 2005-12-10
I too have the same problem.

No Default Route.

I've tried the command ipconfig /all under the command prompt of windows. It produces the ip address, subnet mask, default gateway, dhcp server, and dns server information.

I tried to manually configure the network.

But it produces another error.

Gateway unreachable.

I have no idea why its unreachable. It works on windows. Why not on Linux?

My current connection on windows uses an accelerator/driver. I guess its one of the reason why it wouldn't work on linux.

Its a windows based software.

---

