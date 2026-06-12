---
title: "Installation 16.04 from USB throwing error (snd_hda_intel)"
date: 2017-01-17
forum: Installation &amp; Upgrades
---

### Post by ekke-ekke-ptang-zoo-boing on 2017-01-17
Hi, I'm just completing my first PC build and am stuck on my first attempt to install Ubuntu. I've spent a few days trying, and I've searched for each of the errors, but none of the solutions that they've raised seem to have worked.

The components:
Intel i5-6600K
ASRock Pro4 Z170
Kingston HyperX DDR4-2133 (2x 8GB)
Gigabyte Geforce GTX 1060K
Corsair CSM 550W
Kingston SSDNow UV400 240GB

I also have a wireless PCIe card connected

I've downloaded the 16.04 64 bit desktop Ubuntu installation, and used Rufus to write it to a USB stick. When I boot up using the default UEFI settings (aside from changing the boot order), everything begins as it should. I can press a key to enter a menu that has options along the lines of 'Run a test version of ubuntu', 'Install Ubuntu', 'Check disk for errors', 'Test memory', and there also are a number of other F-key options, including F6 which gives other boot options.

On trying to install Ubuntu, up pops a message labelled "nouveau" which states "unknown chipset". 
After maybe a second an Ubuntu loading screen appears, loads for a few seconds and then throws an error labelled by "snd_hda_intel", "failed to add i915_bpo component master (-19)" - the screen then turns off.

There are a few threads about each of these errors, and I've tried some of the advice with varying effects:

- Enable IGPU Multi-Monitor: the installation just hangs on a blank screen
- Boot with the options "nomodeset" and "rdblacklist=nouveau": this skips the nouveau message above, but the snd_hda_intel error still appears.
- Attempt each of the other boot options given in the f6 menu. Most of them don't do much. "noapic" Sends me to a busybox with intframs. "nolapic" ends in kernel panic.

As far as I understand, this error seems to be something to do with the inbuilt sound, but to be honest, I don't really understand much at all. Can anyone help me please?

---

### Post by kc1di on 2017-01-17
instead of nomodset try this command ```
nouveau.noaccel=1
```

---

### Post by ekke-ekke-ptang-zoo-boing on 2017-01-17
Thanks for your quick reply kc1di. I just tried that command, but there was unfortunately no change - both the nouveau and snd_hda_intel messages appeared and then the screen turned off. Any other ideas what might help?

---

