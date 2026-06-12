---
title: "64 bit boot problems"
date: 2013-11-08
forum: Installation &amp; Upgrades
---

### Post by tougeattackitr on 2013-11-08
hello all i just installed latest ubuntu 64bit in my laptop(i7 8giga ram 640 nvidia)

the problem is that the OS wont boot at the begining and i have to  hit f12 to select boot divices and then select a device called "ubuntu" to start booting

i went to the bios and i wasnt able to find that device in my hd list... i dont know what to do i dont want to hit f12 every time to boot

is there any solution for this?

also secure boot is disabled

---

### Post by oldfred on 2013-11-08
Welcome to forums.

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

### Post by ubfan1 on 2013-11-08
Install the efibootmgr package.  It allows you to rearrange the efi boot order.

---

### Post by tougeattackitr on 2013-11-08
output of efibootmgr
mayh3m@revers3:~$ sudo efibootmgr 
Timeout: 1 seconds
BootOrder: 0007,0008,0009,0000,000A
Boot0000* ubuntu
Boot0007* Hard Drive 
Boot0008* CD/DVD Drive 
Boot0009* Network Card 
Boot000A* UEFI: Hard Drive 

i got problems on installing boot-repair

---

### Post by oldfred on 2013-11-08
You should be able to just use efibootmgr to change boot order to make 0000 first.

       sudo efibootmgr -v

[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

See this setting

-o | --bootorder XXXX,YYYY,ZZZZ,...     explicitly set BootOrder (hex)

---

### Post by tougeattackitr on 2013-11-09
i tryed that but my system frozes and i have to shutdown my pc

---

### Post by oldfred on 2013-11-09
You have to type in all the devices with the correct hex numbers as shown by the -v command, just in your prefered order.

---

### Post by tougeattackitr on 2013-11-09
yep i did that then did a restart and my pc said BOOTMGR not found hit cltr+alt+del but then again when i hit f12 and choose ubuntu manualy i can boot fine

---

### Post by oldfred on 2013-11-10
Is the bootmgr not found a UEFI/BIOS error? Then you have a buggy UEFI that has been manually modifed to only boot Windows but description. The f12 must bypass that bit of code so you can boot.

       Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

They debugged this one to see details:

 Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[URL="http://mjg59.dreamwidth.org/20187.html?thread=774619"]http://mjg59.dreamwidth.org/20187.html?thread=774619

[/URL] Rename will occure if Boot-Repair sees Windows kernel issues, but may not always be required. 
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]?
Rename option now under advance choices - updated Boot-Repair so that by default it will put grub/shim in EFI/BOOT/bootx64.efi only
[http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984](http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984)
 available as a "Rename Windows EFI files" option in the Advanced Options for the few UEFI that are modified to only Boot Windows efi file.
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply

      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
     
[URL="http://mjg59.dreamwidth.org/20187.html?thread=774619"]
[/URL]

---

### Post by tougeattackitr on 2013-11-13
i dont think its modified to work with windows only becouse ubuntu or any other linux os that is 32 bit is working fine

---

### Post by oldfred on 2013-11-13
If you install any 32 bit versions those only install in BIOS boot mode, not UEFI. So they would work. But some UEFI are modified to only boot Windows.

---

