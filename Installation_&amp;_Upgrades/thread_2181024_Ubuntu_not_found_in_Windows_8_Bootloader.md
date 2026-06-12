---
title: "Ubuntu not found in Windows 8 Bootloader"
date: 2013-10-15
forum: Installation &amp; Upgrades
---

### Post by Ryan_Lagasse on 2013-10-15
My Computer's Native OS: Windows 8
OS installed: Ubuntu 13.10 Saucy Salamander

Video used as a guide: [https://www.youtube.com/watch?v=PK7gWIkAY7s](https://www.youtube.com/watch?v=PK7gWIkAY7s)

I wanted to install Ubuntu as I had never before used a Linux Operating System. I first shrinked Window's C Drive to create room for the 4 partitions I would make for Ubuntu (Root, Home, Boot and a Swap). After booting from a LiveUSB with pendrivelinux, I then created the partitions on my storage device and installed Ubuntu.

I figured that as soon as that was finished, Ubuntu would be added to Windows bootloader and I would be good to go. Instead, I have to hit ESC and run Ubuntu as a device under device options OR select a device under the bootloader (all options listed under bootloader).

I recently downloaded EasyBCD in order to add Ubuntu to the bootloader but am having no luck. I have tried selecting the root and boot partitions to make a new GRUB2 Linux entry but it returns with an error so I deleted them.

How can I add Ubuntu to my list of Operating Systems in the Windows bootloader? Should I make one of my partitions have a letter drive (I cannot even see it from Windows)?
[U]
My Disk Management (Windows 8)[/U]

9 Partitions total
1 - 400 MB Healthy (Recovery Partition) *
2 - 260 MB Healthy (EFI System) *
3 - (C:) 465.78 GB NTFS Healthy (Boot, Page File, Crash Dump, Primary Partition)
4 - 191 MB Healthy (Primary Partition) - My boot partition installed as logical, formatted ext 4
5 - 7.63 GB Healthy (Primary Partition) - My swap partition installed as logical
6 - 38.15 GB Healthy (Primary Partition) - My root partition installed as primary, formatted ext 4
7 - 57.22 GB Healthy (Primary Partition) - My home partition installed as logical, formatted ext 4
8 - 334.44 GB Unallocated
9 - RECOVERY (D:) 27.34 GB NFTS Healthy (OEM Partition)

* I have no idea what the first two partitions are on this HDD

_My Boot Menu Entries (from EasyBCD)_

1 - Internal Hard Disk or Solid State Disk (Goes back to OS selection when clicked)
2 - Internal Hard Disk or Solid State Disk (Boots Ubuntu)
3 - Internal Hard Disk or Solid State Disk (Boots Ubuntu)
4 - USB Drive (UEFI) (I don't have a USB Drive in at the moment...)
5 - Internal CD/DVD ROM Drive (UEFI) (Not using a disk either...)
6 - HP RM (ESP)
7 - Windows 8 (DEFAULT)

---

### Post by oldfred on 2013-10-15
You should not need EasyBCD. It is a bootmanager that uses grub4dos. But with UEFI you have UEFI which is a boot manager and grub2 which is a boot manager and a boot loader.

With UEFI you do not have one MBR that BIOS always uses to boot from and last install then controls booting. With UEFI you have an efi partition and every system you install adds a separate folder with its boot files into that folder. You then need to use UEFI to choose which to boot from. (that is unless you install Ubuntu in CSM/BIOS/Legacy boot mode).

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Ryan_Lagasse on 2013-10-25
I ran Boot Repair off of my LiveUSB and it prompted me to input commands to the terminal. After that, I reset my computer to find that there had been very few noticible changes to Ubuntu besides the addition of more boot options when selecting Ubuntu as my OS. Posted is the BootInfo Report: [http://paste.ubuntu.com/6304193/](http://paste.ubuntu.com/6304193/)

---

### Post by oldfred on 2013-10-26
You should be just able to set ubuntu as default boot in UEFI, not Windows. 
It looks like that may have been done?

line 1453 in your BootInfo report:
>  BootOrder: [COLOR=#ff0000]0000[/COLOR],2001,3001,3000,3002,2002,2003
Boot[COLOR=#ff0000]0000[/COLOR]* ubuntu	HD(2,c8800,82000,59fabae8-8683-4404-9461-e6bcbd261940)File(EFIubuntugrubx64.efi)
Boot0001* Windows Boot Manager	HD(2,c8800,82000,59fabae8-8683-4404-9461-e6bcbd261940)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.



HP has all of its efi files to boot into HP utilities in the efi partition. Boot-Repair sees efi boot files and adds all of them to grub menu. You may not need nor want those but can just manually edit 25_custom to remove them.

 # Edit descriptions used by Boot-Repair or remove entire boot stanza
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkup25_custom
gksudo gedit /etc/grub.d/25_custom
#Then do:
sudo update-grub

See also link below in my signature.

---

