---
title: "repair dual boot and MBR issues"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by neukuk on 2009-12-23
I had XP home running fine, then installed ubuntu 9.10 on the same hd and all ran fine until I uninstalled a free windows cleaner program.  I then had the dreaded hal.dll missing problem. I have copied the hal.dll file across and got nowhere.

If I do a **repair** installation from the XP CD ( not a reinstallation, nor from recovery console, just straight repair from my XP installation CD )  does this change my **MBR** ? 
Love using Ubuntu, but I want to go on playing my Windows games and using my Windows photoediting progrms
Thanks gang
:confused:

---

### Post by oldfred on 2009-12-23
Reinstalling grub is not that difficult as long as you have the liveCD that you installed from. You do need to know if you have grub legacy from an upgrade, or grub2 from a new install.

Grub version:
grub-install -v
Ubuntu version:
lsb_release -a

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I do not know if you have to run the fixmbr command that overwrites grub to run the other commands:
FIXMBR  C:
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
BOOTCFG  /rebuild


Another way from within ubuntu:
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

---

### Post by neukuk on 2009-12-23
Thanks oldfred
I ll go off and try that tomorrow
I take it from yr reply that repairing XP does indeed change the MBR

:P

GNU GRUB 1.97~beta4 is the grub version I have
I think thats grub2 ?

lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic

---

### Post by phillw on 2009-12-23
> **neukuk said:**
> Thanks oldfred
I ll go off and try that tomorrow
I take it from yr reply that repairing XP does indeed change the MBR

:P

GNU GRUB 1.97~beta4 is the grub version I have
I think thats grub2 ?

lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic

Yeah, recovering XP will reset the MBR to Win. Once Win is happily booting, re-do the grub install (yes, grub 1.97beta = grub2)

Regards,

Phill.

---

### Post by neukuk on 2009-12-24
Thanks Phil
I will gather my courage and tackle it
hate the possiblity of being without a PC and or having to resinstall ubuntu, just started figuring out how things work there.

patrick:P

---

