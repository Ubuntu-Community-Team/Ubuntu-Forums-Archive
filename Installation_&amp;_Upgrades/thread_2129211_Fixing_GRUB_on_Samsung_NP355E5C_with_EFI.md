---
title: "Fixing GRUB on Samsung NP355E5C with EFI"
date: 2013-03-25
forum: Installation &amp; Upgrades
---

### Post by Torquenstain on 2013-03-25
Hello,

I have a problem with booting Windows from GRUB menu.

I installed boot-repair and tried to fix the GRUB  by "Recommended repair", but it stuck on "Reinstall GRUB. This may  require several minutes.". I was waiting about two hours, then I pressed  "cancel".
I tried again, but also unsuccessfully.


[http://paste.ubuntu.com/5640095/](http://paste.ubuntu.com/5640095/)


I would be grateful for your help.

---

### Post by oldfred on 2013-03-25
Does Ubuntu boot ok?

Are you running the very newest version of Boot-Repair. I saw just yesterday Yann was making fixes for just that issue.

You can manually add correct Windows boot entries. Boot-Repair scans for efi files and adds boot entries to 25_custom. But you can manually add to 40_custom. Bug report has several examples.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

If you use UUID (red in example below)
      
 # To clear cache and get new view:
sudo blkid -c /dev/null -o list
Then add one or both of below examples with changes to 40_custom
 gksudo gedit /etc/grub.d/40_custom



     menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

   menuentry "Windows bootmgfw.efi " {
search --fs-uuid --no-floppy --set=root [COLOR=#ff0000]18FE-69D8[/COLOR]
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

---

