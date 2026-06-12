---
title: "Booting to window 8 instead of GRUB w/ UEFI"
date: 2014-12-27
forum: Installation &amp; Upgrades
---

### Post by samercier on 2014-12-27
I was told to post here if the boot-repair utility didn't work from this article. ([https://help.ubuntu.com/community/UEFI#Installing_Ubuntu_Quickly_and_Easily_via_Trial_and_Error](https://help.ubuntu.com/community/UEFI#Installing_Ubuntu_Quickly_and_Easily_via_Trial_and_Error))

My paste bin that it told me to post is here. ([http://paste.ubuntu.com/9632983](http://paste.ubuntu.com/9632983))

Can someone help me? I'm in way over my head.

---

### Post by yancek on 2014-12-27
There is nothing at the link for your bootrepair output.

> The Paste you are looking for does not currently exist. 

---

### Post by samercier on 2014-12-27
Sorry I fixed that. Thank you for pointing that out. :)

---

### Post by oldfred on 2014-12-27
What is not booting, Windows or Ubuntu?

You have Multiple Windows entries in Grub menu and multiple entries in UEFI menu.
First from UEFI menu or one time boot key (often f12 or f10) what entries boot?
It looks like you have two Windows UEFI entries that are duplicates but one is 00 and the other 04.

The do you get grub menu and what entries work or what comes up on screen. 
Some with Toshiba have had to make grub be bootx64.efi to get Ubuntu to boot.
And some with i915 Intel Video need boot parameters for Ubuntu to boot fully.
The mokmanager entry is only if you modify secure boot keys, so not really used yet. 
And the Toshiba/Boot/bootmfgw.efi is probably to the Toshiba recovery mode, to totally reset system to as purchased.

```
 menuentry "Windows UEFI [COLOR=#ff0000]bootmgfw.efi[/COLOR]" {
search --fs-uuid --no-floppy --set=root 7EAA-2EFF
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

   menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root 7EAA-2EFF
chainloader (${root})/EFI/Boot/[COLOR=#ff0000]bootx64.efi[/COLOR]
}

   menuentry "EFI/ubuntu/MokManager.efi" {
search --fs-uuid --no-floppy --set=root 7EAA-2EFF
chainloader (${root})/EFI/ubuntu/MokManager.efi
}

   menuentry "EFI/Toshiba/Boot/bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 7EAA-2EFF
chainloader (${root})/EFI/Toshiba/Boot/bootmgfw.efi
}

   BootOrder: 0003,0005,0004,0001,0002,0000
Boot[COLOR=#ff0000]0000[/COLOR]* Windows Boot Manager    HD(2,200800,32000,c0dbf929-8d61-11e4-9693-e760a74f8003)File(EFIMicrosoftBoot[COLOR=#ff0000]bootmgfw.efi[/COLOR])WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...2................
Boot0001* UEFI: IP4 Realtek PCIe GBE Family Controller    ACPI(a0341d0,0)PCI(1c,3)PCI(0,0)MAC(MAC(600292261528,0)..BO
Boot0002* UEFI: IP6 Realtek PCIe GBE Family Controller    ACPI(a0341d0,0)PCI(1c,3)PCI(0,0)MAC(MAC(600292261528,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot0003* [COLOR=#ff0000]ubuntu[/COLOR]    HD(2,200800,32000,c0dbf929-8d61-11e4-9693-e760a74f8003)File(EFIubuntushimx64.efi)
Boot[COLOR=#ff0000]0004[/COLOR]* Windows Boot Manager    HD(2,200800,32000,c0dbf929-8d61-11e4-9693-e760a74f8003)File(EFIMicrosoftBoot[COLOR=#ff0000]bootmgfw.efi[/COLOR])WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...d................
Boot0005* UEFI: SanDisk Cruzer Blade 1.26    ACPI(a0341d0,0)PCI(14,0)USB(2,0)HD(1,800,ee7801,00066d5e)..BO


```

---

### Post by samercier on 2014-12-28
@oldfred,
When I press f10 I get nothing. When I press f12 my options are to boot to the flashdrive, HDD/SSD, and then LAN. I chose HDD/SDD.

I just tried replacing bootx64.efi with grubx64.efi /EFI/Boot, and surrounded it with all the files it would normally have in /EFI/ubuntu/, but that didn't work. My system is still completely ignoring grub and just booting straight into windows.

It is interesting to note that in /EFI there is a "Toshiba" directory that contains everything that is in the "Windows" directory or so including the "bootmgfw.efi". It is quite possible that that is why there are multiple boot entries for the Windows Boot Manager in my grub config. 

Just from booting you wouldn't be able to tell that GRUB is anywhere on my system. It shows no signs of even initiating it still. That is what I mean by it boots straight into windows. 

It is also interesting to note that when booting it shows Toshiba branding which possibly suggest that it is using /EFI/Toshiba instead of /EFI/Windows, but I don't know. I think it is just as possible that that folder only contains data for the recovery mode.

---

### Post by oldfred on 2014-12-28
I do not understand why UEFI and one time key do not show at least the Windows entry. You are showing two Windows entries in UEFI list from efibootmgr. My old Toshiba from 2006 uses f12, so that still is the same, but different vendors use different keys or sometimes change.

Too many systems to be accidental do not show or boot the Ubuntu entry even when efibootmgr shows it and it is set as default. Many vendors have modified UEFI to only boot an entry that says "Windows".  Microsoft must be giving a discount or else it would not be so common. And Ubuntu has a position paper saying vendors should not violated UEFI standard by setting description as only boot.

Perhaps now instead of Windows description it is using "Toshiba" description. But some systems just booting into a recovery partition seems to reset something and cause issues, so I do not suggest that. Does your manual say to boot into recovery partition and make a recovery set of DVDs. Then it should be safe to boot into it. And you probably should make that recovery set of DVDs as if drive fails it is a copy to have. More for if you want to sell system without your data but fully Windows.

From Linux we cannot look at BCD, but that is the Windows file that tells it what to boot. Are the BCDs different in the Windows efi folder and the Toshiba folder?

Several others with Toshiba have just copied grub or shim to be bootx64.efi and hard drive boot entry then boots grub. The bootx64.efi was for external devices only but newer UEFI includes it on internal devices also as a boot choice. I thought it was a direct boot to UEFI to allow setting changes, but some systems seem to really have it has the same as bootmgfw.efi to directly boot Windows, and of course now we have some with grub.

Since 00 and 04 are duplicates I might delete one, since that may be causing UEFI confusion as it only wants to boot one Windows entry?

IF you have not backed up efi partition, do that now. I should have suggested that before you started making changes.

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
modprobe efivars
sudo efibootmgr -v
ls /sys/firmware/efi/vars
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Change boot order with efibootmgr
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)

---

### Post by samercier on 2014-12-29
Okay so it turned out that, through some inexplicable event, somehow between running boot-repair and rebooting the boot order was changed for my system was changed from the one in the one in the boot-repair logs to "0005,0000,0001,0002,0003". Also interestingly 0004 deleted itself. I don't know how that happened. 

Anyway thanks for telling me how to edit the efiboot order. I used efibootmgr like you showed me to change the boot order in case anyone else has this problem.

Thank you very much @oldfred for your help. I wouldn't have known how to start in on diagnosing this problem without you.

For future reference the methods I used are described more specifically in this ( [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD) ) article's example #3.

---

### Post by oldfred on 2014-12-29
Glad it is working.

If you are booting Windows 8.1, that may be why boot order changes. I understand it syncs UEFI with its BCD. I think that is why now Boot repair is suggesting adding an Ubuntu entry to BCD.

---

