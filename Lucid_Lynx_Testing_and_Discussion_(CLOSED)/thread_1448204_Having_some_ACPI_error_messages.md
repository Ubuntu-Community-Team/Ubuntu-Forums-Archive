---
title: "Having some ACPI error messages"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dusdus on 2010-04-06
Just started today. I've disables ACPI for a couple of days, just because I use my laptop as a desktop (seldom use of battery).
Today I got some weird messages about low memory (those messages are gone btw, don't ask me how, I don't know) and my eye fell on a lot of messages about ACPI.
Now, also after enabling ACPI, using "bum", I still get these messages:
```

laptux kernel: [    1.630171] ACPI Error (dswload-0781): [_T_0] Namespace lookup failure, AE_ALREADY_EXISTS
Apr  6 16:46:25 laptux kernel: [    1.630177] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20090903/psloop-230)
Apr  6 16:46:25 laptux kernel: [    1.630182] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.BAT1.UBIF] (Node ffff8800793280c0), AE_ALREADY_EXISTS
Apr  6 16:46:25 laptux kernel: [    1.630190] ACPI: Marking method UBIF as Serialized because of AE_ALREADY_EXISTS error
Apr  6 16:46:25 laptux kernel: [    1.630215] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.BAT1._BIF] (Node ffff880079328080), AE_ALREADY_EXISTS
Apr  6 16:46:25 laptux kernel: [    1.630222] ACPI: Marking method _BIF as Serialized because of AE_ALREADY_EXISTS error
Apr  6 16:46:25 laptux kernel: [    1.630249] ACPI Exception: AE_ALREADY_EXISTS, Evaluating _BIF (20090903/battery-363)
Apr  6 16:46:25 laptux kernel: [    1.632140] ACPI Error (psargs-0359): [_T_0] Namespace lookup failure, AE_NOT_FOUND
Apr  6 16:46:25 laptux kernel: [    1.632145] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.BAT1.UBIF] (Node ffff8800793280c0), AE_NOT_FOUND
Apr  6 16:46:25 laptux kernel: [    1.632174] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._Q09] (Node ffff880079333240), AE_NOT_FOUND
Apr  6 16:46:25 laptux kernel: [    1.650094] ACPI Warning for \_SB_.PCI0.SAT0.PRT0._GTF: Return type mismatch - found Integer, expected Buffer (20090903/nspredef-1006)

```


Does anyone recognize these messages? I can't find anything while searching...

---

### Post by dino99 on 2010-04-06
seems to conflict with bios settings

---

