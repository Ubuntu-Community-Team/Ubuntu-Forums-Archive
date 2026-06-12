---
title: "After Upgrading from 10.10 to 11.04 Laptop does not boot"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by muzikayise on 2011-05-05
After upgrading my Toshiba Satellite Pro, it would not boot but on closer inspection this not a 11.04 upgrade i had the same issue when upgrading from 10.04 to 10.10. And I've finally figured out what the problem is.

**[SIZE="4"]after upgrading the Laptop boots up fine but does not get into the login screen because of graphic card problem. I have an ATI Mobility Radeon HD 3650 graphics card.[/SIZE]**

I solved this issue by doing the following:

1.1) restart your when your system hangs and you can do that by Ctrl+Alt+Delete

1.2) before your system boots press Esc so you may force GRUB

1.3) now once in GRUB select the (recovery mode) option

1.4) this will display another screen with more options, select option to boot into ubuntu using failsafe graphics

1.5) once you make this selection GRUB will then take you to the ubuntu login screen but in low graphics mode. (kinda like Windows Safe mode but way better)

1.6) once youre logged in connect to the internet

1.7) Use the Additional Drivers Application this will detect what hardware needs drivers in my case only my ATI Card needs drivers and ATI Catalyst Control Center

1.8) this will install the drivers for you then it will ask you to reboot your system.

1.9) then once you reboot GRUB will come up automatically but this time just press enter because the normal ubuntu mode is selected by default

1.10) and Voilà, 11.04 works fine now

so i think if my laptop had a standard graphics card i dont think i would have this problem whenever i upgrade.

anyway i just wanted to share this maybe someone else might find it useful

thanks for 11.04 its awesome

---

