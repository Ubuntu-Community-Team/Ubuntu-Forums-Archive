---
title: "I'm having problems with a new roll-your-own kernel"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by fnf on 2006-11-26
Hi everyone.

After installing my customized linux kernel on Edgy, I have found two problems so far:
[LIST]
[*]The console didn't show anything, though it was responsive.
[*]Nothing networking-related worked, I could no longer connect to any networks other than lo (including wireless and ethernet).
[/LIST]

To further clarify my situation:
[LIST]
[*]If I use another framebuffer driver (nvidiafb), the console works normally (but nvidiafb has a known problem that I couldn't change the default resolution in anyway).
[*]To ensure maximum compatibility, I made the new kernel as bloated as possible (that is, I selected any relevant - but must be compatible - options). I also left the old config intact in another compilation, but to no avail.
[/LIST]

I'd like to know if there was anything Ubuntu was doing under the hood that I wasn't aware of. Thanks for any insights.

[Edit]: Btw, here are the relevant errors with bringing up network interfaces (brought from my memory):
> $ sudo ipw3945d
... ERROR: Could not find any Intel PRO 3945ABG Network Connections ...

Bringing up eth1 (my wireless connection) and eth0 (ethernet) both failed. They couldn't find any DHCP server around.

---

