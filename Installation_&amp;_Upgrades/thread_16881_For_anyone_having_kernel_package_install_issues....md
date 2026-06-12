---
title: "For anyone having kernel package install issues..."
date: 2005-02-24
forum: Installation &amp; Upgrades
---

### Post by jtopping on 2005-02-24
Well, I was getting very confused installing Ubuntu...

During installation, the install kept failing during installing base system. It would complain that the kernel package was not valid. So I did a CD verification and it failed the MD5. So, I burned another cd, at a lower speed. Same issue. Tried different media, same issue. Each time i burned, i checked my sums and  they matched what they should be. Looking around, i found some others had the same issue, but with no resolution stated in their threads.

What I found was that you need to start the installer by adding -noapic and -lapic to the boot loader, why I do not know...it was many people's suggestions for other issues that I randomly tried and worked.

So, i put the ubuntu cd in, when it says hit enter to boot, i instead entered:
linux -noapic -lapic

and then hit enter, and viola, my install went smoothly.

Then, on first boot, the hotplug service hung during start up, so i did the same thing, but through GRUB's menu, and now I will always load with those flags set.


Post here if this helps you out, and if you have any explanation why this is such?

---

