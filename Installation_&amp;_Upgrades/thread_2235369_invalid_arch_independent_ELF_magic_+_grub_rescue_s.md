---
title: "invalid arch independent ELF magic + grub rescue screen, no fixes I've tried yet have"
date: 2014-07-20
forum: Installation &amp; Upgrades
---

### Post by cody.messick on 2014-07-20
I know there's a lot of questions online already similar to my own,  but I've tried all of the solutions I can find.  Normally I'm able to  fix my issues on my own with the help of this forum, but when trying to  help my friend with his laptop I finally hit a wall and thought I'd ask a  question myself.
  He installed ubuntu 12.04, dual booting with windows 8.  His window  booter wasn't working, so I told him to try boot-repair, and I forgot  that the option for fixing the windows MBR was in the advanced options  until after the boot-repair had run.  So we restarted the computer just  in case it fixed the problem.  Once we did that, we got the invalid arch  independent ELF magic error.  So I tried a few of the fixes I found on  this forum, including running

```


sudo mount /dev/sda10 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
```

This did not fix the problem.  I'm at a loss, help would be appreciated.  I ran boot-repair again to grab this: [http://paste.ubuntu.com/7826738/](http://paste.ubuntu.com/7826738/)

---

### Post by oldfred on 2014-07-20
You show grub installed to protective MBR, so at some point it was in BIOS mode. But it looks like Boot-Repair or a new install, now has it in UEFI boot mode as you have /boot/efi in fstab. Invalid arch or ELF issues often are mixed UEFI or BIOS boot messages.

UEFI & BIOS boot modes are not compatible. So once you start booting in one mode you cannot switch to the other mode. Or from grub menu you can only boot systems in same boot mode.
So if Windows is in UEFI boot mode, you need Ubuntu in UEFI boot mode.

You do need to insure fast boot is/was off in Windows. Grub cannot boot it if it still is on, grub really only boots working Windows, so you may need Windows repair CD or flash drive to fix Windows whenever it has issues.

You show that you ran Boot-Repairs buggy UEFI fix. Best to undo that.

       Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only grub 
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)

To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. Then directly boot Windows from UEFI menu. Current Windows entry boots grub as the file has been renamed.

New UEFI systems work better with the newest Ubuntu or 14.04.

What model computer? Some do require file rename similar to what Boot-Repair does, but other rename works better in most cases now.

Be sure to always boot in UEFI mode. Boot-Repair indicates you booted it in BIOS mode which may add to issues.

See recent post by Balz_Miller. 
[http://ubuntuforums.org/showthread.php?t=2227720](http://ubuntuforums.org/showthread.php?t=2227720)

---

### Post by cody.messick on 2014-07-20
Thanks for the thorough response.  The computer is a Lenovo y510p.

---

### Post by oldfred on 2014-07-20
Some quotes from others Lenovo users:

 > Lenovo's  buggy EFI Bios is will not boot from a DVD at all unless you enable 'legacy' (which you can't do because it screws with Windows 8!)
 The work around was to turn ON 'Legacy' boot mode in the BIOS and turn OFF "secure-boot" mode from locking out Ubuntu), and also make sure to turn OFF 'Legacy' SATA AHCI to ATA.
Then I installed Ubuntu from a USB stick (because these settings would only boot the Ubuntu installer from USB, but not DVD). 

   
 linux	/boot/vmlinuz-3.5.0-25-generic.efi.signed root=UUID=07df2e4a-8ef3-4f35-9b9c-43bf0570d04b ro   quiet splash $vt_handoff
initrd	/boot/initrd.img-3.5.0-25-generic

 }
Another Lenovo solution copy grubx64.efi to bootx64.efi & boot hard drive not anyother entry
[http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470](http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470)

  Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)

---

