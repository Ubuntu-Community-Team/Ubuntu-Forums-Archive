---
title: "Boot Repair fails with message about UEFI"
date: 2018-02-07
forum: Installation &amp; Upgrades
---

### Post by johnaaronrose on 2018-02-07
As a result of the latest update by Canonical to Ubuntu 16.04 on my barebones PC (Intel NUC 5CPYB), it would not boot. This has happened before and I have successfully used Boot Repair. When I tried it just now, it boot up from my memory stick containing 64 bit boot repair so I used my CD (after changing to USB Legacy in the BIOS in order to do the boot) and it booted Ok. I selected the Recommended Repair option and it seemed to work as it then showed the green coloured screen for Boot Repair but Boot Repair then complained about not being UEFI boot and stopped. So I tried to boot from UEFI but it would not boot from the SATA SDD after I had selected UEFI in the BIOS. Any ideas please?

---

### Post by yancek on 2018-02-07
Post a link to the output of boot repair so members have access to that information.  You may need to run it again and select the option to Create BootInfo Summary.

---

### Post by ajgreeny on 2018-02-07
If your problem system uses UEFI and you boot the live system that you want to use to repair it in legacy mode, which is what you appear to have done, you will be wasting your time.

You MUST boot the repair DVD/USB in the, same mode as the OS you wish to repair, so boot the live system again, this time  in UEFI mode, and as mentioned by yancek, post back here the pastebin link you get from running the Bootinfo summary from the **Boot-Repair** link in my signature below.

---

### Post by johnaaronrose on 2018-02-07
I downloaded latest 64 bit version of Boot Repair from Sourceforge, used Unetbootin to create Boot Repair boot on USB memory stick and Boot Repair booted up Ok and repaired the PC Ok.

However, whilst I was doing this I accidentally deleted (using gparted) the EFI partition (mounted at /boot/efi, /dev/sdb1 on my SDD which contains everything except for /home which is on my HDD as my SDD is not big enough for it) as I intended to delete the partition on my memory stick but blundered. I then used testdisk to recover my EFI partition and checked it using gparted. It looked Ok. However, when I tried to boot from it there was a message stating:
 "Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key". However, just before this appeared, there were some quick-flashing messages about can't open files in /boot/efi. They were hardly on the screen for more than a second. I've captured them on my phone but they are too quick too see on replay. I'll try again later. I looked at another PC and the files in /boot are:
john@Barebones:~$ ls /boot/efi
EFI
john@Barebones:~$ ls /boot/efi/EFI
Boot  ubuntu
john@Barebones:~$ ls /boot/efi/EFI/boot
bootx64.efi  bootx64.efi.grb
john@Barebones:~$ ls /boot/efi/EFI/ubuntu
fw  fwupx64.efi  grub.cfg  grubx64.efi  mmx64.efi  shimx64.efi

I don't understand why Boot Repair or Ubuntu Installer (on a memory stick) should need these files from my SDD. Is there any way that I can put these files in the /boot/efi partition on my SDD even though I can't boot? Probably a stupid question as I assume that the BIOS is objecting to my SSD as its EFI partition is messed up!

When I try to boot from a memory stick with Boot Repair, there is same files problem as above. I then see a GNU Grub screen which hangs with Boot-Repair-Disk session highlighted and stating something like "Use arrow keys to select entry, 'e' to edit command, 'c' for command line, Esc for Previous Menu". There is no change when I press any key (including Enter or arrow keys or e or c or Esc). Similar, situation for booting from Ubuntu Installer.

Tomorrow I'll disconnect the SSD and try booting again from the Boot Repair memory stick. If it boots, hopefully I will then be able to connect the SSD again to repair its EFI partition. Does Boot Repair allow repairing of the SSD in this situation i.e. after it loads, to then connect the SDD even though the BIOS doesn't know about it?

---

### Post by oldfred on 2018-02-07
If booting in UEFI mode, not CSM/BIOS/Legacy you need both UEFI boot entires in UEFI and files/folders in the ESP - efi system partition.
You can just restore boot files in an ESP, but may need to update or recreate UEFI entries in UEFI.
You can use efibootmgr to add UEFI boot entries for Windows & Ubuntu if folders exist in ESP.
Or you can use Boot-Repair's advanced mode and just do a full reinstall of grub. 
I believe similarly running the full set of Windows boot repairs will also update entries.
You may need to houseclean out old entries in UEFI also.

Best not to use Boot-Repair's ISO as it was based on Lubuntu 14.04 and is not dated.
Use Ubuntu live installer and ppa to add Boot-Repair to your live installer.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

See this & more examples in link in my signature on use of efibootmgr
man efibootmgr

---

### Post by johnaaronrose on 2018-02-07
> **oldfred said:**
> If booting in UEFI mode, not CSM/BIOS/Legacy you need both UEFI boot entires in UEFI and files/folders in the ESP - efi system partition.
You can just restore boot files in an ESP, but may need to update or recreate UEFI entries in UEFI.
You can use efibootmgr to add UEFI boot entries for Windows & Ubuntu if folders exist in ESP.
Or you can use Boot-Repair's advanced mode and just do a full reinstall of grub. 
I believe similarly running the full set of Windows boot repairs will also update entries.
You may need to houseclean out old entries in UEFI also.

Best not to use Boot-Repair's ISO as it was based on Lubuntu 14.04 and is not dated.
Use Ubuntu live installer and ppa to add Boot-Repair to your live installer.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

See this & more examples in link in my signature on use of efibootmgr
man efibootmgr

As I said in my last post, I'm not able to boot into Ubuntu Live Installer as I get a message:
Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key".

---

### Post by oldfred on 2018-02-07
Are you selecting the USB flash drive?
Did settings in UEFI get changed? Either UEFI update or some settings may get changed with Windows updates (which may be in back ground).

You need to make sure you have  turned on allow USB boot.
Usually best to have UEFI Secure Boot off.

Otherwise your Ubuntu live installer was damaged and needs to be recreated. If it worked before it should work again. And live installer will boot in any mode, UEFI with Secure Boot, UEFI, or BIOS/CSM/Legacy.
But message seems to be defaulting to internal drive and boot mode does not match install.

---

### Post by johnaaronrose on 2018-02-07
I don't know if I'm selecting the USB flash drive. I can't get into the BIOS using the Del key or even check the Boot order using F10 or any other key.
I created my Ubuntu Live Installer flash drive earlier today and it's Ok as I tried it on another PC earlier. Same goes for my Boot Repair flash drive.

---

### Post by oldfred on 2018-02-07
If you have UEFI fast boot on, that assumes your system has not changed, so it immediately starts boot. You then do not have time to press any key.

Most systems will then use standard UEFI boot with a full power down & boot or cold boot. If laptop you have to also remove battery. Then hold power switch for 10 sec or so, so all power is drained. But you have to then press correct key(s) to get into UEFI when you boot or it will revert to warm reboot using fast boot.

Some have to remove coin battery from motherboard or jumper pins on motherboard. But that also resets all UEFI settings, so you have to redo them. One system had some many settings I have to keep a list.

---

