---
title: "Few questions before I install..."
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by Mol_Bolom on 2008-10-31
I had just set up 20g of space and would like to know if it's possible to install without installing a boot manager?
  I have the Rescue LiveCD which I can boot into it from, which I'm definitely sure I can do it, I think gag works without installing, but I'm not sure, it's been a while since I've used it.

Every distro I've installed before Ubuntu 8.04 has asked if I wanted to install a boot loader into the MBR or just the root partition, when I installed Ubuntu on my older computer, it didn't ask. So is there a way to force it to ask where I want the boot loader?

Thanks...

---

### Post by kostkon on 2008-10-31
> **Mol_Bolom said:**
> I had just set up 20g of space and would like to know if it's possible to install without installing a boot manager?
  I have the Rescue LiveCD which I can boot into it from, which I'm definitely sure I can do it, I think gag works without installing, but I'm not sure, it's been a while since I've used it.

Every distro I've installed before Ubuntu 8.04 has asked if I wanted to install a boot loader into the MBR or just the root partition, when I installed Ubuntu on my older computer, it didn't ask. So is there a way to force it to ask where I want the boot loader?

Thanks...
Yes, I think the Alternate Install CD offers you such an option.

---

### Post by mikewhatever on 2008-10-31
You have to install Grub, but the good news is, it doesn't have to go to the MBR. There is the 'Advanced' button on bottom right of the last window where you get to review all the choices, and which is before the actual installation. By clicking the Advanced button, you can choose were Grub gets installed.

---

