---
title: "laptop does not load Ubuntu14.10 but instead loads Windows8.1"
date: 2015-03-13
forum: Installation &amp; Upgrades
---

### Post by garry7 on 2015-03-13
[FONT=arial]here is my URL [/FONT][FONT=arial]
[/FONT]
[FONT=arial][http://paste.ubuntu.com/10589752/](http://paste.ubuntu.com/10589752/)
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]after running this commend in window [/FONT]
[FONT=arial]bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi 
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]i am still unable to go to boot menu and it directly go to window and from there i have to [COLOR=#333333][FONT=Ubuntu]Go to the [/FONT][/COLOR][PowerOff]("https://help.ubuntu.com/community/PowerOff")[FONT=Ubuntu][COLOR=#333333] options and the choose Ubuntu to run. [/COLOR][/FONT][/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][IMG]https://mail.google.com/mail/u/0/?ui=2&ik=4e05a3e6b1&view=att&th=14c13e82df07a548&attid=0.2&disp=safe&realattid=ii_i77s91j31_14c13e82daf872e6&zw[/IMG][COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR][/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][COLOR=#333333][FONT=Ubuntu]this my system details:-[/FONT][/COLOR]
[/FONT]
[FONT=arial][COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR][/FONT]
[FONT=arial][COLOR=#333333][FONT=Ubuntu].[IMG]https://mail.google.com/mail/u/0/?ui=2&ik=4e05a3e6b1&view=att&th=14c13e625731214d&attid=0.1&disp=safe&realattid=ii_i77s67ap0_14c13e625b867848&zw[/IMG]
[/FONT][/COLOR][/FONT]
[FONT=arial][COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR][/FONT]
[FONT=arial][FONT=Ubuntu][COLOR=#333333]i have disable the secure boot.
&#8203;t and lagace mode is enable. [/COLOR][/FONT][/FONT]
[FONT=arial][FONT=Ubuntu][COLOR=#333333]
[/COLOR][/FONT][/FONT]
[FONT=arial][FONT=Ubuntu][COLOR=#333333]
[/COLOR][/FONT][/FONT]
[FONT=arial][FONT=Ubuntu][COLOR=#333333]Please help with this problem.[/COLOR][/FONT][/FONT]
[FONT=arial][FONT=Ubuntu][COLOR=#333333]
[/COLOR][/FONT][/FONT]
[FONT=arial][FONT=Ubuntu][COLOR=#333333]
[/COLOR][/FONT][/FONT]
[FONT=arial][FONT=Ubuntu][COLOR=#333333]Regards[/COLOR][/FONT][/FONT]
[FONT=arial][FONT=Ubuntu][COLOR=#333333] Garry[/COLOR][/FONT][/FONT]

---

### Post by flaymond on 2015-03-14
1. Do you installed with UEFI method?

Take a look here - [http://www.makeuseof.com/tag/tired-of-windows-8-how-to-dual-boot-windows-ubuntu/](http://www.makeuseof.com/tag/tired-of-windows-8-how-to-dual-boot-windows-ubuntu/)

---

### Post by oldfred on 2015-03-14
What brand/model computer. Some only boot Windows as in UEFI they have modified it to only look for entries with Windows in Description. Hard drive entry works so we can create a work around by copying grub into hard drive boot entry.

Never seen an UEFI with so many duplicate entries for hard drive boot. There were issues a couple of years ago with a couple of vendors that if UEFI's NVRAM got too full it totally bricked computer. 
I would suggest deleting most of the duplicate entries.

Link in my signature has all the details. Your efi partition is sda2.

Back up entire efi partition before making any changes. Boot-Repair may have made copies already, but better you do your own to another drive.

          A: Manually rename files efi hard drive boot files in efi partition /EFI/Boot
          Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.
     Older rename of Windows efi file not recommended anymore. (old versions of Boot-Repair did rename the Windows efi file)
         From live installer mount the efi partition on hard drive, lines with # are comments only: Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.
         sudo mount /dev/sda1 /mnt
         only if /EFI/Boot not already existing, run the mkdir command,
        sudo mkdir /mnt/EFI/Boot
        sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
         If new folder created, the bootx64.efi will not exist, skip backup command
             sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
         make grub be hard drive boot entry in UEFI. Then boot hard drive entry in UEFI menu.
             sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi
      More examples of users who manually moved efi files
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

    
           If you cannot do change from UEFI menu, you can from command line with efibootmgr.
        sudo apt-get install efibootmgr

      You can add, change or delete UEFI entries with efibootmgr:
    Really UEFI boot menu edits 
    [http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)
    [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
     Remove Duplicate Firmware Objects in Windows BCD and NVRAM
    [http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx)
           # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
ls /sys/firmware/efi/vars
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.

---

