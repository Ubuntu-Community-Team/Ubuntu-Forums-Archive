---
title: "Grub2 cross-architectural madness"
date: 2013-02-16
forum: Installation &amp; Upgrades
---

### Post by Figasoft on 2013-02-16
Hello everyone,
First, thanks to anyone who will take time to read and hopefully answer this message.
I have been trying to do something which  is apparently against nature, moral and good sense, namely a dual boot with 

- Ubuntu  12.04  64 bit on a gpt disk
- Windows XP 32 bit on a mbr disk

Having no optical drive on this computer, I managed to install the latter from ubuntu inside a virtual machine. It is physically present on the correct disk, and I have no problem launching it again in the VM. 
It has also been detected automatically by Grub, which has added a Windows XP entry. But that entry doesn't work - with the rather familiar errors

"Unknown command drivemap.
Invalid EFI path"

Now after much reading, my first guess was trying to force it to use ntldr. However at first it could not find the module ('File not found' when I added insmod ntldr), and it only started to see it when I copied ntldr.mod to /boot/efi/boot/grub/ 
(It didn't seem to find it in any other directory, including /boot/grub/)
Of course, at that point, I received an 

'Invalid arch independent ELF magic
Unknown command drivemap
Unknown command ntldr'

Some external help led me to suspect that this was due to ntldr.mod being in 32-bits only - indeed, drivemap.mod is also in 32-bits only and it doesn't seem to work all that well. And while all modules in /boot/efi/boot/grub are in 32-bit, all those that are working seem to have 64-bit replicas in /boot/grub (which is not the case for drivemap, and despite the fact that ntldr.mod was not found when copied to that directory)

Now, I am thinking that there is simply no way to have grub load both of my systems on their respective disks. And for some mysterious reason, although the mbr on the windows drive seems good (i have made the partition bootable and used fix-mbr and whatnot), I cannot simply bypass the whole grub deal by using the multiboot from bios at startup, since it seems unable to launch what it calls Windows Boot Manager.

You Jedis are therefore my only hope.

Edit: Oh I have also heard of some mythical solution involving a 32-bit loader and eficross to make it able to load my ubuntu, but all my research along this path has been doomed by the total lack of documentation about that eficross thing - unless it is too well hidden for my google-fu.
Also, if you can think of any place more appropriate for this question, please do not hesitate to redirect me.

---

### Post by GerMulvey on 2013-02-16
Is the drive your trying to install ubuntu to bigger than 2.2TB because if not then your better off converting the drive back to mbr as gpt will not really give you any benefit tbh
I tried to do it on a 750gb drive but found it caused problems and in the end just went back to using standard msdos partition table

---

### Post by oldfred on 2013-02-16
I used to boot Ubuntu from gpt drive with BIOS and XP from MBR drive. But when I got my SSD I had to change BIOS to AHCI for trim to work,  and my XP did not have AHCI drivers. Easiest to install AHCI drivers with new install of XP, so I finally stopped booting XP.
But XP will not work with gpt drives.

And if you installed Ubuntu in UEFI mode, you cannot dual boot with XP. UEFI or BIOS write somewhat different system configuration data to hard drive for system to use and they are not compatible. Or XP cannot read UEFI system data.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

If Ubuntu is UEFI, you may be able to go into UEFI menu and change to BIOS or compatiblity mode and then boot XP in BIOS mode. Bit of a hassle but XP has limited life now anyway.

---

