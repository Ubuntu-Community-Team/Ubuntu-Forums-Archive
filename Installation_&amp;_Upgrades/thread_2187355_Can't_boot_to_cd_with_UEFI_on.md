---
title: "Can't boot to cd with UEFI on?"
date: 2013-11-11
forum: Installation &amp; Upgrades
---

### Post by xan3 on 2013-11-11
I can't seem to press F12 to boot while UEFI is enabled. SecureBoot is disabled, the option to use F12 is enabled, but it doesn't work. Unless I disable UEFI. Trying to install Ubuntu 13.04.

---

### Post by oldfred on 2013-11-11
Every vendor seems to do UEFI a bit different even thought it supposed to be a standard.

I would try a flash drive.

A few systems have to install in BIOS mode and then use Boot-Repair to convert to UEFI.

What system it this? And what video card/chip?

Besure to review install instuctions for UEFI. See links in link in my signature.

---

### Post by ubfan1 on 2013-11-12
In Windows, make sure "fast boot" is disabled.  You then get more time to type function keys at bootup.  Without fast boot, 6 seconds to vendor splash screen, then I type F12 and it works.  With fast boot, splash screen come up in 3 seconds, but then F12 doesn't work.  Repeatedly typeing F12 right after power-up may work half the time.

---

