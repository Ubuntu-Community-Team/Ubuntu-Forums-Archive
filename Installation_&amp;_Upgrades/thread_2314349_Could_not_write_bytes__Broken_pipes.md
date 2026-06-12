---
title: "Could not write bytes : Broken pipes"
date: 2016-02-20
forum: Installation &amp; Upgrades
---

### Post by jaswinderjalandhar on 2016-02-20
I have installed ubuntu 12.04 on my ACER All in one PC with Model Veriton. After completing installation there is the message to restart the PC.
After restarting, before the user login screen appears, i got the following message  " COULD NOT WRITE BYTES : BROKEN PIPES ".
I have also replaced the installation media twice, but getting the same error every time after the installation.
Any one Pl help.

---

### Post by grahammechanical on 2016-02-20
Is Ubuntu loading to a login screen & can you log in and get to working desktop? If you can load Ubuntu and it works as it should, Then there is no problem.

As Linux loads it will print system messages to the screen. Most of the time we do not see these messages because at the start of the OS loading process Linux has been instructed to be quiet about what it is doing. Also, we usually have a splash screen that hides any messages that might cause us concern if we saw them.

A broken pipe message means that some system process was writing to another system process but the other system process broke the connection. Most likely caused by the other process shutting down.

I have, myself, sometimes seen the broken pipe message but it has never stopped Ubuntu from loading to a working desktop.

Regards.

---

