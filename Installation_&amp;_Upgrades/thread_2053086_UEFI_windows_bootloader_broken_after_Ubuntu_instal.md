---
title: "UEFI windows bootloader broken after Ubuntu install"
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by dzeipou on 2012-09-04
Hey all,

I had working Windows 7 system that was booting in UEFI mode. After installing Ubuntu 12.04, I no longer can see Windows 7 in Grub screen. My /boot/UEFI partition _was not_ overwritten by Ubuntu.

I tried adding Windows 7 boot menu option as was advised in [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting) part "Non-Mac x86_64 UEFI specific info".

What I did was:
```
# grub-probe --target=fs_uuid /boot/efi/efi/Microsoft/Boot/bootmgfw.efi
``` 

and then updated grub cfg with fs_uuid from my system:
```
menuentry "Windows x86_64 UEFI-GPT" {
    search --fs-uuid --no-floppy --set=root 5634-954E
    chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}
```


Now if I select Windows x86_64 UEFI-GPT option in grub menu, i just get few lines of shell output and computer stops booting.

Is there anything that I am missing?

Thanks!

EDIT:
If I press F12 during BIOS startup, I can select Windows from boot devices menu and it loads OK. I can live with this as workarround, but it would still be neat if I could start Windows from GRUB selector.

---

### Post by oldfred on 2012-09-04
Welcome to the forums.

This often can fix the issue as it will add a correct chain entry:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by dzeipou on 2012-09-04
I don't know what boot-repair did to my system, but now I am no longer able to launch my Windows 7 even via BIOS boot selector. And grub is totally not stable, there is no count-down timer and 4 out of 5 times it just freezes.

Pastebin link here [Pastebin]("http://paste.ubuntu.com/1186343/") /dev/sdb can be ignored. It's just a second disk in laptop with Win7 that is not used.

---

### Post by oldfred on 2012-09-04
Was sda gpt before you started any changes and Windows in efi boot mode?

If Boot-Repair sees a gpt drive and efi partition it will add or convert Ubuntu to UEFI boot also.

Windows Boot files BIOS/MBR:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Only your Windows 7 in sdb will work in BIOS mode. And you do not have a grub entry to chain load to that. Not sure if you can chain from efi to BIOS mode in another drive?

If from UEFI mode can you directly boot Windows?

Does grub just totally lock up or what occurs?

---

### Post by YannBuntu on 2012-09-05
> **dzeipou said:**
> I don't know what boot-repair did to my system, but now I am no longer able to launch my Windows 7 even via BIOS boot selector. And grub is totally not stable, there is no count-down timer and 4 out of 5 times it just freezes.

Pastebin link here [Pastebin]("http://paste.ubuntu.com/1186343/") /dev/sdb can be ignored. It's just a second disk in laptop with Win7 that is not used.

Your two Windows are not compatible: one is EFI, the other is not. Did your computer come pre-installed this way? if not, disconnect sdb.

First restore access to Windows:
1) run Boot-Repair, update it
2) click "Advanced options"
3) click "Restore MBR", this will make the "Restore EFI backups" appear
4) untick "Restore MBR", untick "Unhide boot menu"
5) tick "Restore EFI backups"
6) click the "Apply" button
7) Indicate the **new URL** that will appear
8.) reboot and tell us if you can launch Windows via the BIOS selector
9) please show pictures of your BIOS and tell us which entries are available in the "boot order" screen

> **oldfred said:**
> If Boot-Repair sees a gpt drive and efi partition it will add or convert Ubuntu to UEFI boot also.

(Only if there is a Windows EFI file and no BIOS_boot partition.)

---

