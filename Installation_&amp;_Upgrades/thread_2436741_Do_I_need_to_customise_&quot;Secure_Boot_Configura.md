---
title: "Do I need to customise &quot;Secure Boot Configuration&quot; in UEFI?"
date: 2020-02-12
forum: Installation &amp; Upgrades
---

### Post by random turnip on 2020-02-12
I'm looking to install some form of Linux (Ubutnu, Mint, Pop_OS, not decided yet, going to try them all) on an old Samsung Series 5 laptop.  In another thread I asked about how safe this is, as there were bricking problems because of a firmware bug on this model, but I'm fairly sure that both Linux and Samsung have worked around this now (I hope).

Anyway, I'm reading through [this guide]("http://www.childsplay.mobi/blog/?p=83") of how to change the settings in the BIOS menu to allow a Linux installation.  I'm fine with disabling fast boot mode and secure mode, and know how to set the USB drive to be the first in the boot que, but there's a couple I don't understand.

Firstly, when I change the "Secure Boot Configuration" to custom it brings up a whole load more setting which mean nothing to me, so I don't think changing it to custom and not editing these settings is actually doing anything, but I aren't sure what else I should be doing.  [Looking at a different page]("http://www.rodsbooks.com/linux-uefi/") I'm not sure if this step is necessary at all.  Does this part really matter?  What is the point of it?

There is also a "OS mode selection" being changed to CMS OS.  I presume this means it will boot in legacy BIOS mode for my Linux install?  I'm thinking of not doing this and going with a UEFI install and hoping to not brick my laptop.

---

### Post by oldfred on 2020-02-12
I have 5 or 7 UEFI settings that I change on my Asus motherboard, some required & some optional. I have to redo them on every UEFI update.

But UEFI boot entries are preserved & will be kept even with a new install.
So if totally uninstalling a version, best to also house clean UEFI boot entries  (so you do not try to overfill UEFI NVRAM) & that version's /EFI/xxx folder in the ESP.
[https://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](https://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743)

---

### Post by random turnip on 2020-02-14
For anyone else stumbling across this, I didn't bother setting this to custom and it worked just fine. I also decided to use CMS mode, not because of the bug as such, but because I'd also read thread about people saying that some hardware functions didn't work properly with UEFI enabled.  The laptop works great, all hardware and lights appear to work as expected.

---

