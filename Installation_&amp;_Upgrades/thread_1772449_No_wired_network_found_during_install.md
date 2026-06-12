---
title: "No wired network found during install"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by Despot Despondency on 2011-05-31
Hi,

I've just installed version 11.04 of ubuntu on to my computer but no wired network is found. 

The router is definitely working as the wired network is working on my laptop. 

The modem on the computer also works as it was working over the weekend on a gentoo install, which I have since removed for this copy of ubuntu.

My initial suspicion is that ubuntu can't recognise my hardware.

I don't know what to do from here. Any pointers?

TAI

---

### Post by mikewhatever on 2011-05-31
Try the usual commands:
```
ifconfig
lspci
```

If the hardware is recognized you'll see it in the output.

---

### Post by Despot Despondency on 2011-05-31
Hey, thanks for the response. 

Tried those commands and the modem is recognised. 

How come the network isn't configured automatically then? Any ideas?

---

### Post by mikewhatever on 2011-05-31
So, there is a router, and a built in modem? Which one did you try using? What makes you think the network is unconfigured? Do you get an IP?

In short, you should really provide more detailed info, instead of me squeezing it out of you.;)

---

### Post by Despot Despondency on 2011-05-31
Maybe I'm not being very clear.

1) I put the liveCD in the computer and boot up as per usual install.
2) Ubuntu then tries to link to the wired network and fails.
3) I then click "Install Ubuntu" and follow the usual install procedure that follows.
4) When I reboot the computer it is still not able link to the wired network. Presumably for the same reason as during the liveCD.

As noted in a previous post my hardware is recognised. The on-line modem is a realtek R8169.

My on-board modem is linked to a BT homehub (which I thought was called a router, sorry if this is incorrect), as is my laptop which is working perfectly. 

I am assuming my network isn't configured as it is not working.

---

