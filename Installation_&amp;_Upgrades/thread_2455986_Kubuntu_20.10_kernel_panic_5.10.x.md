---
title: "Kubuntu 20.10 kernel panic 5.10.x"
date: 2021-01-01
forum: Installation &amp; Upgrades
---

### Post by ravendark2 on 2021-01-01
Hello, 

I am experiencing some random flickering issues with the current [FONT=monospace][COLOR=#000000]5.8.0-33-generic[/COLOR][/FONT] kernel which is due to my MSI Radeon RX 5600XT Gaming X.
Some times the system boots fine, some times it boots displaying some errors and flickering appears.
```

[FONT=monospace][COLOR=#000000]kernel: [   25.191874] amdgpu: Msg issuing pre-check failed and SMU may be not in the right state!
[/COLOR][/FONT]
[FONT=monospace][FONT=monospace][COLOR=#000000]kernel: [    8.624468] EDAC [/COLOR][COLOR=#ffffff]amd[/COLOR][COLOR=#000000]64: Error: F0 not found, device 0x1650 (broken BIOS?)[/COLOR]
[/FONT] [/FONT]
```

So, I tried installing the 5.10.x precompiled kernels and all of them result in a kernel panic.

I used the kernel utility build scripts, compiled and installed the 5.10.4 kernel with the same result.

Anyone experiencing the same?

---

