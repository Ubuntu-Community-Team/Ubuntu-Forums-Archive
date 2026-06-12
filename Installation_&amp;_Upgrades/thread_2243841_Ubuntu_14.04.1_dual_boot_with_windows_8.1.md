---
title: "Ubuntu 14.04.1 dual boot with windows 8.1"
date: 2014-09-11
forum: Installation &amp; Upgrades
---

### Post by Jack_Ditchburn on 2014-09-11
Hello all,

I have just installed ubuntu 14.04.1 on an asus n550lf laptop, dual booted (I wish) with windows 8.1.

The install seemed to go without a hitch, but when I rebooted all I got was windows.  Grub did not appear, and on accessing the BIOS screen it does not appear in the boot options screen.

In order to install Ubuntu I turned off "fast boot" and "secure boot", and turned on "CSM", in the BIOS (not the correct term I know).

I have tried booting with all these turned on, and all turned off, and I can't see Ubuntu or the grub menu at all.  Not sure how to proceed now.

I am wondering if I should just wipe out windows and install Ubuntu as the sole operating system.  Are there any issues doing this with EUFI hardware?

All comments welcome, and thanks in advance,

Jackplug

---

### Post by oldfred on 2014-09-11
If you install Ubuntu in CSM/BIOS mode then you have to boot system in that mode. Then you will only get Ubuntu. 
UEFI and BIOS are not compatible, so once you start booting in one mode you cannot change, or you cannot use grub menu. 
But you should be able to use UEFI/BIOS or one time boot key if system auto switches. Some require you to turn on/off UEFI or CSM modes. CSM is automatically without secure boot.

A few systems only boot Windows. Users in those cases have had to recreate an efi folder with /efi/Windows/Boot with grub's efi file renamed to be the Windows efi file. Then system thinks it is booting Windows but really boots grub.

If you reinstall Ubuntu only use Something Else or it may just erase Windows. And best to have full backup of Windows as users find one app or game they cannot live without and want Windows back. Or later want to sell system but have to have Windows to sell it.

        Installation of Ubuntu 14.04 on ASUS N550JV (a Status Report)
[http://ubuntuforums.org/showthread.php?t=2208852](http://ubuntuforums.org/showthread.php?t=2208852)
[http://ubuntuforums.org/showthread.php?t=2184383](http://ubuntuforums.org/showthread.php?t=2184383)

---

### Post by Jack_Ditchburn on 2014-09-12
OldFred,

Thanks for the reply. 

My problem is that I never see the grub menu, and grub does not appear as an option in the boot order screen in setup and so can not be chosen for booting.

I have repaired grub using a live CD (Ubuntu 14.04) and the instructions from a thread in this forum.  Again all seemed to go according to plan, but I am still left with the situation above.

Regards

Jackplug:confused:

---

### Post by oldfred on 2014-09-12
You will not normally get grub menu.

You only have Ubuntu installed in BIOS/CSM boot mode and cannot boot Windows from its menu. So with only one entry it auto boots that one entry. If you need menu to boot recovery mode or add temporary boot parameters you have to hold shift key from BIOS until menu appears. With UEFI you use escape key not shift key.

But to boot in BIOS mode you either have to turn off UEFI and maybe separately turn on CSM/BIOS/Legacy boot mode. Some let you boot directly using one time boot key, often f12, some f10 check your manual.

---

