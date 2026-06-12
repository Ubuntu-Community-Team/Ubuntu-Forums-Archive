---
title: "Non bootable Windows 8.1 after clean install of Ubuntu 14.04"
date: 2014-05-25
forum: Installation &amp; Upgrades
---

### Post by ilia_avramov on 2014-05-25
I did a clean install of Ubuntu 14.04 on my Acer Aspire One 756. There was Ubuntu 13.10 but instead of upgrade I always prefer a clean install. Now I have working Ubuntu (and MInt 16 on another partition) but when I try starting windows 8.1 from GRUB I get this message "no such device: d65cb800-ac31-45b8-a67d-94dd8a1754f5". The same message I get if I choose   WINDOWS BOOT Manager (ST320LT020-9YG142) from the boot menu in BIOS. Enabling secure boot doesn't help, neither changing boot order in BIOS. BOOT-REPAIR can't fix the problem.
 This is info from BOOT-REPAIR: [http://paste.ubuntu.com/7511917/](http://paste.ubuntu.com/7511917/). The language is bulgarian.

---

### Post by oldfred on 2014-05-26
Is script not showing efi files in your sda2 efi partition or are they missing?

You show Windows in UEFI boot mode and one install booting with BIOS and grub in MBR with /boot partition in sda6. Install in sda9 uses UEFI.

Better if all systems are in same boot mode, either UEFI or BIOS. But you can boot from UEFI menu if not in same mode. But may have to turn on or off UEFI boot mode or CSM/BIOS boot mode to match that install.

You cannot boot from grub menu an install in a different boot mode.

---

### Post by ilia_avramov on 2014-05-26
All systems are in the same UEFI boot mode, secure boot is off, bootloader is installed in /dev/sda. I can see EFI files in /boot/efi/, because /sda2 is mounted in /boot/efi. There are folders Boot,EFI,Microsoft,Ubuntu and bootsect.bak . I think that sda2 is in a healthy condition. But I'm worryed about sda3. I don't even know what is it. GParted says unknown file system. It is 128 MB big and has flags msftres. Probably it's UUID is d65cb800-ac31-45b8-a67d-94dd8a1754f5 and  when I try to boot Windows it says:    no such device: d65cb800-ac31-45b8-a67d-94dd8a1754f5 and GRUB RESCUE>. Actually GPARTED doesn't show it's UUID but I suppose it's sda3. There is another partition with unknown UUID and it is sda7. It is bios_grub. All partitions beyond sda4 are made by me when I bought this comp a year ago and on the same evening I installed Ubuntu 13.04 following instructions of dual boot ubuntu and windows8. Now /boot and bios_grub are not necessary any more but the partitions are there and I use them. If sda3 is brocken for some reason, what can I do?

---

### Post by oldfred on 2014-05-26
Microsoft reserved is requied by Windows. It is a scratch area, as with gpt the space between protective MBR and rest of drive does not exist. With MBR the area between MBR and first partition is used by Windows for same purpose. 
       Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Similarly if you install grub in MBR mode it needs a bios_grub partition. Normally with MBR core.img is written just after MBR, but that space does not exist with gpt. Only required if booting Ubuntu in BIOS mode.

Both Windows reserved and bios_grub are unformatted, so some tools do not correctly show them. Since not formatted they would not have UUID, but will have gpt GUIDs and flags that in effect show a conversion from GUID to something we understand. Near bottom are the GUIDs and names/labels they are.
      
 [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

Is not your Mint BIOS booting (then needs bios_grub partition), but Ubuntu UEFI booting (uses efi partition)? And you have to choose which way to boot in UEFI menu not grub. Once you start booting in one mode you cannot change to another, or grub menu cannot switch boot modes as you already have started booting in one mode.

---

### Post by ilia_avramov on 2014-05-26
Hmm,interesting! It seems that my Mint is in BIOS mode because /sys folder is empty. In Ubuntu there is /sys/firmware/efi, so it must be in EFI mode if this is the way to check which mode it boots. But in Ubuntu I used BOOT-REPAIR, so probably it converted to EFI mode. Both Ubuntu and Mint work perfectly, only W8 complains of a missing device. In BIOS there are options UEFI and Legasy BIOS. It is set to UEFI.

---

### Post by oldfred on 2014-05-26
If fstab shows the mount of the /efi partition then it is booting with UEFI. 
As that is where it will reinstall grub boot files. 
If fstab does not show an efi partition mount or it is commented out with #, then it is BIOS boot or converted to BIOS boot by Boot-Repair.

Is the Windows issue from UEFI boot of Windows or grub menu boot of Windows.
If Windows is hibernated, or fast boot still on, or needs chkdsk or has other issues you may be only able to boot from UEFI menu and may need f8 to get into repairs. Best to have a Windows repairCD or flash drive for those times when that does not work.

Grub really only boots a Working Windows that is not hibernated. And it has to be in the same boot mode or since Windows is UEFI, Ubuntu must be in UEFI boot mode.
Or if booting in BIOS mode to Mint that version of grub will not boot any install in UEFI mode. Boot-REpair may be able to convert it to UEFI also.

---

### Post by ilia_avramov on 2014-05-27
COMPLETE SUCCESS! Luckily I have Mint 16 on another partition. I booted  it and installed BOOT-REPAIR. It immediately fixed GRUB2 reporting no  errors: [http://paste2.org/wEfgggKK](http://paste2.org/wEfgggKK)
This shows that Ubuntu 14.04  installs buggy GRUB2. This problem is not my fault. Before the fix I  checked fstab in Ubuntu and in Mint. They both show UEFI boot mode.  There is no reason for this issue. I have installed Ubuntu tens of times  before and I never faced a problem like this.
Now I have 3 working OSes. And I'll keep Mint 16 even when it's support expires because this Ubuntu is very buggy.

---

### Post by oldfred on 2014-05-27
You have this:
 /EFI/Microsoft/Boot/bkpbootmgfw.efi 

      
 Boot_Repair rename Windows bootmfg.efi. But cannot boot Windows from UEFI only grub 
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

You may need it if you have an UEFI that the vendor modified to only boot Windows. If you can boot either ubuntu or HDD entry then better to undo the 'buggy' UEFI.


>  BootOrder: 0004,0001,0000
Boot0000* Windows Boot Manager HD(2,c8800,96000,b51ac764-63dd-40a7-81e8-ca1de515c277)File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0001* HDD: HD(2,c8800,96000,b51ac764-63dd-40a7-81e8-ca1de515c277)File(EFI[COLOR=#ff0000]ubuntugrubx64[/COLOR].efi)RC
Boot0002* BRCM MBA Slot 0400 v15.0.11 BIOS(80,500,00)................a........ ..E............ .............................
Boot0003* ST320LT020-9YG142 BIOS(2,500,00)................-.o.......o.A.o........................................
Boot0004* ubuntu HD(2,c8800,96000,b51ac764-63dd-40a7-81e8-ca1de515c277)File(EFI[COLOR=#ff0000]ubuntushimx64[/COLOR].efi)



---

