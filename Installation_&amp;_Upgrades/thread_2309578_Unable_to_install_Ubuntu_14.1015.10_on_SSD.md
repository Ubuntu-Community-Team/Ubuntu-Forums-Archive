---
title: "Unable to install Ubuntu 14.10/15.10 on SSD?"
date: 2016-01-11
forum: Installation &amp; Upgrades
---

### Post by Jamie_Edwards on 2016-01-11
Hi guys,

So I've recently put a Kingston HyperX 250Gb SSD into my system and immediately put Win10 onto it (Boo, yes I know but I game a lot so kinda need it otherwise Ubuntu all the way!). Anyway, I've tried to install both Ubuntu 14.10 AND 15.10 onto it and dual boot both of the OS's but have a major issue that happens with both of them...

So initially, upon trying to boot from my USB key, it goes pretty damn normal. I get asked if I want to install ubuntu or try before installing. But this is where it get's irritating. No matter whether I click install or try I get the following:

```

/init: line 7: can't open /dev/sr0: No medium found

```

And it then loops a couple of times (I found threads on this and tried everything and nothing worked).

It then gives up and boots into the BusyBox shell and says:

```

(initramfs) Unable to find a medium containing a live filesystem

```

And just sits there until I press enter. (Another thread said to wait a bit and Ubuntu will boot normally as the above is something to do with Floppy drivers in the bios). I've waited 30+ mins for something to happen and nothing does.

Any ideas on how I can get ubuntu installed onto my SSD?

Also, both liveUSB's work. I've installed both on various other PCs and laptops both legacy and UEFI without hitches.

---

### Post by Jamie_Edwards on 2016-01-11
So after some tinkering I figured out that if I put my usb drive into my motherboards usb3.0 port, ubuntu's bootloader craps itself but if I put it into it's 2.0 port, it still comes up with "cannot find /dev/sr0" but ubuntu boots normally... So much so that I'm currently installing ubuntu.

---

### Post by Irihapeti on 2016-01-11
14.10 is no longer supported, so it would be better to choose something that is. 14.04 would be a good idea, as it's a LTS release.

---

### Post by Jamie_Edwards on 2016-01-12
I know 14.10 isn't supported, I used it as a base to see if it was an issue with my 15.10 XD

---

