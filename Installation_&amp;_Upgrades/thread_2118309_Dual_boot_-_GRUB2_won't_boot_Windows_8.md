---
title: "Dual boot - GRUB2 won't boot Windows 8"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by Ne0nLigh7 on 2013-02-20
Hello. I'm a Windows user and am curious about Linux. I'm completely new to Linux.

I've been trying to dual boot Windows 8 and Kubuntu 12.10 on my laptop. It's a newer one, so I have UEFI to worry about. Windows 8 came pre-installed in EFI mode. I've disabled secure boot and have my boot mode set to UEFI. I'm trying to dual boot onto only one HDD.

My "BIOS" has the words "InsydeH20 Setup Utility" top and center when changing BIOS settings, like this one:
[img]http://pix.toile-libre.org/upload/original/1347270332.jpg[/img]

I've been following the first paragraph of this:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
I've just been using a Kubuntu install disk and not Ubuntu. I'm hoping there isn't a terribly large difference in the installation process.

I've booted from the live CD and installed my Kubuntu partitions just fine. I have /(root), swap and /boot(loader went here) partitions.

As instructed upon the completion of the installation, I restarted my computer and it loads into GRUB2. Kubuntu boots just fine from here but when booting into Windows 8, I get the following:

```
error: can't find command 'drivemap'.
error: invalid EFI file path.
```

I've booted into the live CD and run boot-repair twice, still no luck. Here is the link provided by boot-repair:
[http://paste.ubuntu.com/1693769](http://paste.ubuntu.com/1693769)
Pardon, it seems a bit of a mess in there. 

I've previously failed at a few installations and have played around (with no success) with EasyBCD. I tried to add Kubuntu to the windows loader, before realizing that it does not work with EFI systems. Bad idea?

How can I get GRUB2 to boot Windows 8 properly?

---

### Post by oldfred on 2013-02-20
Boot-Repair found a lot of efi files so it added a lot of boot entries. Those should work. The one's from os-prober will not.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

### Post by Ne0nLigh7 on 2013-02-20
Hm, this is odd. I'll retract a previous statement of mine. I cannot boot Kubuntu either, I'm only met with a gray screen. I did not change anything.

As per the Windows 8 entry, I do not know how to add a valid boot entry.

---

### Post by oldfred on 2013-02-21
Boot Repair added the correct entries just do not use the incorrect one's from os-prober that try to boot the old BIOS way.

If you get grub menu then you may have video issue or need other boot parameters. 

What video card? But nomodeset usually gets you to a minimal video mode.

       Boot-Repair --> Advanced options --> GRUB options tab --> tick "Add kernel option: nomodeset" --> Apply

How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Ne0nLigh7 on 2013-02-21
Adding nomodeset allowed me to boot into Kubuntu, thanks! Although now it's displaying everything in 4:3 instead of 16:9, and I'm using a widescreen. I suppose this problem for a different thread.

I'm using an NVIDIA GeForce GT650M for a graphics card.

As far as a valid boot entry for windows 8, I'm not sure I have one labeled something along the lines of "Windows UEFI loader". My Grub menu looks like the following:
```
Ubuntu
Advanced options for Ubuntu
efi/EFI/Microsoft/Boot/bootmgfw.efi
efi/EFI/Boot/bootx64.efi
Windows UEFI recovery bootmgfw.efi
Windows Boot UEFI recovery
Windows UEFI recovery LrsBootmgr.efi
Windows Boot UEFI recovery bootx64.efi
Windows 8 (loader) (on /dev/sda5)
System setup
```
Are one of these a valid windows 8 boot entry? Option 3 and 4 give me a "file not found" message and the rest of them are labeled "recovery" so i'm assuming that those aren't the droids I'm looking for. From what I understand, the last windows option is the BIOS way of doing things, so that's no good either.

Boot-repair should have created a valid entry somewhere, right?

---

### Post by oldfred on 2013-02-21
```
/dev/sda2        F426-6174                              vfat       SYSTEM_DRV
/dev/sda3        3A26-B28D                              vfat       LRS_ESP
```

Your sda2 is your efi partition and it looks like sda3 is the one with recovery boot files.

```
menuentry "efi/EFI/Microsoft/Boot/bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 5294cf89-df38-44d7-8c34-0c34eda10bd4
chainloader (${root})/efi/EFI/Microsoft/Boot/bootmgfw.efi
}

menuentry "efi/EFI/Boot/bootx64.efi" {
search --fs-uuid --no-floppy --set=root 5294cf89-df38-44d7-8c34-0c34eda10bd4
chainloader (${root})/efi/EFI/Boot/bootx64.efi
}

menuentry "Windows UEFI recovery bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root[COLOR=Red] F426-6174[/COLOR]
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

menuentry "Windows Boot UEFI recovery" {
search --fs-uuid --no-floppy --set=root [COLOR=Red]F426-6174[/COLOR]
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}

menuentry "Windows UEFI recovery LrsBootmgr.efi" {
search --fs-uuid --no-floppy --set=root 3A26-B28D
chainloader (${root})/EFI/Microsoft/Boot/LrsBootmgr.efi
}

menuentry "Windows Boot UEFI recovery bkpbootx64.efi" {
search --fs-uuid --no-floppy --set=root 3A26-B28D
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}
```

So I do not know where the first two entries came from as they refer to a ext2 partition. Did some windows file get copied into that?

But regardless of title the [COLOR=Red]F426-6174 [COLOR=Black]entries should work. They refer to the efi partition.[/COLOR]
[/COLOR]

---

### Post by Ne0nLigh7 on 2013-02-21
Agh, dangit! There was a valid entry sitting there all along, just with a slightly different name then I though. I was deceived by the word "recovery" thinking that that entry pointed at some sort of recovery tool/partition.

Things are working just fine now that I know where to look for them. Thanks for the help olfred!

---

### Post by oldfred on 2013-02-21
Glad that is working. :)

Not sure why it says recover. I know Yann has posted links to his program to file a bug, but I do not have that handy. You might just post in the mega-thread.

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

