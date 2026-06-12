---
title: "Windows 8 + Ubuntu (Can't Boot)"
date: 2013-10-16
forum: Installation &amp; Upgrades
---

### Post by Mohammed_Ibrahim on 2013-10-16
Hello,

I've been using Ubuntu for a while and liked it. I bought a new computer and installed Ubuntu into it, I'll leave the old computer with Windows only.

So, I removed the Ubuntu partition from the Windows 8 Disk Management, and restarted my computer, now it shows a GRUB Terminal with 'grub>'.

I don't have the Windows 8 Recovery Disk. I downloaded Ubuntu into a DVD from another computer, but when I insert the disk, nothing happened.

Is there a way to return the MBR back to Windows?

Thanks.

Edit:
Terminal Title = GNU GRUB version 1.99-21ubuntu3.10

---

### Post by oldfred on 2013-10-16
If a BIOS based system with MBR.
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Boot-Repair is a gui based script that is probably the easiest way. You can install to any working Linux, Live installer or download as a repair CD.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

You can manually install the lilo boot loader which from MBR works just like Windows.
      
 Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader to boot partition with boot flag (Windows).

---

### Post by Mohammed_Ibrahim on 2013-10-16
Hello,

I installed Ubuntu again and everything worked.
Then, I went into Windows, used EasyBCD to write the MBR, and then deleted the Ubuntu partition again.
Now, when I restarted my computer, I'm getting the grub terminal again!

---

### Post by oldfred on 2013-10-16
I do not know EasyBCD. But you should just install a Windows boot loader to MBR if your system is BIOS/MBR and not new UEFI/gpt type system.

---

### Post by Mohammed_Ibrahim on 2013-10-16
My system has a pre-installed Windows, so it's a UEFI/gpt type.

---

### Post by oldfred on 2013-10-16
Then I would not use EasyBCD. They have fixed it to work with UEFI but old versions did not. And it is not required as all systems install separate boot files in efi partition and you choose from UEFI menu which system to boot. And grub will give you choice to boot Windows from grub menu. No need for another boot manager. 

Ignore all the BIOS based instructions above. You need UEFI booting not BIOS booting. If you installed Ubuntu in BIOS/CSM mode you can use Boot-Repair to convert to UEFI or just reinstall. How you boot install media is how it installs, so boot installer in UEFI mode.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

More detail & links to lots of info in link in my signature.

---

### Post by Mohammed_Ibrahim on 2013-10-17
BootInfo Report:
[http://paste.ubuntu.com/6249304/](http://paste.ubuntu.com/6249304/)

---

### Post by oldfred on 2013-10-17
You should just be able to go into UEFI and boot Windows. 
But part of issue may be that Boot-Repair has run the rename function. That is for those systems that will not boot Ubuntu and only boot Windows. So it renames the Windows file to really be grub2's shim file that has the Microsoft signing key and will boot in secure boot mode and then from grub menu you boot Windows backup file.
If you can directly boot Ubuntu you do not need rename or if uninstalling, you would not want rename.

  /EFI/Microsoft/Boot/bkpbootmgfw.efi 
 /EFI/Microsoft/Boot/bootmgfw.efi
Above from changes from this on line 856 of pastebin script:
Save and rename /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi (/boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi)
cp /boot/efi/EFI/ubuntu/shimx64.efi /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi

      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 
You can test if your system will boot Ubuntu directly by removing the rename function and see if Ubuntu can be booted from UEFI menu. If so you would not need rename.

If changing back does not work.
      
 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

---

