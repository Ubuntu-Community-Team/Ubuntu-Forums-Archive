---
title: "unknown error"
date: 2024-03-14
forum: Installation &amp; Upgrades
---

### Post by juanrendon12 on 2024-03-14
hello everyone, I am experiencing an error that sometimes when I turn on the computer stays on black screen, or starts but many errors appear but I do not know, this started when I installed a hdd and partitioned half for ubuntu and half for windows, in ubuntu appeared mounted in a folder and did many things to appear mounted as a normal drive (according to me), since that began the error, and windows leads me to repair the computer, I recommend that I recommend considering that I know little linux.

```

journalctl -b -p err
mar 14 08:57:02 rendon-HP-Laptop-14-ck0xxx kernel: x86/cpu: SGX disabled by BIOS.
mar 14 08:57:02 rendon-HP-Laptop-14-ck0xxx kernel: ACPI BIOS Error (bug): Failure creating named object [\_GPE._L72], AE_ALREADY_EXIST>
mar 14 08:57:02 rendon-HP-Laptop-14-ck0xxx kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20230331/psobject-220)
mar 14 08:57:02 rendon-HP-Laptop-14-ck0xxx kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.AWAC], AE_ALREADY_EXISTS>
mar 14 08:57:02 rendon-HP-Laptop-14-ck0xxx kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20230331/psobject-220)
mar 14 08:58:32 rendon-HP-Laptop-14-ck0xxx systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-12345678\x2d90ab\x2dcdef\x2d12>
mar 14 08:58:33 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: src/adapter.c:reset_adv_monitors_complete() Failed to reset Adv Monitors: >
mar 14 08:58:33 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: Failed to clear UUIDs: Failed (0x03)
mar 14 08:58:33 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: Failed to add UUID: Failed (0x03)
mar 14 08:58:33 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: Failed to add UUID: Failed (0x03)
mar 14 08:58:33 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: Failed to add UUID: Failed (0x03)
mar 14 08:58:33 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: Failed to set mode: Failed (0x03)
mar 14 08:58:33 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: Failed to add UUID: Failed (0x03)
mar 14 08:58:33 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: Failed to add UUID: Failed (0x03)
mar 14 08:58:33 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: Failed to add UUID: Failed (0x03)
mar 14 08:58:37 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: Failed to add UUID: Failed (0x03)
mar 14 08:58:37 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: Failed to add UUID: Failed (0x03)
mar 14 08:58:37 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: Failed to add UUID: Failed (0x03)
mar 14 08:58:37 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: Failed to add UUID: Failed (0x03)
mar 14 08:58:37 rendon-HP-Laptop-14-ck0xxx canonical-livepatch.canonical-livepatchd[1032]: The platform Ubuntu 23.10 is not supported.>
mar 14 08:58:38 rendon-HP-Laptop-14-ck0xxx canonical-livepatch.canonical-livepatchd[1374]: The platform Ubuntu 23.10 is not supported.>
mar 14 08:58:38 rendon-HP-Laptop-14-ck0xxx canonical-livepatch.canonical-livepatchd[1425]: The platform Ubuntu 23.10 is not supported.>
mar 14 08:58:38 rendon-HP-Laptop-14-ck0xxx canonical-livepatch.canonical-livepatchd[1467]: The platform Ubuntu 23.10 is not supported.>
mar 14 08:58:39 rendon-HP-Laptop-14-ck0xxx canonical-livepatch.canonical-livepatchd[1520]: The platform Ubuntu 23.10 is not supported.>
mar 14 08:58:39 rendon-HP-Laptop-14-ck0xxx systemd[1]: Failed to start snap.canonical-livepatch.canonical-livepatchd.service - Service>
mar 14 08:59:01 rendon-HP-Laptop-14-ck0xxx gdm-password][1929]: gkr-pam: unable to locate daemon control file
mar 14 08:59:02 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: Failed to remove UUID: Failed (0x03)
mar 14 08:59:02 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: Failed to remove UUID: Failed (0x03)
mar 14 08:59:02 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: Failed to remove UUID: Failed (0x03)
mar 14 08:59:02 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: Failed to remove UUID: Failed (0x03)
mar 14 08:59:02 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: Failed to add UUID: Failed (0x03)
mar 14 08:59:02 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: Failed to add UUID: Failed (0x03)
mar 14 08:59:02 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: Failed to add UUID: Failed (0x03)
mar 14 08:59:02 rendon-HP-Laptop-14-ck0xxx bluetoothd[852]: Failed to add UUID: Failed (0x03)
mar 14 08:59:03 rendon-HP-Laptop-14-ck0xxx systemd[1941]: Failed to start app-gnome-gnome\x2dkeyring\x2dsecrets-2164.scope - Applicati>
mar 14 08:59:35 rendon-HP-Laptop-14-ck0xxx systemd[1]: Failed to start NetworkManager-wait-online.service - Network Manager Wait Onlin>
rendon@rendon-HP-Laptop-14-ck0xxx:~$ 

```

this error appears when shutting down:
```

[FAILED] Failed unmounting run-user-1000.mount - /run/user/1000.

```

by turning this on:
```

8.090063] x86/cpu: SGX disabled by BIOS. us.


0.160107] ACPI BIOS Error (bug): Failure creating named object [V_GPE. 172]


AE ALREADY EXISTS (20230331/dswload2-326)


0.160126] ACPI Error: AE ALREADY_EXISTS, During name lookup/catalog (282303 31/psobject-220) [ 0.160142] ACPI BIOS Error (bug): Failure creating named object [SB.ANAC),


AE ALREADY EXISTS (20230331/dswload2-326) 0.160153] ACPI Error: AE ALREADY EXISTS, During name lookup/catalog (292383 31/psobject-220)


/dev/sda5: clean, 505455/17080320 files, 13133505/68320512 blocks You are in emergency mode. After logging in, type "Journalctl-xb" to view system logs, "systemctl reboot" to reboot, "systemctl default" or "exit"


to boot into default mode.


Pulse Enter para mantenimiento (o pulse Control-D para continuar):

```

if you need more information please let me know.  
_

---

