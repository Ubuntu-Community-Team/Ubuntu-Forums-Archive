---
title: "Question about testing"
date: 2009-09-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sashin on 2009-09-27
I get errors apart from the norm, after the "skipped firefox" error. Is there a way to get the text and report it?

---

### Post by ricsi-pontaz on 2009-09-27
> **Sashin said:**
> I get errors apart from the norm, after the "skipped firefox" error. Is there a way to get the text and report it?

Got a thread for this error:
[http://ubuntuforums.org/showthread.php?t=1273556](http://ubuntuforums.org/showthread.php?t=1273556)

---

### Post by Sashin on 2009-09-27
Its not that error, its a completely different error that's completely different and I think its unique to me, since its only on one particular computer and it says to report it.

---

### Post by PhoHammer on 2009-09-27
I get an unknown BIOS error during bootup, is that what your are talking about?

---

### Post by cariboo on 2009-09-27
Does your error message look someting like this?

```
dmesg | grep k8
[    0.539585] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (2 cpu cores) (version 2.20.00)
[    0.539603] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    0.539604] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[   12.308424] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
```

---

### Post by guillelo11 on 2009-09-27
> **cariboo907 said:**
> Does your error message look someting like this?

```
dmesg | grep k8
[    0.539585] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (2 cpu cores) (version 2.20.00)
[    0.539603] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    0.539604] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[   12.308424] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
```

I've this error

---

### Post by Sashin on 2009-09-27
Something to do with the acer bios. "Acer hdf". And it says "please report this problem.

---

### Post by buzzmandt on 2009-09-27
something like this?
```
buzzmandt@buzzmandt-laptop:~$ dmesg | grep hdf
[   20.146844] acerhdf: Acer Aspire One Fan driver, v.0.5.16
[   20.146849] acerhdf: unknown (unsupported) BIOS version Acer, inc./Aspire 3680     /v1.3505, please report, aborting!

```

---

### Post by Sashin on 2009-09-28
something like that.

---

