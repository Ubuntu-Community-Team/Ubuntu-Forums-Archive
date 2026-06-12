---
title: "Using DisplayPort for Video During Installation"
date: 2012-09-27
forum: Installation &amp; Upgrades
---

### Post by Incarnadine on 2012-09-27
I bought a HP Elite L2201x monitor that only supports a DisplayPort video input. I attempted to install Ubuntu 12.04 with this monitor and after the BIOS boots from the CD the screen stays black. I tried this several times, but get the same result.

I then plugged in my older monitor and hooked it up via the DVI port and this solved the problem. After I installed Ubuntu and the ATI drivers I plugged back in my new monitor and now the DisplayPort works! What's the reason for this? Is it because Ubuntu doesn't come with a generic DisplayPort driver?

---

### Post by dino99 on 2012-09-27
displayport is drived directly from the kernel. So which kernel is it ? (should work with kernel 3.5+) and which xorg abi ? (but should not matter)

---

### Post by Incarnadine on 2012-09-27
> **dino99 said:**
> displayport is drived directly from the kernel. So which kernel is it ? (should work with kernel 3.5+) and which xorg abi ? (but should not matter)

Thanks for the reply :p I'm not sure what kernal it is. It's whatever kernal comes with the Ubuntu 12.04 installation disc. Is there anyway to check this?

---

