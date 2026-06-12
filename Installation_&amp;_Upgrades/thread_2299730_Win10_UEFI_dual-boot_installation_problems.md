---
title: "Win10 UEFI dual-boot installation problems"
date: 2015-10-20
forum: Installation &amp; Upgrades
---

### Post by Jukka-Pekka on 2015-10-20
Hello,

I have a working Windows 10 pro installation on a Lenovo T450s laptop. (UEFI and Secure Boot on, but not Fast startup and not Rapid Start)
I have tried to install Ubuntu 15.04 for dual-booting. 

The problem is: after installing ubuntu, I can not boot to Windows at all via grub. Grub lists many options, but none of them work. Only Ubuntu loads with grub (when chosen, and it works perfectly on this laptop).
Win10 can only be booted through the UEFI BIOS (by hitting F12 on power-up for alternative startup disks -> select Windows bootloader).

First, it was impossible to boot into Windows, and unfortunately I do need it for work. I tried all kinds of solutions (searching the net), and finally I managed to get windows loading with bootcfg and bootrec to manipulate the EFI-files.

This works now (via UEFI BIOS), in a way, but is awkward. I would prefer to get the grub options for booting Windows working as well. How to do that? Please hel!. There is something serioulsly mixed up, but I can't figure out what. I am a long-time user of Ubuntu (since 2008), but not very fluent in command-line/terminal operations.

