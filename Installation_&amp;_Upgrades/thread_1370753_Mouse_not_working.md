---
title: "Mouse not working"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by gordon3913 on 2010-01-02
Since 1-1-2010 I had so many problems with 9.10 that I decided it would be better to re-install the system. It looked like I was going to get some of the same X problems but on doing a package upgrade I now get a gui but my IDE/USB mouse will not work.

How can I fix this?

I have Mint running on a seperate partition without any problems.

---

### Post by gordon3913 on 2010-01-02
I changed to a usb port connected mouse and re-booted.
The screen initally came up ok with the mouse working but after a few seconds my screen turned black with a few purple blocks with flashing U's.

This is real crazy.

I will have to use my newly installed Mint 8 for the time being.

---

### Post by cpplinux on 2010-01-02
Check the result of **dmesg **command. For example, I used to have problems with my keyboard and touchpad and I found dmesg complains "PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp". So I added i8042.nopnp as the boot parameter and it worked.

---

