---
title: "Unable to boot Ubuntu 13.04 after upgrading to Windows 8.1"
date: 2014-02-06
forum: Installation &amp; Upgrades
---

### Post by Kevin_Tang on 2014-02-06
Dear Ubuntu Forum,

[FONT=arial] I have recently upgraded from WIndows 8 to Windows 8.1. 

Prior upgrading, I was dual-booting Ubuntu 13.04 and Windows 8. 

After upgrading, I was unable to see the GRUB screen, and can only boot into WIndows 8.1.
[/FONT]
[FONT=arial]My computer's model is SONY E14
[/FONT]
[FONT=arial] It has UEFI and Secure boot options (both enable)
[/FONT]
[FONT=arial]1. I first disable the Secure boot option
[/FONT][FONT=arial]2. I did a boot-repair using the Try-Ubuntu option from a USB drive.
[/FONT][FONT=arial]3. I did a recommended repair, but no avail.

[/FONT]
[FONT=arial] Here is the report:
[http://paste.ubuntu.com/6885118/](http://paste.ubuntu.com/6885118/)
[/FONT]
[FONT=arial]
I am looking forward to hearing from you.
Many thanks,
[/FONT]
Kevin

---

### Post by oldfred on 2014-02-06
Did you run the backup & rename function in Boot-Repair before to get your system to boot?

That renames bootmgfw.efi to bkpbootmgfw.efi and makes grub or shim be bootmfgw.efi. Then system thinks it is booting Windows from UEFI menu, but actually boots grub. Then you only can boot Windows from bkpbootmgfw.efi menu listing in grub.

But if you installed new version of Windows you may have a new bootmfgw.efi which only boots Windows. And it may not be the same as the old version so you need to be careful not to auto run the restore function in Boot-Repair. Would be best to run restore before Windows update and then redo rename after.

Back up efi partition. And at this point we probably need to manually do the rename that Boot-Repair does.

After backup of efi files, change name of current bkpbootmfgw.efi (delete or rename to something else just in case) and rename bootmfgw.efi to bkpbootmfgw.efi. Copy shim from ubuntu folder into Micosoft folder and rename it to bootmfgw.efi.

Assumptions, but if you ran Boot-Repair again you may have moved files around.
current bkpbootmfgw.efi is Windows 8's version of bootmfgw.efi.
bootmfgw.efi is Windows 8.1's new efi boot. And is the only file UEFI lets you boot.
Old grub shim that was bootmfgw.efi was overwritten, but you still have original in ubuntu folder in efi partition.

---

### Post by Kevin_Tang on 2014-02-06
Dear [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711"),

What you described is exactly what happened.

Your solution of manually renaming the files works like a treat.

Much appreciated! You've just saved me another 6 hours battling with this.

Best,
Kevin

---

### Post by oldfred on 2014-02-06
Glad that worked. :)

---

