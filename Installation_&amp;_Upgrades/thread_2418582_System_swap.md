---
title: "System swap"
date: 2019-05-08
forum: Installation &amp; Upgrades
---

### Post by zkab on 2019-05-08
I have Intel NUC with Xfce 18.04.2 LTS installed at Samsung SSD 960 EVO 250GB (the only disk in my system).
Now I want to swap the Intel NUC to ASRock DeskMini 310 Series.
I don't want to install Xfce from scratch but just plug in the Samsung SSD 960 EVO 250GB & current memory cards into ASRock.
According to the specification I can use the same memory cards but I will use a faster CPU in ASRock that I have in NUC.
Can that be done ?
What changes do I have to do before the swap?

---

### Post by Autodave on 2019-05-08
Will it work the way you want?  Probably.  I have swapped HDs from one machine to another quite often with good results.  IF you have installed any drivers, you may want to uninstall them first.  For instance, a video driver or sound card driver assuming that neither will be installed in the new system.

My best advice is to simply try it first: if it doesn't work, then swap them back and come back here with specifics on what didn't work correctly.

---

### Post by oldfred on 2019-05-08
Many systems just work.
Often issues are video card/chip or Internet Wi-Fi chips & drivers.
But those are both using Intel internal video? Not sure about wireless.

If UEFI install, you have to add UEFI entries to UEFI on new system. 
Often easiest by just doing a full reinstall of grub with Boot-Repair or manually, but you probably can just use efibootmgr to add an entry. 

It may let you boot initially from UEFI using the hard drive or fallback entry with is in /EFI/Boot/bootx64.efi. Most UEFI have a hard drive entry.
If it lets you boot, you can just reinstall grub from your install to create ubuntu entries in UEFI to use the standard /EFI/ubuntu/shimx64.efi entries. Not sudo update-grub which just updates grub menus, but a full reinstall which internally uses efibootmgr to create UEFI entries.

---

### Post by zkab on 2019-05-08
OK ... sounds it will probably work.
I will give it a try and see what happens after the swap ...
If problems occur I'll come back ... thanks

---

### Post by zkab on 2019-05-13
I stumbled across open source Aptik that should do the work ... anyone who has any experience from Aptik?

---

