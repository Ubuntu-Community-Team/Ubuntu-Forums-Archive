---
title: "Constant acpi errors in logs"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by wizardks on 2010-07-27
New install of 10.04 on Compaq sr1711nx and when I check the logs I get the following continuously.  I have done some searching without much luck and the only reference to GPE that I can find is related to Palm OS. Any ideas would be welcome.  In addition, occasionally a program window 9ie Firefox) will go nuts displaying random lines etc.


 86.643235] ACPI Exception: AE_LIMIT, Returned by Handler for [SystemIO] (20090903/evregion-424)

 [   86.643249] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L09] (Node f700fdb0), AE_LIMIT

 kernel: [   86.643309] ACPI Exception: AE_LIMIT, while evaluating GPE method [_L09] (20090903/evgpe-568)

: [   88.406142] ACPI Error: Illegal I/O port address/length above 64K: 0x00400020/4 (20090903/hwvalid-154)

: [   88.406158] ACPI Exception: AE_LIMIT, Returned by Handler for [SystemIO] (20090903/evregion-424)

 [   88.406171] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L09] (Node f700fdb0), AE_LIMIT

: [   88.406223] ACPI Exception: AE_LIMIT, while evaluating GPE method [_L09] (20090903/evgpe-568)

: [   88.425561] ACPI Error: Illegal I/O port address/length above 64K: 0x00400020/4 (20090903/hwvalid-154)

 [   88.425577] ACPI Exception: AE_LIMIT, Returned by Handler for [SystemIO] (20090903/evregion-424)

: [   88.425588] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L09] (Node f700fdb0), AE_LIMIT

l: [   88.425638] ACPI Exception: AE_LIMIT, while evaluating GPE method [_L09] (20090903/evgpe-568)

---

### Post by Clever_Username on 2010-07-29
I came across [this]("http://art.ubuntuforums.org/showthread.php?p=8700833") thread that might be useful to you. Hope it helps

---

### Post by P4man on 2010-07-29
Try to update your BIOS?

---

