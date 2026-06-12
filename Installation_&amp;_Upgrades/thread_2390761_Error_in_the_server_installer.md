---
title: "Error in the server installer?"
date: 2018-05-02
forum: Installation &amp; Upgrades
---

### Post by yar.s on 2018-05-02
When I try to install Ubuntu Server 18.04 from the image of ubuntu-18.04-server-amd64.iso (I need LVM)
in a virtual machine (VMware ESXi 6.5) in the "Russian version" of the installer (I choose "Russian" on the first page),
when setting up the network, it is not possible to manually configure the network settings.
After the DHCP-server did not respond, I choose "Configure network manually" (in Russian, of course),
but actually works the item "Do not configure the network at this time",
as if I did choose "Do not configure the network at this time".
So I can't configure the network.
This is obtained only in the "Russian version" of server installer.
If I doing everything in the "English version" (did choose "English" on the first page), then everything works correctly.
It looks like this is a bug in the server installer.

Who can I contact with this problem?
Thanks in advance.

---

### Post by dino99 on 2018-05-02
Looks like a bug with 'subiquity' you might want to report on launchpad (related to Russian setting not managed, cyrillic font not available ?)

But you maybe able to bypass the problem: say you go with english interface for installation; then you can change the language to Russian into Settings option -apply to whole system); could this be a problem ?

---

### Post by yar.s on 2018-05-02
I reported a possible bug on launchpad: [https://bugs.launchpad.net/subiquity/+bug/1768551](https://bugs.launchpad.net/subiquity/+bug/1768551)
Thank you!

I use a workaround: change language to English before the network configuration, and after - change back to Russian and continue the installation.

---

