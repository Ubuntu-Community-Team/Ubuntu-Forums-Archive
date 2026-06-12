---
title: "Two error messages on ubuntu mate 16.04 LTS"
date: 2017-03-12
forum: Installation &amp; Upgrades
---

### Post by jotacebp on 2017-03-12
Hi.
I have an HP 250 g5 laptop. At startup two error messages can be read.
Anyone knows how to solve this?:confused:
Thanks

```
[ 3.676688] [drm] Replacing VGA console driver
[ 3.682286] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[ 3.682286] [drm] Driver supports precise vblank timestamp query.
[ 3.684881] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+memwns=io+mem
[ 3.696757] ACPI: Video Device [GFX0] (multi-head: yes rom: no post: no)
[ 3.697815] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[ 3.697963] [drm] Initialized i915 1.6.0 20160711 for 0000:00:02.0 on minor 0
**[ 3.744242] [drm:intel_dp_start_link_train [i915]] *ERROR* failed to train DP, aborting**

3.320585] ACPI: AC Adapter [ACAD] (on-line)
[ 3.320659] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:18/PNP0C0D:00/input/input0
[ 3.320678] ACPI: Lid Switch [LID0]
[ 3.320723] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[ 3.320725] ACPI: Power Button [PWRB]
[ 3.320764] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[ 3.320765] ACPI: Power Button [PWRF]
[ 3.320818] ACPI Error: [\_SB_.PCI0.LPCB.H_EC.ECWT] Namespace lookup failure, AE_NOT_FOUND (20160422/psargs-359)
[ 3.320822] ACPI Error: Method parse/execution failed [\_TZ.FN00._ON] (Node ffff9a8a1a1001e0), AE_NOT_FOUND (20160422/psparse-542)
[ 3.320829] acpi PNP0C0B:00: Failed to change power state to D0
[ 3.320855] ACPI Error: [\_SB_.PCI0.LPCB.H_EC.ECWT] Namespace lookup failure, AE_NOT_FOUND (20160422/psargs-359)
[ 3.320857] ACPI Error: Method parse/execution failed [\_TZ.FN00._ON] (Node ffff9a8a1a1001e0), AE_NOT_FOUND (20160422/psparse-542)
**[ 3.320862] acpi PNP0C0B:00: Failed to set initial power state**
[ 3.344216] acpi PNP0C0B:00: Cannot transition from (unknown) to D3hot
[ 3.344966] ACPI Error: [\_SB_.PCI0.LPCB.H_EC.ECRD] Namespace lookup failure, AE_NOT_FOUND (20160422/psargs-359)
[ 3.344971] ACPI Error: Method parse/execution failed [\_TZ.TZ00._TMP] (Node ffff9a8a1a106190), AE_NOT_FOUND (20160422/psparse-542)
[ 3.345064] ACPI Error: [\_SB_.PCI0.LPCB.H_EC.ECRD] Namespace lookup failure, AE_NOT_FOUND (20160422/psargs-359)
[ 3.345067] ACPI Error: Method parse/execution failed [\_TZ.TZ00._TMP] (Node ffff9a8a1a106190), AE_NOT_FOUND (20160422/psparse-542)
[ 3.345114] ACPI Error: [\_SB_.PCI0.LPCB.H_EC.ECRD] Namespace lookup failure, AE_NOT_FOUND (20160422/psargs-359)
[ 3.345116] ACPI Error: Method parse/execution failed [\_TZ.TZ01._TMP] (Node ffff9a8a1a106820), AE_NOT_FOUND (20160422/psparse-542)
[ 3.345155] ACPI Error: [\_SB_.PCI0.LPCB.H_EC.ECRD] Namespace lookup failure, AE_NOT_FOUND (20160422/psargs-359)
[ 3.345157] ACPI Error: Method parse/execution failed [\_TZ.TZ01._TMP] (Node ffff9a8a1a106820), AE_NOT_FOUND (20160422/psparse-542)
```

---

