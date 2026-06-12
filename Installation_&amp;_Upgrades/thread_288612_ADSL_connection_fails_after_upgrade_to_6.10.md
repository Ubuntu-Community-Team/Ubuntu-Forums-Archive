---
title: "ADSL connection fails after upgrade to 6.10"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by daugirdas on 2006-10-30
Hi,

The upgrade went rather well. Just I can't connect to internet any longer.
I have a modem connected to a network card (eth0). pppoe and pppoeconf are installed. I have recreated all configs for those and it doesn't help. All ubuntu* packages are installed on the system, and there are no old packages left.
When I try to connect with pon dsl-provider it instantaneously fails. 
This prevents firestarter from being upgrade and configured properly. Funny thing is I can't see both /dev/eth0 and /dev/ppp0. Should they be there at all? lsmod says that all the necessary modules are loaded; so is it hotlpug (which is missing the distro by the way) problem? Anything else?
Sorry I can't add any logs since I can't connect from ubuntu.

I really badly need to resolve this issue.

Edit:
The problem also occurs with both 5.10 and 6.06 live cds. So I guess it is not the system which is broken. Possibly I can't configure pppoe properly.

Could anyone give a full description how to configure ADSL on ubuntu edgy?

---

