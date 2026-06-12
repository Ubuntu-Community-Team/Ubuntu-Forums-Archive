---
title: "Making a custom Ubuntu installation"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by cwklinuxguy on 2011-01-16
Hey guys. I'm wondering--if say, someone wanted to make a custom installation CD of Ubuntu (while retaining the graphical installer and all) how could they do it?

I'm looking into the idea of starting a business of selling computers loaded with Linux at some point in time, and I'm wondering about this because I'd want a quick and easy way to install everything in one foul swoop. I would install Ubuntu (probably desktop edition unless otherwise requested) as well as all the media codecs and plugins that don't already come with the system, plus a few extras like Comiz, GTG, Thunderbird, etc. Can I just assemble it in a VM and burn a bootable ISO somehow? How do I do this?

---

### Post by pashdown on 2011-01-20
If you're going to be installing the same thing repeatedly and making small tweaks to it over time, setup a PXE server and apt-cacher-ng on your LAN.  This is an involved process, but so worth it once you are done because you'll never burn another CD for install.

[https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)

---

