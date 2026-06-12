---
title: "AMD Radeon HD 7870 XT not working, only black screen and cursor"
date: 2019-07-14
forum: Installation &amp; Upgrades
---

### Post by klode82 on 2019-07-14
[SIZE=2][FONT=arial]I've installed Kubuntu 18.04 in order to use my Radeon HD 7870 XT. I've used AMD Gpu Official driver, downloaded from AMD website.

The driver is [COLOR=#FF5454][B]amdgpu-pro-19.20-812932-ubuntu-18.04.
[/B][/COLOR]
After using the command:

```

amdgpu-pro-install.sh --opencl=legacy

```

After installation I've got black screen with cursor. I can move it, but nothing else.


I've used nomodeset on GRUB startup command, but nothing.

On dmesg with the command:
```

dmesg | grep 'amd'

```

I obtain:

```

[COLOR=#000000][    0.000000] Linux version 4.18.0-25-generic (buildd@lgw01-[/COLOR][COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]64-033) (gcc version 7.4.0 (Ubuntu 7.4.0-1ubuntu1~18.04.1)) #26~18.04.1-Ubuntu SMP Thu Jun 27 07:28:31 UTC 2019 (Ubuntu 4.18.0-25.26~18.04.1-generic 4.18.20)[/COLOR]
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.18.0-25-generic root=UUID=08eb4ae9-b64c-4c8e-aadd-1f4cb9028a91 ro radeon.si_support=0 radeon.cik_support=0 [COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]gpu.si_support=1 [/COLOR][COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]gpu.cik_support=1 [/COLOR][COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]gpu.dc=1 [/COLOR][COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]gpu.dpm=1 [/COLOR][COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]gpu.modeset=1 splash quiet nomodeset[/COLOR]
 vt.handoff=1                                                                                                                                                                                                                                                                
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.18.0-25-generic root=UUID=08eb4ae9-b64c-4c8e-aadd-1f4cb9028a91 ro radeon.si_support=0 radeon.cik_support=0 [COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]gpu.si_support=1 [/COLOR][COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]gpu.cik_support=1 [/COLOR][COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]gpu.dc=1 [/COLOR][COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]gpu.dpm=1 [/COLOR][COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]gpu.modeset=1 splash quiet no[/COLOR]
modeset vt.handoff=1                                                                                                                                                                                                                                                         
[    1.596361] [COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]kcl: loading out-of-tree module taints kernel.[/COLOR]
[    1.596390] [COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]kcl: module verification failed: signature and/or required key missing - tainting kernel[/COLOR]
[    1.731327] [COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]gpu: unknown parameter 'modeset' ignored[/COLOR]
[    1.731707] [drm:[COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]gpu_init [[/COLOR][COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]gpu]] *ERROR* VGACON disables [/COLOR][COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]gpu kernel modesetting.[/COLOR]
[   31.363030] [COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]gpu: unknown parameter 'modeset' ignored[/COLOR]
[   31.363456] [drm:[COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]gpu_init [[/COLOR][COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]gpu]] *ERROR* VGACON disables [/COLOR][COLOR=#FF5454]**amd**[/COLOR][COLOR=#000000]gpu kernel modesetting.[/COLOR]

```

[/FONT][/SIZE]I've made a new installation (from 19.04 to 18.04) because many people says the AMD driver are compatible with 18.04, and not for 19.04. How can I use new driver and how can I use the kubuntu desktop?

---

