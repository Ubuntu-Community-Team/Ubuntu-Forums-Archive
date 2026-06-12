---
title: "FIPS mode lost after an update"
date: 2023-07-20
forum: Installation &amp; Upgrades
---

### Post by faldrich on 2023-07-20
We are building/testing Ubuntu Focal Fossa (20.04) in FIPS mode; currently, in a VMware vm.  Recently, after applying some updates and rebooting, the system appears to have lost FIPS mode.  fips-mode-setup --check says "FIPS mode is ."   Should this ever happen?

The tools to configure this are (as I understand) meant to automate this process.   When I go to re-enable FIPS mode, it next asks me to manually update the bootloader.

So I see two problems... 1) FIPS mode was lost, 2) re-enabling this via "fips-mode-setup --enable" doesn't fully work, requiring some apparent manual updating.  Additionally, the output of fips-mode-setup suggests a command called "grubby" isn't present -- which prompts a manual update of the loader, but it's not available in the repositories (that I can see) -- should it be, or even if this is a dependency would it make sense to have it a part of the FIPS or base distribution.

For us to adopt Ubuntu/FIPS in our environment, we can't have FIPS mode being disabled like this, so I want to understand how to mitigate it.


Thanks.

---

### Post by faldrich on 2023-07-20
So, I think I solved the issue.  The clevis-initramfs was missing.  I joined the LUKS devices to the Tang servers, installed clevis-initramfs and rebooted, worked fine.

---

### Post by MAFoElffen on 2023-07-20
Happy you found the problem.

So you can mark this as "Solved" now?

---

