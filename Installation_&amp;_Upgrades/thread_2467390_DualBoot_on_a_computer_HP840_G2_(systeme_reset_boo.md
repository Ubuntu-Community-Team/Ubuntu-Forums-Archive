---
title: "DualBoot on a computer HP840 G2 (systeme reset bootordernotfound)"
date: 2021-09-25
forum: Installation &amp; Upgrades
---

### Post by sc4r on 2021-09-25
Hello I installed ubuntu 20.04.1 LTS on a usb key with rufus, I have windows 10 installed and I will put linux ubuntu next to it.
I followed the steps of a video and I stopped when we must remove the usb key and hit the enter key (after installation)
Except that after I have a message in loop which tells me:


System BootOrder not found. Initializing defaults.
Creating boot entry "BootXXXX" with label "ubuntu" for the file "\ EFI \ ubuntu \ shimx64.efi"
Reset System


I have not activated the Secureboot, I am doing this with a hybrid UEFI boot (CSM) and the boot order is:
Usb hard drive
generic USB device
PCle / M.2 SSD Hard drive
OS boot manager
ethernet card ipv4
ethernet card ipv6


I have tried to see on some forum and I did not understand how to successfully solve this problem.
I want to have the choice to choose between windows 10 and ubuntu

---

### Post by tea for one on 2021-09-25
Can you still boot into Windows 10?
If you can, please navigate to System Information > System Summary > BIOS mode > UEFI (hopefully)

From the information supplied, you may have mixed mode installations?

More info here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by sc4r on 2021-09-25
when i try to boot on the notebook hard drive it tells me hard drisk (3F0) boot device not found please install on operating system on hard disk


I think I no longer have windows 10 ****

---

### Post by tea for one on 2021-09-25
> **sc4r said:**
> when i try to boot on the notebook hard drive it tells me hard drisk (3F0) boot device not found please install on operating system on hard disk
I think I no longer have windows 10 ****

That doesn't look promising.
I do not know what 3FO is?

The first priority is to try and boot into Windows so that you are back to square one.
Do you have data backups?
You can boot into a live Ubuntu session and backup your data, if necessary.

There are various other things to try:-

Power off the PC completely.
Remove and re-install the battery (if possible).
Open up the UEFI firmware and reset to default.
Remove and re-install the M2 SSD.
Do you have a UEFI shell to select boot options?
Download a Windows 10 ISO and make a repair disk.

---

### Post by sc4r on 2021-09-25
[SIZE=4]I managed to put linux I saved a file to see if it will be saved I restarted and it works
for windows it will be hard I have not managed to put it back[/SIZE]

---

### Post by tea for one on 2021-09-25
You can now boot into Ubuntu, create and save a file - that is progress.

Can you open a terminal, enter this command and post the output:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```
This will tell us how Ubuntu is installed.

---

### Post by sc4r on 2021-09-25
The terminal replied "UEFI mode"

it's very good we can do it !

---

### Post by MAFoElffen on 2021-09-26
@Tea for One...

On a training break right now. Have him run the boot-repair and system-info reports. That will show you the layouts, what efi boot files are in /dev/sdxx/efi/xxx and what the efi boot default is set at right not...

And more importantly, that his Windows install is still there.

---

### Post by sc4r on 2021-09-26
I made an info system report [https://paste.ubuntu.com/p/vxWXH8c2GP/](https://paste.ubuntu.com/p/vxWXH8c2GP/)

---

### Post by tea for one on 2021-09-26
Have you tried to boot Windows via the UEFI boot menu?
Power on and repeatedly tap F9 - do you see the Windows Boot Manager?

---

### Post by yancek on 2021-09-27
Linue 5 of boot repair shows that you have windows boot code in the MBR of that drive.  Is this system an upgrade from an earlier windows?
Beginning at line 13, boot repair shows the content of sda2 which is the EFI partition for your systems.  Line 27 shows your windows EFI boot file so it is there.
Starting at line 31, you will see the 2 windows partitions so your windows partitions are also there.

Do you know how to access the BIOS Boot Options?  Do you know how to access the BIOS to make permanent changes?
In boot repar, lines 81-84 are identical and boot Ubuntu (or should).  You should never need identical entries in the BIOS and this is probably the result of reading online a method to get UBuntu to boot by overwriting the windows entry.  You have/had windows installed in UEFI and the entry on line 78 should be the default to boot windows.  Have you run:  sudo update-grub from Ubuntu? .

---

### Post by tea for one on 2021-09-27
@yancek

Some parts of the report confused me also:-

[COLOR="#0000FF"]Line 5[/COLOR] - Windows 7/8/2012 is installed in the MBR of /dev/sda 
This implies a Legacy install

[COLOR="#0000FF"]Line 27[/COLOR] - /efi/Microsoft/Boot/bootmgfw.efi 
This indicates a UEFI install

[COLOR="#0000FF"]Line 78[/COLOR] - Boot0000* Notebook Hard Drive	BBS
I think that this only identifies the Disk because:-
[COLOR="#0000FF"]Line 75[/COLOR] - BootCurrent: 0000
[COLOR="#0000FF"]Line 58[/COLOR] - OS#1:   L'OS actuellement utilisé - Ubuntu 20.04.3 LTS CurrentSession on sda5

Anyway, I agree with you that the OP should try:-

[LIST]
[*]Access the UEFI boot options to see if Windows Boot Manager is visible
[*]Update Grub to see if Windows is added to Grub
[*]Remove the duplicate entries in efibootmgr
[*]
[/LIST]

---

### Post by sc4r on 2021-09-27
my pc goes off and on again with the message "reset system" I cannot access windows

---

### Post by tea for one on 2021-09-27
Can you still boot into Ubuntu?

---

### Post by MAFoElffen on 2021-09-29
This has gone on for 4 days and 14 posts so far..\. I can see from the disk-repair script, that it has EFI files that follow HP naming conventions. I also see the HP UEFI system and firmware setup and diagnostics startup files there. Being I just updated and re-certified my HP Certs... I recognize those. LOL

It looks like it was originally Windows 7, will an MBR disk (not GPT), so, even though it is UEFI, has no "real" physical EFI partition. So the MBR sector contains the Windows pointer.

That laptop came out in 2014 and came pre-loaded with either Win 7 or Win 8.1... So, either way, the OP upgraded it to Windows 10. On lines 75 and 77... The current boot is set at 0000, but the only entry in boot order is 0006(???) There is no entry in the boot order for any of the windows startup files, nor for the HP system or HP Diagnostics startup files. He needs to use efibootmgr to reset his boot order.

But YES... If he uses <F9>while the logo/boot process is going on, it should bring up his EFI boot menu, where he can try to boot windows, Ubuntu, The HP Setup, or HO Diagnostics. His Setup should also come up with eithether <Esc> or <Fn><Esc>... There was one model that used that...

If you boot from your Ubuntu LiveCD, and bring up a Treminal seesion, what is the output from 
```

sudo efibootmgr -v

```
What I saw on the report was this:
```
efibootmgr -v BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0006
Boot0000* Notebook Hard Drive	BBS(HD,,0x0).......................................................................
Boot0001* Notebook Ethernet	BBS(128,,0x0)........................E..............................................
Boot0002* Notebook Ethernet	BBS(128,,0x0)........................E..............................................
Boot0003* ubuntu	HD(2,GPT,17e8e658-fbdf-4bb8-ac11-4260db3f1aca,0x40800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0004* ubuntu	HD(2,GPT,17e8e658-fbdf-4bb8-ac11-4260db3f1aca,0x40800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0005* ubuntu	HD(2,GPT,17e8e658-fbdf-4bb8-ac11-4260db3f1aca,0x40800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0006* ubuntu	HD(2,GPT,17e8e658-fbdf-4bb8-ac11-4260db3f1aca,0x40800,0x32000)/File(\EFI\ubuntu\shimx64.efi)

```

...which if you did this
```

sudo efibootmgr -o 0000,0003,0001,0002
sudo efibootmgr -b 0005 -B
sudo efibootmgr -b 0006 -B

```
That would reset the boot order to Windows, Ubuntu, NIC1, NIC2. Then the next two will delete the duplicated entries in the boot menu...

Doing this
```

sudo efibootmgr -c -p 2 -L "Grub" -l '/Boot/grubx64.efi'
sudo efibootmgr -c -p 2 -L "Memory" -l '/Boot/mmx64.efi'
sudo efibootmgr -c -p 2 -L "BIOS Setup" -l '/HP/BiosUpdate/HpBiosUpdate.efi'
sudo efibootmgr -c -p 2 -L "Windows" -l '/Microsoft/Boot/bootmgr.efi'

```
After adding those entries in, then do
```

sudo efibootmgr -v

```
...to see the entries.

What i would do then is to reboot, and on the startup, bring up the Boot Menu and try each entry, to set which you want to add to your boot order.

---

### Post by oldfred on 2021-09-29
In addition to looking at boot loaders, whether in MBR or in the ESP - efi system partition, with Windows you must also look at drive's partitioning.
Windows only boots in UEFI mode from gpt partitioned drive.
Windows only boots in BIOS/CSM/legacy boot mode from MBR(msdos) partitioned drives.

Since drive is gpt & you have /efi/Microsoft/Boot/bootmgfw.efi in ESP, Windows must be UEFI boot.

You do not show a typical Windows boot entry in UEFI. You should be able to add one with efibootmgr.
See also:
man efibootmgr

Typical New Windows entry - assumes default sda1  add -d /dev/sda -p 2 if sda2:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

Your New Windows entry - with added -d /dev/sda -p 2 since sda2: 
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" -d /dev/sda -p 2

Confirm entry it there:
sudo efibootmgr -v

---

### Post by MAFoElffen on 2021-09-30
@oldfred

Snip from his pastebin
```

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/grubx64.efi 
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/HP/BiosUpdate/CryptRSA32.efi 
                       /efi/HP/BiosUpdate/CryptRSA.efi 
                       /efi/HP/BiosUpdate/HpBiosUpdate32.efi 
                       /efi/HP/BiosUpdate/HpBiosUpdate.efi 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi 
                       /efi/Microsoft/Boot/memtest.efi

===================================== UEFI =====================================

BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
No EFI in dmseg.
SecureBoot disabled.

efibootmgr -v
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0006
Boot0000* Notebook Hard Drive    BBS(HD,,0x0).......................................................................
Boot0001* Notebook Ethernet    BBS(128,,0x0)........................E..............................................
Boot0002* Notebook Ethernet    BBS(128,,0x0)........................E..............................................
Boot0003* ubuntu    HD(2,GPT,17e8e658-fbdf-4bb8-ac11-4260db3f1aca,0x40800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0004* ubuntu    HD(2,GPT,17e8e658-fbdf-4bb8-ac11-4260db3f1aca,0x40800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0005* ubuntu    HD(2,GPT,17e8e658-fbdf-4bb8-ac11-4260db3f1aca,0x40800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0006* ubuntu    HD(2,GPT,17e8e658-fbdf-4bb8-ac11-4260db3f1aca,0x40800,0x32000)/File(\EFI\ubuntu\shimx64.efi)

f7a57b08bc7c1c85417ae4cea582d1d4   sda2/Boot/bkpbootx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda2/Boot/bootx64.efi
85fa9d77b929ec4231aba29476574eb6   sda2/Boot/fbx64.efi
1476c8ed1ce8271aab2fbe89d534cfa4   sda2/Boot/grubx64.efi
469e608783843a701d172242f016c79c   sda2/Boot/mmx64.efi
fa1bf1a7f90a852abe0bdbd089b7f1b0   sda2/ubuntu/grubx64.efi
469e608783843a701d172242f016c79c   sda2/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda2/ubuntu/shimx64.efi
1b8c0684ede8539ccc205cf7a750eca3   sda2/HP/BiosUpdate/CryptRSA32.efi
6488d391f74263c9da3c3d47dffa6212   sda2/HP/BiosUpdate/CryptRSA.efi
d3ed3bbb2557c7232ab90f2743940084   sda2/HP/BiosUpdate/HpBiosUpdate32.efi
18baee3d6f7498125772d0fdc71b3e55   sda2/HP/BiosUpdate/HpBiosUpdate.efi
fe3ffeb7801e22cdcfa74612bf7c6401   sda2/Microsoft/Boot/bootmgfw.efi
616f6b48acaeba6ee37b041118756ce4   sda2/Microsoft/Boot/bootmgr.efi

```

---

