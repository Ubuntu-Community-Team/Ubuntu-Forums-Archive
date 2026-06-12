---
title: "boot error persist after boot-repair"
date: 2013-02-18
forum: Installation &amp; Upgrades
---

### Post by ciphoenix on 2013-02-18
I installed ubuntu 12.10 alongside windows 8. did the partitioning manually. booting into windows 8 works fine but when I attempt to boot into ubuntu I get an error that a file is missing. I ran boot repair and was given this link [http://paste.ubuntu.com/1679407](http://paste.ubuntu.com/1679407)

---

### Post by oldfred on 2013-02-18
Are you booting Windows from UEFI menu for from grub menu? Last couple of entries in grub menu will not work.

When you boot from UEFI to ubuntu entry do you get grub menu?

Other HPs
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)

            UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)

How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

    Some computers only boot Windows or only boot ubuntu with secure boot off. For those that only boot Windows Boot-Repair renames files as Ubuntu's shim uses the Windows secure boot id.

---

### Post by ciphoenix on 2013-02-18
yes I'm booting from UEFI menu. I've read the post at [http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445) . that was exactly the steps I took to get the system to boot from the live cd. I enabled legacy support. problem is I do get this error when I select ubuntu from the UEFI menu.

file: /NST/AutoNeoGrub0.mbr
status: 0xc0000001
info: the application or operating system couldn't be loaded because a required file is missing or contains errors.

I downloaded the ubuntu secure iso and burnt it. I ran the recommended boot-repair with it but I got the error with the link [http://paste.ubuntu.com/1679407](http://paste.ubuntu.com/1679407)

---

### Post by ciphoenix on 2013-02-19
I couldn't find a solution so I uninstalled. I want to install again. my question now is, can I select the "install alongside windows" option without causing some conflict between it and windows 8?

---

### Post by oldfred on 2013-02-19
Were you trying to boot with EasyBCD. I do not know that. Only the very newest version may work with UEFI, but there is little reason for it with grub. 

With MBR there sometimes was conflicts with grub in the MBR and Windows 7 wanting MBR. So those users that primarily wanted Windows might use EasyBCD. But that required compromises with grub on Ubuntu.

With UEFI evey boot loader goes into efi partition and they all all equial and do not have to overwrite each other. But now we find some UEFI are not correct and have been hard coded to only boot Windows. So Boot-Repair will rename Windows file and use shim/grub which has the same UEFI key as Windows and then from grub menu you boot Windows backup file.

       How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

    
Your install looks ok, did you try running Boot-Repair? It looks like grub-efi did not get installed to efi partition.

---

### Post by ciphoenix on 2013-02-20
yes I tried easyBCD then I got to find out it doesn't work with uefi. I did run boot repair still get same error on boot.

I want to reinstall. my question is, if I choose the install alongside windows option, will it cause any conflicts?

---

### Post by oldfred on 2013-02-20
The reinstall along side just shrinks some partition and creates new ones. Better to shrink Windows from inside Windows with its Disk tools, but never create partitions with Windows for Linux. If you have a Linux install it will create another.

If existing partitions are ok for size and planned use, then you should use manual install or something else and just choose existing / (root) as /. It will find swap automatically. If you have other partitions like /home also choose those. You also have to choose format usually ext4.

Other choice is use gparted to delete existing partitions. Then you should get option to install into the unallocated space or use manual install and create new partitions of a size you prefer.

---

