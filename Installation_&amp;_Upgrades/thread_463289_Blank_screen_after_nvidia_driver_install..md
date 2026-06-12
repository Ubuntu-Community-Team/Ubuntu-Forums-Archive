---
title: "Blank screen after nvidia driver install."
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by xl_cheese on 2007-06-03
Now I cannot boot to ubuntu.  I have an 8600gt and initially installed the wrong driver before I found the beta driver instructions for this card.

Now my screen is blank.  How do I uninstall the driver so I can get back to ubuntu?

Can I do it from booting from the CD?

Thanks.

---

### Post by xl_cheese on 2007-06-03
I should have spent just a lil more time trying to figure it out.

I booted to the recovery mode.  After poking around on the command line a bit I saw that an xorg.conf.backup file existed.  Lucky me.  Copied it to xorg.conf and I'm back in business.

Now to figure out how to install it correctly...

---

