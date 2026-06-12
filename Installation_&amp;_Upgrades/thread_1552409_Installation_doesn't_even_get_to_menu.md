---
title: "Installation doesn't even get to menu"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by naproduction on 2010-08-13
I have tryed to install Ubuntu 10.04 using both the USB flash drive and the live cd and both have not worked. The load screen appears and right as it looks like it is done loading and is about to bring up the menu it goes black and my monitor says that there's no signal. any suggestions? possible hardware issues?

---

### Post by dabl on 2010-08-13
Yep -- it's ACPI, I think, or some other power management issue.

When you boot the Live CD, there is an initial text menu.  At the bottom are some "F" key options , and one them has an ability to add a "boot" option.  Try pressing F4 or F6 or whatever it is, and enter "noacpi" with no quote marks, and then try to continue booting.

---

### Post by naproduction on 2010-08-14
I disabled the ACPI dealio and now when all the dots light up like it's finished loading nothing happens haha so instead of shutting off at that point and losing signal it just sits on that screen

---

### Post by oldfred on 2010-08-14
I have nvidia but this may work for some others. From the f6 choose nomodeset. I also had to use the nomodeset on the first boot by editing grub with e and replacing quiet splash to get it to boot. After installing the nvidia driver everything has worked.

---

