---
title: "No option to boot from USB on Asus UX31A Touch"
date: 2013-05-18
forum: Installation &amp; Upgrades
---

### Post by theaceoface on 2013-05-18
I'm trying to install Ubuntu 13.04 on my Asus Zenbook prime touch (I'm not trying to dual boot, I just want linux)

And I've done some reading and done everything people say I should:

1) I've updated the bios 
2) Turned off secure boot
3) Turned off fast boot
4) Enabled CMS

But USB is still not listed as a boot option. I've tried a bunch of things but nothing seems to work.

update:
Ok I solved it. 
5) First I uninstalled Asus instant on in windows
This may or may not have helped. But it still didn't work after this.
6) I went and changed the usb configuration in the advanced panel of the bios/UEFI. There I enabled both legacy usb support and XHCI pre boot mode.
I was then able to boot from USB

Problem solved!

---

