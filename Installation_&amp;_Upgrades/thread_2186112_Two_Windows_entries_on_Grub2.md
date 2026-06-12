---
title: "Two Windows entries on Grub2"
date: 2013-11-05
forum: Installation &amp; Upgrades
---

### Post by Thomas Oliveira on 2013-11-05
Hi!

After installing Ubuntu and running Boot-Repair, I have these two Windows entries on /boot/grub/grub.cfg:

```
menuentry "Windows Boot UEFI loader" {
    search --fs-uuid --no-floppy --set=root A62E-0230
    chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}


menuentry "Windows Boot Manager (UEFI on /dev/sda2)" --class windows --class os {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  A62E-0230
    else
      search --no-floppy --fs-uuid --set=root A62E-0230
    fi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
```

Could you please tell me what is the difference between them and which one I should use?
(I have already searched for it on grub2 documentation but I had not really understood the differences).

Thanks!

---

### Post by oldfred on 2013-11-05
Is this 13.10?
Only the very newest Ubuntu has a fix for a bug where grub only created BIOS boot entries that did not work with UEFI. So Boot-Repair adds correct entries in 25_custom. But if you have the new version maybe grub2's os-prober  is creating a correct entry now?

 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
      
 os-prober fix in grub2_2.00-14 and os-prober_1.58 from Debian

If you want to houseclean some entries or change them, info is in link in my signature.

---

### Post by Thomas Oliveira on 2013-11-23
It is 13.10, grub2_2.00-19ubuntu2.1 and os-prober_1.61ubuntu1.
 

 I don't know if this can be the reason for this problem, but just to let you know:

 in order to be able to boot on GRUB on my HP notebook, I had
 moved  /boot/efi/EFI/**Microsoft/Boot**/bootmgfw.efi to /boot/efi/EFI/**Microsoft**/bootmgfw.efi and
copied /boot/efi/EFI**/ubuntu**/grubx64.efi to /boot/efi/EFI/**Microsoft/Boot**/bootmgfw.efi

 

 After that, I had edited /etc/grub.d/30_os-prober replacig references to /boot/efi/EFI/**Microsoft/Boot**/bootmgfw.efi by /boot/efi/EFI/**Microsoft**/bootmgfw.efi  

 

 Anyway, I followed the instructions found in your message in [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

 added GRUB_DISABLE_OS_PROBER=true to /etc/default/grub

 run  update-grub and everything is fine now.

 

 Thanks!

---

