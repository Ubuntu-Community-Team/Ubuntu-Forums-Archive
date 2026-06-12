---
title: "Upgrading over SSH"
date: 2014-09-12
forum: Installation &amp; Upgrades
---

### Post by Trevor_White on 2014-09-12
Hi all,
I've been looking over the net and can't see to find an answer so I'm hoping someone can help.

I need to update My Ubuntu 12.04LTS (command line only version), however the problem is my server doesn't have internet connection (and it's not possible to give it one), my local Windows machine however has direct internet access because it has a network bridge.

Is there anyway I can well putty to create a reverse tunnel to use my local internet connection that apt-get can run over?  I've even tried installing WinGate proxy to see if that helps but to no avail, and the only solution I've found requires two linux boxes.

Any ideas?

Many thanks.

---

### Post by Lars Noodén on 2014-09-12
> **Trevor_White said:**
>  the only solution I've found requires two linux boxes.

Any ideas?


You could boot the second machine as a live session from DVD and then install what you need.  Because it is a live session, there will be no changes to the system and everything would be as before once you reboot.

---

### Post by nerdtron on 2014-09-12
Windows machine has internet? You can try to use Connectify. [http://www.connectify.me/](http://www.connectify.me/)

If windows laptop is connected to wifi, you can share it to the LAN and connect the Ubuntu Server.

---

### Post by Trevor_White on 2014-09-15
Thanks both, my company will most likely block connectify, so I'm going to try and boot off the Ubuntu disc and see how that goes, thanks.

---

