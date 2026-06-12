---
title: "Ububtu 12.04 dual boot with windows 8"
date: 2013-04-05
forum: Installation &amp; Upgrades
---

### Post by ponchok on 2013-04-05
Hello,

I followed the instructions found here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Here's the pastbin: [http://paste.ubuntu.com/5681729/](http://paste.ubuntu.com/5681729/)

Windows 8 is not booting from Grub. Error is:
error: Unknown command `drivemap'
error: Invalid EFI file path

Thanks for the help!

---

### Post by oldfred on 2013-04-05
Boot-Repair normally adds correct efi chain boot stanza. Grub2 is still creating old BIOS entries that do not work with UEFI.

If Boot-Repair does not add entries to 25_custom you can manually add to 40_custom. Examples in bug report if needed.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

 menuentry "Windows UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}


 # To clear cache and get new view:
sudo blkid -c /dev/null -o list

This version needs your UUID for the efi partition:


   menuentry "Windows bootmgfw.efi " {
search --fs-uuid --no-floppy --set=root [COLOR=#ff0000]18FE-69D8[/COLOR]
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}


/dev/sda2        [COLOR=#ff0000]BC04-26CA  [/COLOR]                            vfat       SYSTEM

---

### Post by ponchok on 2013-04-06
Thanks! That did the trick.

For the sake of others:
> sudo vim /etc/grub.d/40_custom
edit it to add the ff:
> menuentry "Windows UEFI" {
search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

To clean grub entries:
> sudo vim /etc/default/grub
then add the ff line:
> GRUB_DISABLE_OS_PROBER=true

Do this to let grub pick-up the changes
> sudo update-grub


Then that's it!

---

### Post by ponchok on 2013-04-06
@oldfred: By the way, 25_custom was not added to /etc/grub.d/ when I run boot-repair. Might be something with my system set-up or boot-repair

---

