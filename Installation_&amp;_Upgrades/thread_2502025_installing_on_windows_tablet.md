---
title: "installing on windows tablet"
date: 2024-10-30
forum: Installation &amp; Upgrades
---

### Post by dcsltd on 2024-10-30
im stuck guys, i have a geopad 110, windows 11 tablet/keyboard thing, very like a surface, but it doesnt seem to have a bios, boot menu, or able to boot from a shift+restart - i want to get ubuntu onto it as i have recenly found that ubuntu can read drive volumes that are sometimes unreadable on a windows pc (so for data recovery) - anybody got any tips please, it does have a standard usb port for dongles

---

### Post by tea for one on 2024-10-30
> **dcsltd said:**
> im stuck guys, i have a geopad 110, windows 11 tablet/keyboard thing, very like a surface, but it doesnt seem to have a bios, boot menu
That's unusual
When you power on the PC, no information about pressing a dedicated key for settings?

Anyway, try this:-
Boot into Windows 11 > Windows Settings > System > Recovery > Advanced Startup > Restart Now
After Restart > Troubleshoot > Advanced Options > UEFI Firmware Settings > Restart

---

### Post by ajgreeny on 2024-10-30
I do not know Windows 11 but possibly when restarting from the normal hibernated state when you shutdown Windows means that you do not get the usual screen display offering a key-press to enter the UEFI setup?

Make sure that fast-startup is disabled in Windows so that it powers off fully rather than the default hibernated state; I have no idea how to do that but I know it can be, and has to be done to allow dual booting.

---

### Post by dcsltd on 2024-11-10
you are a star, i now have a bios, and was able to enable getting into this on boot too, next step, trying to get an installer to boot, im stuggling, it keeps bypassing usb, but i will keep at it :-)

---

