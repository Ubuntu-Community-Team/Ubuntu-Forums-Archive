---
title: "Ubuntu 18.04LTS Server install Problem with renamed network interfaces"
date: 2018-04-28
forum: Installation &amp; Upgrades
---

### Post by zappaf. on 2018-04-28
Hi;
i have problems installing Ubuntu 18.04LTS Server on Intel bases Supermicro Board (SuperMicro X9DRi-LN4F+) with multiple Intel Nics. Under some Intel Boards this network renaming does not work properly and so i am never to be able to install and configure a working network interface.
I had the same problem on different testservers under 16.04 and could only solve the problem editing grub config with "*ifnames*=[I]0 biosdevname=0".

[/I]Found the solution in this thread:
[https://ubuntuforums.org/showthread.php?t=2347903&highlight=net.ifnames%3D0](https://ubuntuforums.org/showthread.php?t=2347903&highlight=net.ifnames%3D0)

This is obliviously a problem with some Board with Intel chipsets...

Is there a way to disable this biosdevname/if- renaming in the installer? 
Disable it totally?

thx

---

