---
title: "Grub EFI: configfile must be specified on every boot *redux*"
date: 2014-11-26
forum: Installation &amp; Upgrades
---

### Post by ronniepinsky on 2014-11-26
edit:
The problem is at least partially fixed.  When dumped to the grub shell  the "set" command is useful.  It clearly showed the prefix as being set  to "(hd0,gpt1)/boot/grub".  This folder and the stub grub.cfg did not  exist and instead the stub grub.cfg was in the /EFI/ubuntu folder in the  EFI partition instead.  I manually created /boot/grub/ in the EFI  partition and copied the stub grub.cfg into it and that was all she  took.

Keep in mind, I have not changed a thing except for adding the 32-bit  EFI loader file.  So this looks like a bug with Ubuntu.  The real  question is where is grub getting it's config (**prefix=(hd0,gpt1)/boot/grub**) from?

-----------

Every time I boot I am dropped to the grub shell.  I am also using the bootia32.efi file because of a 32-bit EFI but I am not sure that has anything to do with the problem. I have to run:
```

configfile (hd0,gpt5)/boot/grub/grub.cfg

```

at the grub shell to continue booting.  I have tried editing the "stub" grub.cfg file in the EFI partition and adding the line above but it still dropped to the shell.  I have tried renaming the "stub" grub.cfg but it still dropped to the shell.  Finally. I have tried copying the "main" grub.cfg file over the "stub" grub.cfg file but it still dropped to the shell.

Last time, this problem was fixed by running boot-repair but I would like to try to fix this manually to learn more and avoid breaking the system in unpredictable ways.  Where should I investigate from here?

---

### Post by oldfred on 2014-11-26
Not sure if somehow different with the 32 bit version, but you normally have a grub.cfg in /efi/ubuntu with the configfile entry.

Your entry looks correct if sda5 is correct partition and that should have worked.

Standard version that grub creates uses search & UUID, but end result should be the same.

 search.fs_uuid Your-uuid-here root hd0,gpt8
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

My entry:
search.fs_uuid 45de38c8-6748-4634-b207-628d9aa8b42b root hd0,gpt3 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg 

Boot-Repair would not have fixed the grub.cfg in the efi partition unless it was part of a grub reinstall. It normally is just running standard updates using scripts.

---

### Post by ronniepinsky on 2014-11-26
edit: see above.

---

