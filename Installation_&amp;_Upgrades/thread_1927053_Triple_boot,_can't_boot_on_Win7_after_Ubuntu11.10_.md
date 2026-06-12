---
title: "Triple boot, can't boot on Win7 after Ubuntu11.10 install"
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by asheenlevrai on 2012-02-17
Hello,

I am familiar with setting up triple boot on macbooks using refit. I did it several times in the past.

Now, I tried to setup a triple boot with
1) OSX 10.7 (x64)      on Sda2
2) Ubuntu 11.10 x64    on Sda3
3) Windows 7 pro (x64) on Sda4
on a Macbook Air 3,2

I 1s installed Lion (on Sda2) and got rid of the "rescue" partition.
I then created the 2 partitions (Sda3 & Sda4) I needed for the other OSs.
I then Installed Win7 on the last partition (Sda4).
After Syncing the EFI and the MBR (using refit) everything was fine (could boot on both OSs).

I then Installed Ubuntu 11.10 x64 on the remaining partition (Sda3) taking care of installing the bootloader (Grub2) on the same partition (Sda3). Now I have the following problem:
 - When I boot on Sda2, OSX launches (OK)
 - When I boot on Sda3, Grub launches and proposes to boot on
 _________Ubuntu (+ safe mode and mem86+) (OK)
 _________OSX 32bits (-> fails but I don't care)
 _________OSX 64bits (-> fails but I don't care)
 _________Windows 7 (-> fails)

 - When I boot on Sda4, Grub launches again (???)

I don't know why grubs proposes to boot on the other OSs.
I cannot boot on Windows 7.

Here is the output from partition inspector:

[B]*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    177362759  Mac OS X HFS+
 3      177625088    333885439  Basic Data
 4      333885440    490233855  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1           39  ee  EFI Protective
 2             40       409639  0b  FAT32 (CHS)
 3         409640    177362759  af  Mac OS X HFS+
 4 *    177625088    333885439  83  Linux

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)
 Listed in MBR as partition 2, type 0b  FAT32 (CHS)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 3, type af  Mac OS X HFS+

Partition at LBA 177625088:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 4, type 83  Linux, active

Partition at LBA 333885440:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 4, type Basic Data[/B]
______________________________

Apparently my windows partition got ejected of the MBR somehow...

Does anyone know what I should do?

Thanx a lot in advance for your help.

-a-

---

### Post by asheenlevrai on 2012-02-19
I followed the tutorial at:
 [http://jonsview.com/fixing-mbr-tables-on-imac-or-mbp-triple-boot-setups](http://jonsview.com/fixing-mbr-tables-on-imac-or-mbp-triple-boot-setups) 
and set up the MBR table as:
1: ee EFI protective (1-39)
2: OSX
3: Ubuntu
4: Windows
I droped the FAT32 EFI system partition (40-409639)

Tx
-a-

---

