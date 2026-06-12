---
title: "Can't boot because of amd gpu"
date: 2018-10-28
forum: Installation &amp; Upgrades
---

### Post by rickseiden on 2018-10-28
Hello,

I have an HP Envy m6-p114dx. It has an AMD Radeon R7 graphics card inside it.  When I boot the live USB stick for 18.10, and include "acpi=off nolapic nomodset" in the boot parameters, but take quiet and splash off, I see that my computer hangs at

Switching to amdgpudrmfb from EFI VGA

So, I know it's my graphics card.  How do I either install the drivers on the live USB (which I don't think I can do), or have the system boot without switching to amd gpu?

Thanks
Rick

---

### Post by rickseiden on 2018-10-28
I had read about adding "nomodeset" to the boot parameters, and did that, and it didn't work.  Then I realized I was using "nomodset" with the missing e.  When I add acpi=off nolapi nomodeset to the boot parameters in GRUB, I get it to boot to a certain point.  I actually get to a point where it says that it can't find any live media.  But that's a different thread.

---

### Post by jkhan720 on 2018-10-28
Try amdgpu.dc=0 instead of nomodeset

---

