---
title: "X crashes after 12.04 -&gt; 12.10 upgrade"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by destiney on 2012-10-20
I upgraded from 12.04 to 12.10.  Now my X server will not start.  I'm attaching some screen shots of the stack trace and logs.

I noticed I no longer have an xorg.conf file since the upgrade.  Is that normal?

Google's not turning up anything useful.  Any idea how to fix?  Thanks.

---

### Post by 2F4U on 2012-10-20
> I noticed I no longer have an xorg.conf file since the upgrade.  Is that normal?

The xorg.conf file has been eliminated long ago.

What are your hardware specs, what graphics card do you have, what graphics driver was installed in 12.04? If you look through the forum, a lot of people report problems with proprietary graphics drivers for ATI cards due to the Xorg server Ubuntu 12.10 uses.

---

### Post by destiney on 2012-10-20
lspci says I have this:

00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Rage XL (rev 27)

I have no idea what was graphics driver was installed before I upgraded, it worked without issue or additional configuration.

---

