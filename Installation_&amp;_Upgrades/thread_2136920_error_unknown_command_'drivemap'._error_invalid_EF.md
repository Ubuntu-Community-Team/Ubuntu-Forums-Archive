---
title: "error: unknown command 'drivemap'. error: invalid EFI file path"
date: 2013-04-19
forum: Installation &amp; Upgrades
---

### Post by AXBX7C on 2013-04-19
Hi all!

My girlfriend purchased an Asus UX31a Zenbook with Windows 7 preinstalled. I talked her into trying Ubuntu 12.04 but now I cannot boot from the recovery partition anymore (Windows 7 recovery). Whenever I try to start from the Windows partition I get the following error "error: *unknown command* '*drivemap*'. error: invalid EFI file path". I tried several solutions suggested on the Web but nothing worked (including trying to repair grub).

My only goal is to boot from the recovery partition to have Windows 7 installed again (I don't intend to use Ubuntu and Windows 7). Has anybody an idea how to do that? I can mount the recovery partition, if this is of any help? Can I just copy the entire recovery partition on an external harddrive and then boot from it?

Thank you for your help!

---

### Post by oldfred on 2013-04-19
Was Windows 7 installed in UEFI mode or BIOS, and then did you install Ubuntu in UEFI or BIOS mode? 
Some newer Windows 7 computers have UEFI but may be installed in either UEFI or BIOS, but with computer having UEFI then the Ubuntu installer may offer to install in either mode also.
Both need to be the same to dual boot.

Best to see details. 
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

If both are UEFI, you may just need the corrected UEFI entries as os-prober only creates BIOS type entries. But if one is UEFI and the other BIOS you can only dual boot by going into UEFI/BIOS and changing to correct mode for install.

---

### Post by AXBX7C on 2013-04-19
Here's the link to the report:

[http://paste.ubuntu.com/5722450/](http://paste.ubuntu.com/5722450/)

I tried to run the recommended repair but the problem persists...

---

### Post by oldfred on 2013-04-19
I cannot tell now how system was originally configured.

You have Lilo (a Windows boot loader only for BIOS/MBR) in the protective MBR, you have the efi partition for UEFI boot with both grub & Windows boot files. But there is no Windows partition. Windows has very specific requirements for partitions both with UEFI and with BIOS installs.

Not sure how to get to recovery with your system. Does vendors web site offer info?
Some have separate UEFI files, some have another partition with efi files (but not set as efi partition), and some have a key on keyboard that launches recovery. Not sure how any of the them actually work.

With BIOS we always suggest making the recovery set of DVDs and a full DVD set of backups before installing just in case. 

If you cannot get recover working, you may have to contact vendor for full install/recovery media. Some only have a minor shipping & handling fee if recent purchase. A few used to have downloads, but those only worked on specific models.

If system was BIOS booted & recovery is a BIOS type install this type of entry works from grub menu. But you have to boot in BIOS mode. You add this to 40_custom. But you have gpt partitioning and Windows will not boot in BIOS mode with gpt paritioning.

      ```
 menuentry "Windows Recovery Environment (loader) (on /dev/sda5)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 2434999C34997192
    drivemap -s (hd0) ${root}
    chainloader +1
}

```

If a UEFI boot this may work. But your Windows BCD in the efi partition has to have an entry into the recovery partition. Maybe copy BCD from sda5?
>  menuentry "Windows UEFI recovery" {
search --fs-uuid --no-floppy --set=root C711-B069
chainloader (${root})/EFI/Microsoft/boot/bootmgfw.efi
}



---

