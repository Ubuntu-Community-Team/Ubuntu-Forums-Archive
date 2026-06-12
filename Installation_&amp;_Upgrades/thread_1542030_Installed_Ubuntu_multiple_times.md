---
title: "Installed Ubuntu multiple times?"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by kmccmk9 on 2010-07-30
Hello, today I installed Ubuntu side by side with my Windows installation. It modified the bios so that when the computer starts you can choose what os to boot. Everything worked fine until I ran the update manager which updated my linux to the latest build and re-did the bios. Now I have two linux options but only one is installed. If I click the newest one, it loads. If I click the older one it gives errors but eventually loads the new one but all skewed and messed up. So how do I fix this? Is this a simple remove from os choice or is this like having multiple linux installations?

---

### Post by oldfred on 2010-07-30
Ubuntu normally downloads new kernels and adds them to the grub boot menu. You then can boot the older kernel in case the newer one has issues. We recommend that you keep 2 kernels, they do not take a lot of hard drive space and are a alternate way to boot if you have issues.

Uninstall extra kernels:-------------------------
In synaptic search for linux-image to choose to delete old ones
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

A Very Easy Alternate GUI Method - Ubuntu-Tweak
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by kmccmk9 on 2010-07-30
> **oldfred said:**
> Ubuntu normally downloads new kernels and adds them to the grub boot menu. You then can boot the older kernel in case the newer one has issues. We recommend that you keep 2 kernels, they do not take a lot of hard drive space and are a alternate way to boot if you have issues.

Uninstall extra kernels:-------------------------
In synaptic search for linux-image to choose to delete old ones
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

A Very Easy Alternate GUI Method - Ubuntu-Tweak
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

ok thank you I understand now. Also I have another question. This deals with screen recording. I used recordmyscreen and it recorded my audio from mic fine. But when I use xvidcap it doesn't record my mic at all. I have checked all volumes and they are turned up.

---