I tried boot-repair, without success, here is the boot-Info link: [http://paste.ubuntu.com/12879928](http://paste.ubuntu.com/12879928)

Edit: after boot-repair, grub does not work at all anymore, it just goes to a kind of command line without any boot options :(

Best regards,

Jukka

---

### Post by ubfan1 on 2015-10-20
Grub still cannot boot Windows when secure boot is enabled (bug 1091464).  Works fine with secure boot off.  Try undoing whatever you did in boot-repair, nothing was really needed.  You have both an MBR and the UEFI boot set up now, not sure what problems having both would cause -- best case, the MBR is just ignored, worst case, it overrides the UEFI boot.

---

### Post by Jukka-Pekka on 2015-10-21
Hello ubfan1, thanks for replying!

Yes, Grub works fine now with Secure Boot disabled. I would like to have Secure Boot enabled, though. 

How can I remove the MBR, if that messes up the UEFI thing?

EDIT: I found that the grub-common package was the wrong i386 -version. I removed it and replaced it with the correct amd64 -version in the Synaptic program. This wrong version was probably why boot-repair kept telling me that grub was still present - and therefore probably did not do everything that it should have done. Now, I ran boot-repair again from the usb live disk, and it went through its thing...and uefi boot works with Ubuntu 15.04 now! Windows 10 still only boots through the UEFI Bios menu, which is not so great. It would be nice to have Win10 to boot from grub as well.

I would still like to remove old-style mbr entries, so that they do not accidentally interfere with some future update or some other event/install. How to do that?

Here is the new boot-repair system-info: [http://paste.ubuntu.com/12885184/](http://paste.ubuntu.com/12885184/)

---

### Post by oldfred on 2015-10-21
We do not normally erase a boot loader in the MBR. It can be done with dd, but dd is also know as Data Destroyer and can be dangerous. As long as you only have UEFI set to boot in UEFI boot mode, it should not matter.

But you can clean up UEFI entries, grub menu entries and the entries added by Boot-Repair into a new grub file 25_custom.

I would first clean up kernels. I only keep two, let it grow to 3 or 4 then delete back to 2.
 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
      
 sudo apt-get install synaptic
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
You can also use command line.

You can edit entires in 25_custom.
       
 # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
gksudo gedit /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

### Post by Jukka-Pekka on 2015-10-21
Thanks oldfred!

I have now cleaned the extra kernels, as you suggested.

I don't know if this is relevant to why windows (or MokManager) do not boot (error messsage:image not found):

The unique GUID for windows seems to be the same in:

```
**efibootmgr -v**
BootCurrent: 0014
Timeout: 0 seconds
BootOrder: 0014,0013,000C,0009,000A,0008,000D,0007,000B,0012
Boot0000  Setup    FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0001  Boot Menu    FvFile(126a762d-5758-4fca-8531-201a7f57f850)
Boot0002  Diagnostic Splash Screen    FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0003  Lenovo Diagnostics    FvFile(3f7e615b-0d45-4f80-88dc-26b234958560)
Boot0004  Startup Interrupt Menu    FvFile(f46ee6f4-4785-43a3-923d-7f786c3c8479)
Boot0005  Rescue and Recovery    FvFile(665d3f60-ad3e-4cad-8e26-db46eee9f1b5)
Boot0006  MEBx Hot Key    FvFile(ac6fd56a-3d41-4efd-a1b9-870293811a28)
Boot0007* USB CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot0008* USB FDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot0009* ATA HDD0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f600)
Boot000A* ATA HDD1    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f601)
Boot000B* ATA HDD2    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f602)
Boot000C* USB HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
Boot000D  PCI LAN    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot000E* IDER BOOT CDROM    ACPI(a0341d0,0)PCI(16,2)ATAPI(0,1,0)
Boot000F* IDER BOOT Floppy    ACPI(a0341d0,0)PCI(16,2)ATAPI(0,0,0)
Boot0010* ATA HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f6)
Boot0011* ATAPI CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a354)
Boot0012* PCI LAN    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot0013* Windows Boot Manager    HD(2,96800,6097f,[COLOR=#FF0000]a1eb04b6-6235-4b46-bae0-a71365dd1ddc[/COLOR])File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...3...............
Boot0014* ubuntu    HD(2,96800,6097f,a1eb04b6-6235-4b46-bae0-a71365dd1ddc)File(\EFI\ubuntu\shimx64.efi)
```
 
and

```
**sudo gdisk /dev/sda**

GPT fdisk (gdisk) version 0.8.10

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): i
Partition number (1-8): 2
Partition GUID code: C12A7328-F81F-11D2-BA4B-00A0C93EC93B (EFI System)
Partition unique GUID: [COLOR=#FF0000]A1EB04B6-6235-4B46-BAE0-A71365DD1DDC[/COLOR]
First sector: 616448 (at 301.0 MiB)
Last sector: 1012094 (at 494.2 MiB)
Partition size: 395647 sectors (193.2 MiB)
Attribute flags: 0000000000000000
Partition name: 'EFI system partition'

Command (? for help): i
Partition number (1-8): 6
Partition GUID code: 0FC63DAF-8483-4772-8E79-3D69D8477DE4 (Linux filesystem)
Partition unique GUID: 3C0DBA76-4770-4D9E-8670-F7265F4B9B60
First sector: 708466688 (at 337.8 GiB)
Last sector: 757295103 (at 361.1 GiB)
Partition size: 48828416 sectors (23.3 GiB)
Attribute flags: 0000000000000000
Partition name: ''

```
```
This is one line of update-grub output for Windows:
Found Windows Boot Manager in  /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Why is the "@" there? Is this the problem, perhaps?

My grub.cfg looks as follows for the Windows etc. parts (which do not work):
### BEGIN /etc/grub.d/25_custom ###

menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 0E19-0889
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root 0E19-0889
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}

menuentry "EFI/ubuntu/MokManager.efi" {
search --fs-uuid --no-floppy --set=root 0E19-0889
chainloader (${root})/EFI/ubuntu/MokManager.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (kohteella /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-efi-0E19-0889' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0E19-0889
    else
      search --no-floppy --fs-uuid --set=root 0E19-0889
    fi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```

The UUID 0E19-0889 matches what gparted reports. The files are in the directories that grub refers to (bootmgfw.efi, bkpbootx64.efi and MokManager.efi).

If you have ideas on how to proceed, I would appreciate that greatly!

Best regards,

Jukka

---

### Post by oldfred on 2015-10-21
The gpt(GUID) partitioning has its own internal unique GUIDs. And that unique GUID is for the ESP.
But then the partitioning tools assign UUIDs for the ESP. 
They are not the same thing.

I think the @ is just saying that is where it found the Windows efi boot files.
Boot stanza does not include the @ and looks normal.

Does any of entries in grub boot Windows with secure boot off? If so I would just delete all the other entries in grub.

---

### Post by Jukka-Pekka on 2015-10-21
Thanks for the clarification!

Yes, I can Boot into Windows (and the MokManager) through the Grub menu when Secure Boot is off. With all the listed options working. Very strange.
However, shouldn't everything work with Secure Boot enabled as well? How can Secure Boot affect loading Windows through grub - can this be repaired (I would like to) ?

The error messages i get from the Grub options with Secure Boot enabled are:

/EndEntire
file path: /ACPI(a0341d0,0)/PCI2(2,1f)/Sata(0,0,0)/HD(2,96800,6097f,b604eba13562464b,2,2)/File(\EFI\Microsoft\Boot)/File(bootmgfw.efi)/EndEntire
error: cannot load image

I don't know what that means - but the bootmgfw.efi file is where it is supposed to be. This is the first entry, the others have a similar error message, ending with the "cannot load image" -statement.


EDIT:
I found an old bug report: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)
I suppose my problem is because of this old bug, which has not been fixed for many years.
So, perhaps nothing can be done about it, at least nothing is indicated in the bug thread.

Thanks for your help anyway!

---

### Post by oldfred on 2015-10-21
ubfan1 posted grub bug report in post #2 on secure boot of Windows from grub. Does not currently work. Something in the chain of signed software must not be correct.

But the entire idea of signed kernel boot is oversold. It is from Microsoft as it has had a major marketing issue of virus on Windows. So what better marketing than have a Secure Boot system. But that does not fix virus issues. And it helps them complicate other system installs which has always been a Microsoft requirement. 

And the only major boot virus we had was from Sony when it implemented a boot sector virus to control Sony DRM and prevent users from running Sony music or videos.

Eventually we may all need signed boot loaders but currently not really required. No BIOS based system has a secure boot.

---

