---
title: "Ubuntu Core 20 on a old machine"
date: 2021-06-01
forum: Installation &amp; Upgrades
---

### Post by mlgupta on 2021-06-01
I am trying to install UC20 on an old machine. The machine has no UEFI capability. CPU is Intel 2160@1.80 GHz with 2GB RAM. 

I installed UC20 using dd on this machine. However,  before grub I get a message "error: invalid signature". Then I see a grub kernel selection menu, and any selection leads to "error: invalid signature..." message and back to the grub menu screen.


The behavior is the same when I tried to run UC20 in a Virtualbox. However, the VM on Virtualbox boots up as soon as I enable EFI.

This is what I see when I look at the partition information for the disk I created using dd.

------------------
[FONT=courier new]Device     Start     End Sectors  Size Type
/dev/sdb1   2048    4095    2048    1M BIOS boot
/dev/sdb2   4096 2461695 2457600  1.2G EFI System[/FONT]

------------------

I searched and so far could not find any solution. Also unsuccessfully tried building different UC20 image using ubuntu image with different combination of pc snaps with the hope that some pc-gadget snap would support legacy BIOS boot.

Ubuntu Core 18 runs fine on this machine.

Is it not possible to run UC20 on non-UEFI system?

Would appreciate help in this regard.

---

### Post by him610 on 2021-06-01
> The machine has no UEFI capability.
It is probably a 32 bit machine. Unless I am mistaken, Ubuntu 20.04 is 64 bit only.
You might want to read this article, [https://itsfoss.com/32-bit-linux-distributions/]("https://itsfoss.com/32-bit-linux-distributions/")

---

### Post by mlgupta on 2021-06-02
It is a 64 bit machine. Here is the output from uname

root@pystro-01-01:~# uname -a
Linux pystro-01-01 4.15.0-144-generic #148-Ubuntu SMP Sat May 8 02:33:43 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by him610 on 2021-06-05
Please show the results, between the code tags, of .....
```

inxi -MCSxz

```

---

### Post by mlgupta on 2021-06-06
Currently, the machine is running Ubuntu Core 18. Unfortunately, could not find a snap for inxi on snapcraft.io.

---

### Post by ajgreeny on 2021-06-06
Try ***sudo apt install inxi***; there's no  need for a snap!

---

### Post by CatKiller on 2021-06-06
> **ajgreeny said:**
> Try ***sudo apt install inxi***; there's no  need for a snap!

Ubuntu Core only uses snaps.

---

### Post by ajgreeny on 2021-06-07
> **CatKiller said:**
> Ubuntu Core only uses snaps.
Oh boy!

That just shows how little I knew about Ubuntu-Core; I had assumed that it was simply a "lite" version of Ubuntu.
Sorry about that: I should have checked first.

---

