---
title: "Clean install of Ubuntu on Dell latitude e6420"
date: 2016-03-16
forum: Installation &amp; Upgrades
---

### Post by azyaser on 2016-03-16
[h=2]Help in Ubuntu[/h][COLOR=#000000][INDENT]Hello

i am new to this forum and to Ubuntu too.  I clean installed Ubuntu 14.04 on a dell latitude e6420 on a new HD. This laptop had another HD with Win 7 before. I installed using UEFI and AHCI. Installation went with no errors until tried to boot after installation and got the error no boot drive detected. Tried with legacy instead and got same error too. 

Can an you please help?[/INDENT]
[/COLOR]

---

### Post by oldfred on 2016-03-16
Probably better to use UEFI.
How is is currently configured?
What CPU, how much RAM, and what video card/chip does your system have?

       But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

And what version of Ubuntu?

---

### Post by azyaser on 2016-03-16
Hello

here is the link to the report: http:/paste.ubuntu.com/15404282

itnis currently configured as UEFI and AHCI
CPU is: i5 Vpro 2520 2.5GHZ 64 bit 
Ram: 4096 MB at 1333 MHz
VGA: Intel HD

---

### Post by oldfred on 2016-03-16
Report says this:
>  SecureBoot maybe enabled. 


It cannot tell for sure. But if you have it on, turn it off, but  leave UEFI boot on, not BIOS/CSM/Legacy.

You do not have the secure boot versions of grub & kernel installed.

You could run the Boot-Repair fix, it says it will install the secure boot version of grub. And update to include /EFI/Boot as a backup or fallback boot method.
Then you could boot with UEFI secure boot on or off, but not with BIOS.

---

### Post by azyaser on 2016-03-16
Thanks for the reply but I searched all the BIOS looking for the secure boot option and couldn't find it. I will run the boot repair but shouldn't I know where this option first?

---

### Post by oldfred on 2016-03-18
Some systems do not call it UEFI secure boot.
They may call it Windows and "Other".
And even those with Windows 7 in UEFI mode have to use "Other" as 7 does not support secure boot.

---

