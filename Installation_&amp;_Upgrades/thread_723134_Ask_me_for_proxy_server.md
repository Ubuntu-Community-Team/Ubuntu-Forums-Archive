---
title: "Ask me for proxy server?"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by tomhorsley on 2008-03-13
Installing gutsy from the alternate CD, I want it to always use a proxy for
access to the repos, but so far, the only way I have discovered to get it
to ask me for a proxy is to install with no network hardware in the system
at all. Then when it can't get to the mirrors, it asks about a proxy and I can
define one (but of course it still can't get to the mirrors since there is no
network).

If there is some boot parameter, please tell me exactly how to feed it a
boot parameter, because I don't get a boot prompt, I just get a menu
of options when the alternate CD boots.

---

### Post by bapoumba on 2008-03-13
I'm not sure I understand your problem.

When you install from the alternate CD, at some point you have the option to declare a proxy. If you do not, then the install goes on without internet access (if the proxy is required on your network) and you can set it up afterwards. This is not a reason for not booting after the install.
What kind of hardware do you have to remove for the install to go through ?

---

### Post by tomhorsley on 2008-03-15
> **bapoumba said:**
> I'm not sure I understand your problem.

When you install from the alternate CD, at some point you have the option to declare a proxy. 
 ?

It would be nice if that happened, but if I have a network that functions
correctly, the installer refuses to ever give me a chance to tell it to use
a proxy. Apparently it discovers the direct connection and won't ask me
for a proxy.

The trouble is, I need to give it a proxy even though there is a working
network, because the powers that be don't want big downloads going
through the normal network.

The only way I've gotten it to ask about a proxy is to do the install with
no network card(actually it is a Xen HVM install, so no network card is
emulated by commenting out the vif in the xen config file).

---

