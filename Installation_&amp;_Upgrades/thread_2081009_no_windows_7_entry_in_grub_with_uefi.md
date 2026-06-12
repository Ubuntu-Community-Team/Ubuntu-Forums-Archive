---
title: "no windows 7 entry in grub with uefi"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by schru on 2012-11-05
Can somebody help me to get windows 7 entry in grub? I've been trying to figure it out for two days :/ I installed windows 7 first, and xubuntu 12.10 after that. Boot-repair doesn't help, here's the url it generates - [http://paste.ubuntu.com/1335796/](http://paste.ubuntu.com/1335796/). Thanks.

---

### Post by oldfred on 2012-11-05
Grub usually adds a BIOS type chain boot entry that does not work. So Boot-Repair has an option to add a correct Windows chain load entry that chains back to the efi entry.

[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)

You can manually add entries to 40_custom. Examples below some with different options. You have to change examples to your UUID.

Chainload entry:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
[http://ubuntuforums.org/showthread.php?t=1934773](http://ubuntuforums.org/showthread.php?t=1934773)
menuentry "Windows 7 UEFI" {
  insmod part_gpt
  insmod fat
  insmod search_fs_uuid
  insmod chain
  set root='(hd0,gpt2)'
  search --fs-uuid --no-floppy --set=root 4f84-ee2e
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

[http://www.insanelymac.com/forum/lofiversion/index.php/t186440](http://www.insanelymac.com/forum/lofiversion/index.php/t186440)
menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

[https://wiki.archlinux.org/index.php/UEFI#UEFI_Shell](https://wiki.archlinux.org/index.php/UEFI#UEFI_Shell)
boot to efi shell:
cd fs0:
cd efi\Microsoft\Boot
bootmgfw.efi

From Boot-Repair
menuentry "Windows UEFI recovery" {
search --fs-uuid --no-floppy --set=root 96D8-1AC2
chainloader (${root})/EFI/Microsoft/boot/bootmgfw.efi.bkp
}

menuentry "Windows UEFI loader" {
search --fs-uuid --no-floppy --set=root E248-8D15
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi.bkp
}

---

### Post by wnelson on 2012-11-05
I had to add the following to /etc/grub.d/40_custom


#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7  (loader) (on /dev/sda7)" --class windows --class os {
    insmod part_gpt
    insmod part_msdos
    set root='(hd0,gpt2)'    # <------ Change this to you gpt partition
    search --no-floppy --fs-uuid --set=root 763A-DA36
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi    # <--- Make sure that this is available in you gpt partition
}
40_custom (END)

---

### Post by schru on 2012-11-06
I tried this and it worked:

menuentry "Windows 7 UEFI" {
search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

Thanks for tips guys.

---

