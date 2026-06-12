---
title: "Unable to Boot Anything"
date: 2012-01-28
forum: Installation &amp; Upgrades
---

### Post by Joomla12 on 2012-01-28
This is really frastrating. I've been trying to install some sort of UNIX system for the past couple days on my laptop (Toshiba Satellite L770D) but it has an internal Bluetooth adapter which is preventing anything to boot after installation. I've tried Mint 12, Fedora 16, Kubuntu 11.10, OS X Snow Leopard, and so on. Booting in verbose mode always spits out the same error which is "hci0 command tx timeout". I've set the "nomodeset" flag but it doesn't resolve this issue. What should I do?

---

### Post by kc1di on 2012-01-28
have you tried disabling the bluetooth in bios then booting?
Also does the live cd run on that machine?

---

### Post by BC59 on 2012-01-28
I think that is a bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/898826](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/898826)

---

### Post by Joomla12 on 2012-01-28
> **kc1di said:**
> have you tried disabling the bluetooth in bios then booting?
Also does the live cd run on that machine?

I'll see if I can disable it once I get finished downloading updates. And the Live USB will only boot into the installer. Live mode won't boot and gives me the same error.

Edit: There isn't an opption to disable it in the BIOS. Is there a way to find which kernel module this is using and how to disable it?

Edit 2: The problem was that X wasn't loading because it couldn't detect my monitor. Installed the ATI driver and I'm able to boot into an X session now. Doesn't necessarily mean it's solved but I can use my system now at least.

---

