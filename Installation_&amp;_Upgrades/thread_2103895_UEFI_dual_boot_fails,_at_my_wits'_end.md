---
title: "UEFI dual boot fails, at my wits' end"
date: 2013-01-11
forum: Installation &amp; Upgrades
---

### Post by wingervolley on 2013-01-11
I have an Asus Zenbook UX32VD with 64 bit Windows 7 installed as the default OS. I'm running into a lot of problems getting a Linux dual boot working - I tried installing Linux Mint and Ubuntu 12.10 non-UEFI and editing the Windows bootloader to be able to boot into  Linux without messing with the MBR, but the bootloader refused to boot into Linux (Windows still worked/works fine). When I try to boot into a live USB of Ubuntu 12.04 (I also tried 12.10, same thing) 64 bit in UEFI mode, it just goes to a GRUB prompt screen and when I try to execute the "boot" command, it says "kernel not loaded". Does anyone have any idea of what to do, do I need to use the UEFI boot and if so how do I get it to work? I really don't want to have to reformat and repartition my SSD to run on MBR/BIOS since that'd involve a lot of work to get Windows working again. Thanks for reading, any help would be much appreciated. I need Linux on my laptop for class so this is becoming a real problem, hopefully there'll be a way around all the issues.

---

### Post by oldfred on 2013-01-11
Welcome to the forums.

Both Windows & Ubuntu have to be in UEFI mode. How you boot install media DVD/Flash drive is how it will install. Turn secure boot & fast boot off.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. (Vital for some systems).
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)


Other models of Asus - may be similar UEFI?

       
 Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
       
 ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

    
Use Boot-Repair to fix this bug:
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

    
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by siepo on 2013-01-11
My ubuntu live usb stick also displays just a grub prompt instead of a boot menu. I still managed to boot ubuntu as follows from the grub prompt:
```

ls
set root=(hd0,msdos1)
linux /casper/vmlinuz boot=casper
initrd /casper/initrd.lz
boot

```
The ls command tells you about available drives and partitions, which lets you make a better guess for the 'set root=' command.

---

### Post by wingervolley on 2013-01-13
Thanks siepo, that worked perfectly, although I need to manually choose my Windows bootloader from my BIOS menu to get it to boot (is there any way to get Windows to boot from the GRUB menu?)

Also, what do the second through the fifth lines of what you posted do, out of curiosity?

---

### Post by oldfred on 2013-01-14
If you  have Ubuntu in BIOS mode & Windows in UEFI mode you cannot chain load. UEFI & BIOS offer different data to operating system so they cannot work together.

Boot-Repair will convert a BIOS install of Ubuntu to UEFI, by uninstalling grub-pc and installing grub-efi. Then it will add a correct chain load entry if you boot UEFI from ubuntu entry. Grub2's os-prober has a bug and does not create correct efi chain entries, but still creates the old BIOS entries.

Your manual boot lines are just like any boot stanza, but you are using the link files in / (root) to the most current kernel, so you do not have to know or type all the details of current version.

---

### Post by wingervolley on 2013-01-16
Thanks again, I can't say I totally understand everything that's going on but I'm successfully dual booting which is great.

---

