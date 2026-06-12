---
title: "Feisty Upgrade: new kernel causes critical temp reboot"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by qwerkus on 2007-04-21
hi,

Just follwed the "official" way to upgrade to feisty on my centrino first generation; after reboot, the laptop keeps rebooting itself after a few minutes, displaying an ACPI error message: critical temperature reached.
I guess the 2.6,20 kernel shipped with feisty doesn t like my acpi...
Any ideas to get it working ?

Thank for help,

qwerkus

PS: don t know if it matters, but I m running Xubuntu...

---

### Post by Nik_Doof on 2007-04-21
It's possible you have a twitchy ACPI implementation on your laptop, I have the same-ish issue in that the temp sensor would jump up to 255 degrees causing the kernel to have a flip :)

As ACPI will mostly listen to the BIOS settings for its max/min temp, check in your BIOS, if its set too low (like below 40) it'll cause issues.

---

### Post by qwerkus on 2007-04-21
I checked my laptop-bios: there is no way to set the critical temp. Anyway, I didn't see anywhere that you can set critical temp manually on **centrino** laptops,
The acpi reboots at 67°C, although centrinos are designed to run at higher temperatures.
It should start the fan, and not reboot the machine ...
 
It worked fine on 2.6.17.10 and 2.6.17.11. What major change happened since ? Should I recompile the kernel with some centrino/speedstep settings enabled ?

Thanks for help

---

