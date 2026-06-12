---
title: "Dual Boot Ubuntu 12.04 and Windows 7 problem"
date: 2013-08-14
forum: Installation &amp; Upgrades
---

### Post by yuhuhack on 2013-08-14
Hello!
I succesfully intalled windows 7 and Ubuntu 12.04 in uefi mode,they both will boot and work perfectly,but the problem is when i power on the computer it will automaticaly boot to Windows 7,so to get to the Grub menu i have to Press F9 then choose Ubuntu from device boot list and after that the grub appears and again choose Ubuntu from the list...how can i set it to boot by default to Grub and not to Windows boot manager? also here is a link with bootinfo from BootRepair :  [http://paste.ubuntu.com/5986012/](http://paste.ubuntu.com/5986012/) if someone can help me that would be grate ,i looked for similar threads but none of them seems to have an answer..

---

### Post by Boab1993 on 2013-08-14
Go into boot-repair and use the recommend-repair option.

I think that would do the trick.

Could be wrong, i just install PLOP everytime.

---

### Post by oldfred on 2013-08-14
Not sure you have Ubuntu set as first to boot.

 At line 442 in report:
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 3003,3001,2001,2002,2003
Boot0001* Ubuntu
       
 Boot0003* Windows Boot Manager
 Boot3001* Internal Hard Disk or Solid State Disk



That says you booted with 0001 but 3003 is default. Which looks more like a BIOS boot since it is just a drive not a name.

Window repairs may also reset defaults and you just have to go into UEFI and change it.

---

### Post by yuhuhack on 2013-08-14
Well i allready tried this with no luck ..

---

### Post by yuhuhack on 2013-08-14
> **oldfred said:**
> Not sure you have Ubuntu set as first to boot.

 At line 442 in report:
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 3003,3001,2001,2002,2003
Boot0001* Ubuntu
       
 Boot0003* Windows Boot Manager
 Boot3001* Internal Hard Disk or Solid State Disk



That says you booted with 0001 but 3003 is default. Which looks more like a BIOS boot since it is just a drive not a name.

Window repairs may also reset defaults and you just have to go into UEFI and change it.

I think that window repairs may be the cause....About the ``BIOS`` i`m on a HP pavilion g6 notebook with Insyde F26 bios,when i installed Ubuntu and Windows i selected ``USB *** -EFI `` ..
go into UEFI and change what?..

---

### Post by oldfred on 2013-08-14
Someone else with a different model HP, so it may not apply, said that they really only had two settings. UEFI on really seemed to mean secure boot. And CSM on was really to boot either UEFI or CSM. It seems that system in CSM mode looks first for efi partition and if boot files found will boot in UEFI mode, if not found it looks in MBR to boot in BIOS mode.

So it may be a combination of settings for boot mode and then which of the listed boot options to set as default. Some may not work in one setting or the other?

---

### Post by yuhuhack on 2013-08-15
think i`ll just downgrade the bios ,change partition table of the HDD to mbr and do a legacy (Bios) install...thanks for reply..

---

