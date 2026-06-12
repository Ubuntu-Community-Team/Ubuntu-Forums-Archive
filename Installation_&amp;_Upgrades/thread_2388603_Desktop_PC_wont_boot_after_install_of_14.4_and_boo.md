---
title: "Desktop PC wont boot after install of 14.4 and boot-repair"
date: 2018-04-05
forum: Installation &amp; Upgrades
---

### Post by harpaz on 2018-04-05
i have a desktop pc of about 5-7 years old with XP on it. With single HD on it. working fine.

i decided to wipe the disk and try to install ububtu on it. 
 
i tried to use the latest LTS ubuntu   version   16.04
 
when i run it on my pc using disk on key (live)  - it works fine 
i installed it on my pc while i requested to format my disk 

installation finished ok
 
boot from my computer - failed
 
i used the boot-repair tool   while bios was in UEFI mode 
but it does not help
 
the pc wont boot.   it works only while i use the live ubuntu
 
 
the boot info is here :  [http://paste.ubuntu.com/p/ckfK9925gx/](http://paste.ubuntu.com/p/ckfK9925gx/) 

 can  you help pls 
 
 
should  the boot mode in bios  should  be  set  to  auto   or UEFI  or legaci ?

---

### Post by TheFu on 2018-04-05
Most XP computers are not UEFI.  I suspect, but do not know, that early UEFI implementations might not have considered Linux at all.  I know that some HP computers require manually renaming the EFI boot file to appear like Windows to get Linux booting.

Regardless, if you install UEFI during the installation, then the BIOS must support and be set to use UEFI for booting. 
If you install using legacy BIOS during installation, then the BIOS must also be set to boot with legacy BIOS.

If you google for Ubuntu + the specific make/model of the computer, specific instructions may be found.  

16.04 really should be used for fresh installs, at least until 18.04 is released this month.  Is there some meaning to 14.4 in the title?

---

### Post by oldfred on 2018-04-05
What model Lenovo?

Since installed in UEFI mode, system must be UEFI.
Have you updated UEFI/BIOS from Lenovo for your model. Early version UEFI from vendors often had bugs many of which they fixed with UEFI updates.

Report says UEFI Secure Boot may be on. Turn it off.

Have you tried booting hard drive entry?
Boot-Repair copied shimx64.efi to /EFI/Boot/bootx64.efi which is a hard drive or fallback boot entry. That entry /EFI/Boot/bootx64.efi is the same entry used on flash drive or live installer for all UEFI external drive boots. But can be a fallback boot entry on internal drives.

Some also modified UEFI to only allow default boot to have description "Windows Boot Manager". That is not allowed per UEFI standard, but several vendors are doing it. Seems strange that multiple vendors would specifically violate UEFI standard in exactly the same way. But they only use description, not actual boot file, so we can have an entry that actually boots with grub's shim file.

       **D:  **Use efibootmgr from live installer in UEFI boot mode.

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

