---
title: "System won't wake from sleep after upgrade to 17.04"
date: 2017-04-30
forum: Installation &amp; Upgrades
---

### Post by studipity on 2017-04-30
I'm not sure if this happens 100% of the time, but since upgrading to 17.04 yesterday, my computer has gone to sleep a few times after 30 minutes inactivity (as configured), but it refuses to wake again following keyboard press, mouse move, or power button press. 

My only recourse is to hold the power button in for 4-5 seconds until the system halts, then restart.

I never had a problem with this on 16.04 or 16.10, and I've made no changes to my hardware as part of upgrading to 17.10.

Not sure what additional information you might need me to provide to help diagnose this, but let me know and I'll include it.

---

### Post by Xian on 2017-04-30
What graphics card do you have?

```
$ [COLOR=#212529][FONT=Inconsolata]lspci -v | less[/FONT][/COLOR]
```

---

### Post by studipity on 2017-04-30
```

01:00.0 VGA compatible controller: NVIDIA Corporation GM206 [GeForce GTX 960] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: Gigabyte Technology Co., Ltd GM206 [GeForce GTX 960]
        Flags: bus master, fast devsel, latency 0, IRQ 128
        Memory at de000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at d0000000 (64-bit, prefetchable) [size=32M]
        I/O ports at e000 [size=128]
        Expansion ROM at 000c0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: nouveau
        Kernel modules: nvidiafb, nouveau

```

---

### Post by studipity on 2017-04-30
Didn't realise 'Capabilities' access was denied without sudo - here is the full output:

```

01:00.0 VGA compatible controller: NVIDIA Corporation GM206 [GeForce GTX 960] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: Gigabyte Technology Co., Ltd GM206 [GeForce GTX 960]
        Flags: bus master, fast devsel, latency 0, IRQ 128
        Memory at de000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at d0000000 (64-bit, prefetchable) [size=32M]
        I/O ports at e000 [size=128]
        Expansion ROM at 000c0000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [78] Express Legacy Endpoint, MSI 00
        Capabilities: [100] Virtual Channel
        Capabilities: [258] L1 PM Substates
        Capabilities: [128] Power Budgeting <?>
        Capabilities: [420] Advanced Error Reporting
        Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
        Capabilities: [900] #19
        Kernel driver in use: nouveau
        Kernel modules: nvidiafb, nouveau

```

---

### Post by studipity on 2017-05-05
Does anyone have any thoughts on this? This is becoming really annoying...

---

