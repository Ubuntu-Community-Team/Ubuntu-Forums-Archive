---
title: "Fresh first-time 22.04 install, hangs on boot, ACPI errors"
date: 2022-08-17
forum: Installation &amp; Upgrades
---

### Post by stevenanewton on 2022-08-17
Hi all,
I looked for a "howto" on posting requests for help, but couldn't find one.  Forgive me if I'm not doing this right.

Motherboard is an ASRock H310M-HDV from about five years ago, 9th-gen i7 processor, currently running Win11.

I installed a 2nd SSD for Ubuntu (actually Kubuntu), doing a clean install from USB.

Try Kubuntu option from USB drive works fine.

Install seemed to go fine.

First reboot after install, I get these errors, and the machine freezes:
[    0.142805] x86/cpu: SGX disabled by BIOS.
[    0.530601] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PR00._CPC], AE_NOT_FOUND (20210730/psargs-330)
[    0.530617] ACPI Error: Aborting method \_SB.PRO1._CPC due to previous error (AE_NOT_FOUND) (20210730/psparse-529)
[    0.530666] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PR00._CPC], AE_NOT_FOUND (20210730/psargs-330)
[    0.530678] ACPI Error: Aborting method \_SB.PRO2._CPC due to previous error (AE_NOT_FOUND) (20210730/psparse-529)
[    0.530725] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PR00._CPC], AE_NOT_FOUND (20210730/psargs-330)
[    0.530736] ACPI Error: Aborting method \_SB.PRO3._CPC due to previous error (AE_NOT_FOUND) (20210730/psparse-529)
[    0.530784] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PR00._CPC], AE_NOT_FOUND (20210730/psargs-330)
[    0.530795] ACPI Error: Aborting method \_SB.PRO4._CPC due to previous error (AE_NOT_FOUND) (20210730/psparse-529)
[    0.530842] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PR00._CPC], AE_NOT_FOUND (20210730/psargs-330)
[    0.530852] ACPI Error: Aborting method \_SB.PRO5._CPC due to previous error (AE_NOT_FOUND) (20210730/psparse-529)

I upgraded to the most recent bios.  Win11 still boots fine.

Thanks in advance for any help you can give me.

---

### Post by ActionParsnip on 2022-08-17
[https://www.asrock.com/mb/intel/h310m-hdv/index.asp#BIOS](https://www.asrock.com/mb/intel/h310m-hdv/index.asp#BIOS)

Do you have the latest BIOS?

---

### Post by stevenanewton on 2022-08-17
I was one rev behind, so I updated to latest.  No change.

So I re-installed, using minimal install, no updates during install, no additional software and drivers.  And it booted up.  ACPI errors were still there, but it booted and I got to the desktop.  I'm running updates now to see if it stops working.

Thanks, I guess we can call this solved.  If I have a problem after updates, I assume there's a bug in the latest kernel that I'll need to monitor.

---

