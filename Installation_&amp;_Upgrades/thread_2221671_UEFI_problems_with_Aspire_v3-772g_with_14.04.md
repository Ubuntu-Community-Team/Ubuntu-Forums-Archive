---
title: "UEFI problems with Aspire v3-772g with 14.04"
date: 2014-05-03
forum: Installation &amp; Upgrades
---

### Post by mart-suga on 2014-05-03
Has pre-installed windows 8.1
Installed Ubuntu 14.04 as secondary OS, ran boot repair, but still cannot boot into ubuntu. Switched off fast-boot and secure boot but still no luck.

Here is the boot-repair log: [http://paste.ubuntu.com/7386007](http://paste.ubuntu.com/7386007)

Mounted efi partition in windows and /ubuntu directory had no .efi files, just some files named with gibberish symbols.

Everytime boots directly to windows. Any ideas?

---

### Post by ubfan1 on 2014-05-03
The files on the EFI partition in /EFI/ubuntu should just be normal files like grubx64.efi, grub.cfg, ...etc.  Sounds like bug 1090829, where the /EFI/ubuntu directory is corrupted.  If you can delete the files, just reinstall grub-efi, if not, try the dosfsck mentioned in comment 40 of the bug to eventually remove the whole directory.

---

### Post by oldfred on 2014-05-03
This user had a Aspire v5.
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)

Did you go into UEFI and change to boot ubuntu entry in UEFI menu.
See last steps that user posted.

---

### Post by mart-suga on 2014-05-05
Found the problem, EFI disk was corrupted. Used chkdsk to fix it and then was able to delete the ubuntu directory on efi drive. Then used boot-repair once more and new .efi files were correctly installed.

---

