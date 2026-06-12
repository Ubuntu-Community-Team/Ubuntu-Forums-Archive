---
title: "Help!!!!!"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by dellowner on 2010-12-15
I installed Ubuntu 32-bit v. 10.10 on a Dell Optiplex GX270, after installation i had to reboot, but then when rebooting it just goes to a black screen with a flashing _ 

What should i do to fix this?

---

### Post by kansasnoob on 2010-12-15
Looking at the Dell docs it appears you probably have an Intel 865G graphics chip:

[http://support.dell.com/support/edocs/systems/opgx270/en/ug/specs.htm](http://support.dell.com/support/edocs/systems/opgx270/en/ug/specs.htm)

If that's correct this may help you:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Intel_integrated_graphics_cards](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Intel_integrated_graphics_cards)

I have seen cases where instead of using the boot parameter "i915.modeset=0" it was necessary to use "i915.modeset=1".

Hope this helps.

---

