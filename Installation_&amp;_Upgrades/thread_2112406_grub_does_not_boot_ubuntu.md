---
title: "grub does not boot ubuntu"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by kokoor on 2013-02-04
Hi,

I recently tried to configure my laptop (lenovo S430) with uefi to dual boot. The laptop came with  windows 8. I partitioned the disk and installed ubuntu 12.10.  I followed the instructions here [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) to setup grub for dual boot. 

Dual boot does not work. The grub menu is listing:
1)Windows UEFI bkpbootmgfw.efi 2)Windows Boot UEFI loader 3)EFI/Lenovo/Boot/bootmgf.efi 4)Windows 8 (loader) (on /dev/sda4) 5)System setup

So no ubuntu.
Boot repair provided this infomration:
[http://paste.ubuntu.com/1610298/](http://paste.ubuntu.com/1610298/)

I am not sure how to implement correctly the last instruction from the URL :
"Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/grubx64.efi file!"

I would like to be able to select windows 8 or ubuntu 12.10 from a menu at start up. 

Thanks

---

### Post by oldfred on 2013-02-04
Welcome to the forums.

I have not understood some details on Lenovo UEFI.
You have two listing of boot entries. Is one recovery and the other standard? Or one mostly hardware and the other systems, although both seem to have both type.

Line 1227 boot order
BootOrder: 0009,000C,000A,0011,000B,0007,0008,000D,000E
Where 0009 is 
 ATAPI CD0

And at line 1248 boot order
BootOrder: 0012,0009,000C,000A,0011,000B,0007,0008,000D,000E
where 0012 is 
ubuntu

so somewhere in your UEFI menu should be entry 0012 that says ubuntu.

Can you boot from that.

---

### Post by kokoor on 2013-02-05
Indeed there is an "ubuntu" entry, but is under devices in "boot" under setup. In grub there is no entry "ubuntu". I think this Boot order is the order I have put the devices in the setup. However even if I put "ubuntu" at the top of the list it doesn't make any difference because it takes me to the grub menu, where ubuntu is not listed.

---

### Post by kokoor on 2013-02-05
How can I make my laptop boot from 
sda2/EFI/ubuntu/grubx64.efi file?

---

### Post by kokoor on 2013-02-05
Actually I see that there an entry in boot.cfg (line 391)

menuentry "efi/EFI/Boot/bootx64.efi" { search --fs-uuid --no-floppy --set=root 519a635f-1d01-4bed-b5c8-fb2964975127 chainloader (${root})/efi/EFI/Boot/bootx64.efi

so the file 
/efi/EFI/Boot/bootx64.efi
is listed in boot.cfg.

However I see that there are two other entries 
menuentry "efi/EFI/Lenovo/Boot/bootmgfw.efi" { search --fs-uuid --no-floppy --set=root 519a635f-1d01-4bed-b5c8-fb2964975127 chainloader (${root})/efi/EFI/Lenovo/Boot/bootmgfw.efi }  

menuentry "efi/EFI/Microsoft/Boot/bootmgfw.efi" { search --fs-uuid --no-floppy --set=root 519a635f-1d01-4bed-b5c8-fb2964975127 chainloader (${root})/efi/EFI/Microsoft/Boot/bootmgfw.efi } 

menuentry "efi/EFI/Boot/bootx64.efi" { search --fs-uuid --no-floppy --set=root 519a635f-1d01-4bed-b5c8-fb2964975127 chainloader (${root})/efi/EFI/Boot/bootx64.efi }


So bootx64.efi is 3rd in the order under the same root. Should I change his order manually?

---

### Post by kokoor on 2013-02-05
new development: after following the instructions in
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I managed to get to a menu after restart that had ubuntu option on it. after choosing it I booted into my ubuntu successfully! I thought I was done. But then I tried booting into windows, which worked fine, but after another restart the whole grub menu was gone..... Overwritten by windows boot manager?

---

### Post by oldfred on 2013-02-05
Are you getting to UEFI menu from Windows entry? You need to get to UEFI entry from UEFI directly not thru windows. As long as you use Windows to get to UEFI menu then Windows is the default for UEFI to boot. 
You want ubuntu (or the grub efi entry) to be the default from UEFI.

You should be able to directly go to UEFI menu with UEFI setup key for your system. Every vendor is different. And key may not work if fast boot is on as that  tries to skip UEFI loading and go straight to Windows and then you only can get to UEFI setup from the Windows menu.
So make sure UEFI has fast boot off.

---

