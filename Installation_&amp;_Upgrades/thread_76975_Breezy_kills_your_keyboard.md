---
title: "Breezy kills your keyboard??"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by rossifumi-gp on 2005-10-16
After upgrading from Hoary to Breezy my USB keyboard will from time to time just stop working.  I have to unplug and plug back in the keyboard to have it re-detected.  Anything I can try to fix this?  I've looked into xorg.conf; everything looks fine..

---

### Post by rossifumi-gp on 2005-10-16
Just a followup.  Possibly an x.org issue?  No one else having this issue?

---

### Post by artships on 2005-10-17
Same problem - I have a USB keyboard, the Breezy ISOs can deal with it, Grub understands it, but when booting into Breezy it asks me to login (I'd fixed hoary to skip login), which is a bit of a problem since none of the keys are what they used to be.  Also lost "locales", judging from the boot messages, but I can deal with that later.  Misunderstood keyboard... A show-stopper.  Thank BillG I'm dual-booting WinXP - And boy, does it hurt to say that!

---

### Post by rossifumi-gp on 2005-10-18
My only solution thus far has been to dig up an usb to ps/2 adapter and plug the keyboard into the old ps/2 port.  Are we going backward here? :(

---

### Post by artships on 2005-10-18
I still had my ps keyboard laying around, so I tried booting with it.  Didn't make any difference.  I've since booted from the breezy livecd, copied most of my customizations to a fat32 partition, and did a complete re-install of breezy - After which I read that I could have used the breezy install cd and entered "rescue" at the boot prompt.

---

