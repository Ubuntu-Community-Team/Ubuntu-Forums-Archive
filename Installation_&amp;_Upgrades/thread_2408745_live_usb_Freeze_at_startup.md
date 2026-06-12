---
title: "live usb Freeze at startup"
date: 2018-12-22
forum: Installation &amp; Upgrades
---

### Post by richardelima on 2018-12-22
Using HP all in one 8373 . with AMD Radeon R5 Graphics. Using lubuntu USB thumb drive with Unetbooitn. Whenever I got to desktop it gets frozen. Only Mouse moves but clicking is unresponsive. keyboard useless. Reboot stays the same. Have tried other distros and is the same result: linux mint cinnamon and  xfce, peppermint. What can I do ?

---

### Post by Autodave on 2018-12-22
Did you actually get it installed or are you speaking of the lockup while still on the installer?

---

### Post by vidtek on 2018-12-23
> **richardelima said:**
> Using HP all in one 8373 . with AMD Radeon R5 Graphics. Using lubuntu USB thumb drive with Unetbooitn. Whenever I got to desktop it gets frozen. Only Mouse moves but clicking is unresponsive. keyboard useless. Reboot stays the same. Have tried other distros and is the same result: linux mint cinnamon and  xfce, peppermint. What can I do ?

You could try editing the startup when first booting, when the first grub screen from the usb stick materialises, press e for edit then scroll down to the entry which says quiet splash and delete those two keys and replace with nomodeset instead.

You will then get a cli listing of what is happening in the boot sequence, you may even find you can then carry on and install it.  I think it would be helpful with all live distros to include this option in the menu.
I no longer even attempt to install a new distro without doing this first.

If you still have issues, try with a different distro, some work, some don't on different hardwares.

Cheers, Tony.

---

