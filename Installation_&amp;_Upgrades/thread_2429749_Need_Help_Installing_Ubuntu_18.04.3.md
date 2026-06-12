---
title: "Need Help Installing Ubuntu 18.04.3"
date: 2019-10-22
forum: Installation &amp; Upgrades
---

### Post by jasperstrange on 2019-10-22
Hey Ubuntu Community,

I am not the most knowledgeable in this field, and I am having a tough time installing Ubuntu on my computer, where I partitioned the disk. I followed this [guide]("https://www.tecmint.com/install-ubuntu-alongside-with-windows/") and got to the point where I can "try ubuntu without installing" or "install Ubuntu".

I spent a couple hours reading about ways to get rid of the errors that pop-up, and have solved a couple but I've hit a wall.

Error Message: 

```

[ 11.614739] Couldn't get size: 0x80000000000000e
[ 11.791712] ACPI BIOS Error (bug): Could not resolve [\_SB.PEGO._PRT.ARO
[ 11.791747] ACPI Error: Method parse/execution failed \_SB.PCIO.PEGO._PRT, AE
[ 11.791888] ACPI BIOS Error (bug): Could not resolve [\_SB.PEGO._PRT.ARO
[ 11.791935] ACPI Error: Method parse/execution failed \_SB.PCIO.PEGO._PRT, AE
[ 11.792174] ACPI BIOS Error (bug): Could Not resolve [\_SB.PEGO._PRT.ARO
2], AE_NOT_FOUND (20181213/psargs-330)
[ 11.792186] ACPI Error: Method parse/execution failed \_SB.PCIO.PEGO._PRT, AE
_NOT_FOUND (20181213/psargs-531)
[ 11.930914] nouveau 0000:01:00.0: bus: MMIO read of 000000000 FAULT at 022554
[ IBUS ]
[ 11.941837] nouveau 0000:01:00.0: bus: MMIO read of 000000000 FAULT at 10ac08 [ IBUS ]

BusyBox v1.27.2 (Ubuntu 1:1.27.2-2ubuntu3.2) built-in shell (ash)
Enter 'help'for a list of built-in comands.

(initramfs) mount: mounting /cow on /root failed: Invalid argument
overlay mount failed

```

My computer is a Lenovo Y50-70
-nvidia GTX 960M
-Intel(R) Core(TM) i7-4720HQ CPU @2.60GHz

I was able to get rid of some error messages with:

```

nouveau.modeset=0

```


But i have yet to be able to actually use Ubuntu.


Thanks in Advance for any help

---

### Post by wildmanne39 on 2019-10-22
Thread closed. Please do not post duplicates, it dilutes community effort.

---

