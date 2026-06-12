---
title: "Noble: incorrect resolution on boot (640x480?)"
date: 2024-05-27
forum: Installation &amp; Upgrades
---

### Post by rjgoverna on 2024-05-27
Successfully upgraded from Mantic to Noble, however one niggly thing occurs now:

My install is LUKS encrypted. When I get prompted for the decryption password, that particular screen is at the wrong resolution (640x480?). After entereing the password it then resumes booting and jumps into the correct native resolution (1600x900).

I have managed to fix it by adding **GRUB_GFXMODE=1600x900** and **GRUB_GFXPAYLOAD_LINUX=keep** to /etc/default/grub

I am still wondering though why is this happening? It was booting straight to the native res under Mantic so what changed? Although the above fixes it, I can still see a clear flashing screen where it now starts at 1600x900, then screen goes black for 1 sec, then back to 1600x900 whereas in Mantic it just straight booted at the native res and kept it throughout the boot phase.

Any tips will be appreciated. Thanks.

---

### Post by MAFoElffen on 2024-05-27
For one: The kernel version. (6.5 vs 6.8)

In that part of the boot process, the machine's graphics are controlled by the BIOS and kernel KMS hints, which you resolved by editing the /etc/default/grub file (correctly). There a few ways to pass that from Grub, which basically do the same thing.

If you read the first post in my Graphics Resolution sticky in my signature line, in this section, I explain that. It's been the same basic concepts since around 2011.

Once you log into the Desktop, then the Linux Graphics Layer initializes, and uses graphics drivers for the specific GPU. So there is a hand-off between.

---

### Post by rjgoverna on 2024-05-27
> **MAFoElffen said:**
> For one: The kernel version. (6.5 vs 6.8)

oh right, good point.

> **MAFoElffen said:**
> If you read the first post in my Graphics Resolution sticky in my signature line, in this section, I explain that.

Was literally reading it just now, great stuff! Cheers!

---

