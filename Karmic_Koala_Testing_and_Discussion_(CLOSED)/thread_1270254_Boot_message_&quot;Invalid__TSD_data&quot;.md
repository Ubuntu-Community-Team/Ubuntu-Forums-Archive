---
title: "Boot message: &quot;Invalid _TSD data&quot;"
date: 2009-09-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cyberkilla on 2009-09-19
For the past two Ubuntu releases, I have been getting a series of error messages along the lines of:

"Invalid _TSD data"

I am running a Sony Vaio, and I'm already quite aware of the ACPI problems for this hardware.

It doesn't actually break anything; my system boots fine. A couple of things, primarily screen brightness, are not implemented in the Vaio's ACPI (as far as I know). Perhaps this is the reason for the error.

Looking at this link: [http://forums.fedoraforum.org/showthread.php?t=225323](http://forums.fedoraforum.org/showthread.php?t=225323)
It seems someone else is having a similar issue. There are some logs from **HIS** system. Here is an excerpt:

```
ACPI Warning (nspredef-0940): \_PR_.CPU0._TSD: Return Package type mismatch at index 0 - found Integer, expected Package [20081204]
ACPI: Invalid _TSD data
ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
processor ACPI_CPU:00: registered as cooling_device0
ACPI: Processor [CPU0] (supports 8 throttling states)
ACPI: SSDT 7FEDC44C, 00DD (r1   Sony     VAIO 20070523 PTL  20050624)
ACPI: SSDT 7FEDC122, 0092 (r1   Sony     VAIO 20070523 PTL  20050624)
ACPI Warning (nspredef-0940): \_PR_.CPU1._TSD: Return Package type mismatch at index 0 - found Integer, expected Package [20081204]
ACPI: Invalid _TSD data
ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
processor ACPI_CPU:01: registered as cooling_device1
ACPI: Processor [CPU1] (supports 8 throttling states
```

AND

```
ACPI Warning (nspredef-0940): \_PR_.CPU0._PSD: Return Package type mismatch at index 0 - found Integer, expected Package [20081204]
ACPI: Invalid _PSD data
ACPI Warning (nspredef-0940): \_PR_.CPU1._PSD: Return Package type mismatch at index 0 - found Integer, expected Package [20081204]
ACPI: Invalid _PSD data

```

I am yet to debug this on my own system.

In truth, it doesn't seem to be a pressing concern, but I thought I would mention it regardless. Anybody else having similar issues?

EDIT:
According to some Intel ACPI specs, _TSD is related to cpu throttling. It seems to throttle the CPU fine, however.
I am not sure what _PSD is related to, however.

EDIT:
_PSD is related to "P-state coordination". It looks like both warnings are related to the ACPI and the CPU.

---

### Post by pwn on 2009-10-07
I have the same issue 'Invalid _TSD data' on a Sony Vaio AR590E. I can't change the brightness of the screen either but I'm used to it.

I've been looking for a way to get rid of that error message.

---

