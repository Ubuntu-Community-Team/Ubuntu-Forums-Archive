---
title: "Message during update of 22.04 after upgrade"
date: 2022-08-17
forum: Installation &amp; Upgrades
---

### Post by zacktu on 2022-08-17
I upgraded from 20.04 to 22.04 from the command line.  Along the way I selected configurations as they were rather than accept the new ones.  When I did a sudo apt upgrade I have a series of messages similar to this one. 
[B]
Skipping acquire of configured file 'sutton.newell/binary-amd64/Packages' as repository 'http://lenovo.archive.canonical.com jammy InRelease' doesn't have the component 'sutton.newell' (component misspelt in sources.list?)[/B]

This appears to relate to my Lenovo laptop.  I found a sutton.newell entry for 22.04 in Synaptic and installed that.  I still get the message.  Do these messages indicate that some Lenovo drivers are not being found and installed?

---

### Post by grahammechanical on 2022-08-17
It could mean that the Lenovo archive for 22.04 (jammy) does not contain any package listed as sutton.newell.

The  system has a text file that lists the internet addresses for all the  repositories. See /etc/apt/sources.list. The internet addresses for  Ubuntu 20.04 repositories contain the word focal. When we upgrade to  22.04 those internet addresses have the word focal replaced by the word  jammy. Installing the sutton.newell package brought in the drivers but you still have an address for a repository in sources.list that does  not have the sutton.newell component. That is why you are still seeing that  error message.

Regards

---

