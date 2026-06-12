---
title: "Ubuntu 10.04 64bit won't boot, even after boot-repair had done it's magic..."
date: 2013-07-16
forum: Installation &amp; Upgrades
---

### Post by RockSolidAfrica on 2013-07-16
I have bought a brand new Dell Inspiron 14z with Win8 pre-installed.
I need the Windoze for my architectural work (ArchiCad)

So I tried the Ubuntu 12.04 32bit live-USB, it worked.
Tried to install, which it did but then failed to boot. (it just booted Win8 which then repaired the MBR)

Okay, so I downloaded Ubuntu12.04 arm64 desktop alternative.iso
Installed okay, but failed to boot.
Downloaded the live cd iso of boot-repair...
Made it to do it's magic...
rebooted... and it now hangs at the point where GRUB presents me with a correctly looking boot menu, I choose the ubuntu normal boot, then I get a purple-ish screen (as if it is about to boot the linux img) but there it hangs!
boot-repair gave me this reference: paste.ubuntu.com/5877893

Then I tried again by downloading the live iso Ubuntu 12.04 64bit
installed it...
booted it... HANGS!
Then I apt-get installed boot-repair on the live-USB, made it do it's magic...
rebooted... HANGS at the same point: purple screen after GRUB2 menu.

The odd thing is that Win8 will boot from that menu.

What am I doing wrong here?

Any help is greatly appreciated.

---

