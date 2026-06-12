---
title: "Clonezilla restore: can't boot because of &quot;invalid secure boot detected&quot;"
date: 2017-03-08
forum: Installation &amp; Upgrades
---

### Post by DB4711 on 2017-03-08
Hello,

I created an image of my disk with UBuntu in UEFI mode with clonezilla-live-20170220-yakkety-amd64. Then I tried to restore it but I can't boot: "invalid secure boot detected"


Clonezilla version should be the right one to use with UEFI installations.

I have no idea where the problem lies...

Thanks for any help!

---

### Post by oldfred on 2017-03-08
Did you have UEFI Secure boot on when you installed Ubuntu?

Try with UEFI Secure boot off.
It may say "Windows" or "Other" in some UEFI, but that is really secure boot as fine print says if installing Windows 7 use "Other" as Windows 7 does not support Secure Boot.

---

### Post by DB4711 on 2017-03-09
Hello oldfred,

thanks for your help.

Yes, Secure Booot was on while Ubuntu was installed and is still on.

In my BIOS I can't turn off Secure boot. I only see that it is turned on.

I noticed that my boot order menu in BIOS is messed up. The titles are not correctly displayed, there are something like display errors...

I wrote the image back to the HD without deleting the existing partitions. Maybe I should try to delete all existing partitions and then try again restoring the image?!

---

### Post by oldfred on 2017-03-09
If you have duplicate UUID or GUIDs then you will have problems.
If UEFI you can often use gdisk or sdgdisk to reset UUID or GUIDs.

 to see GUID/partUUID for each device, post with code tags to preserve formatting:
lsblk -o +PARTUUID /dev/sda
sudo blkid -c /dev/null -o list

---

### Post by DB4711 on 2017-03-09
Hello oldfred,

just to clarify: I made an image of the whole HD and restored it again on the same HD. So there  should be no problems with UUIDs or GUIDSs.

---

### Post by oldfred on 2017-03-09
Microsoft requires vendors to allow users to turn on/off Secure boot.
Exceptions are some 32 bit UEFI only tablet type systems.

---

### Post by DB4711 on 2017-03-09
Hello oldfred,

I don't understand this:

"Microsoft requires vendors to allow users to turn on/off Secure boot.
Exceptions are some 32 bit UEFI only tablet type systems."

---

### Post by oldfred on 2017-03-09
You said you could not turn off UEFI Secure boot.
It is a requirement, so your vendor should explain where or how that setting works. Check your manual.
One or two vendors have had to update their UEFI to allow turning it off.
Some hide settings under the CSM (BIOS) settings. But you still want UEFI boot, not CSM.

---

### Post by DB4711 on 2017-03-09
Thanks for your time :)

OK, so if disabled it should work again.

But what I do not understand is: why is my ubuntu not booting anymore. Isn't it possible to clone HDs with UEFI Secure Boot enabled anymore? Even if I restore the image exactly on the same source HD?! It's confusing me...

---

### Post by oldfred on 2017-03-09
UEFI forgets UEFI entries in NVRAM when a drive is removed. So you may just need to use efibootmgr to add entries. You can re-install grub which always adds new entries.

To see UEFI boot entries(included in Boot-Repair's Summary Report).
sudo efibootmgr -v

 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by DB4711 on 2017-03-09
Funny,

here is the output

ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0005
Timeout: 1 seconds
BootOrder: 0005,0003,0004,0001,0000,0002
Boot0000  ubuntu
Windows Boot Manager
ubuntu    HD(1,GPT,078635fc-9a98-409c-bc70-4f5a9670e63a,0x800,0xa7000)/File(\EFI\UBUNTU\GRUBX64.EFI)
Boot0001*  Windows Boot Manager     HD(1,GPT,078635fc-9a98-409c-bc70-4f5a9670e63a,0x800,0xa7000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0002* UEFI OS    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0003*  UEFI: IP4 Realtek PCIe GBE Family Controller     PciRoot(0x0)/Pci(0x1c,0x1)/Pci(0x0,0x0)/MAC(fcaa1495472c,0)/IPv4(0.0.0.0:0<->0.0.0.0:0,0,0)..BO
Boot0004*  UEFI: IP6 Realtek PCIe GBE Family Controller     PciRoot(0x0)/Pci(0x1c,0x1)/Pci(0x0,0x0)/MAC(fcaa1495472c,0)/IPv6([::]:<->[::]:,0,0)..BO
Boot0005* UEFI: SanDisk Cruzer Micro 8.02    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(1,MBR,0x61,0x3860,0x1300)..BO



ubuntu@ubuntu:~$ sudo efibootmgr
BootCurrent: 0005
Timeout: 1 seconds
BootOrder: 0005,0003,0004,0001,0000,0002
Boot0000  ubuntu
Windows Boot Manager
ubuntu
Boot0001* Windows Boot Manager
Boot0002* UEFI OS
Boot0003* UEFI: IP4 Realtek PCIe GBE Family Controller
Boot0004* UEFI: IP6 Realtek PCIe GBE Family Controller
Boot0005* UEFI: SanDisk Cruzer Micro 8.02



with -v there are many strange charachters. It must be the problem why I see strange characters and dispplay errors in my BIOS.

---

### Post by oldfred on 2017-03-09
That looks like a normal UEFI entry. The -v shows the details.
Does GUID match for sda1?
ubuntu    HD(1,GPT,[COLOR=#ff0000]078635fc-9a98-409c-bc70-4f5a9670e63a[/COLOR],0x800,0xa7000)/File(\EFI\UBUNTU\GRUBX64.EFI)
with this for sda1?
       lsblk -o +PARTUUID /dev/sda 

The grubx64.efi only works with Secure boot off. You do not show an entry for shimx64.efi. 
Most installs have two ubuntu entries, one grub & one shim. I use shim but not Secure boot. Shim works either way.

My entry & GUID that matches.
```
fred@Z170N:~$ lsblk -o +PARTUUID /dev/sda
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT PARTUUID
sda      8:0    0 232.9G  0 disk            
&#9500;&#9472;sda1   8:1    0  49.8G  0 part /boot/efi  [COLOR=#ff0000]c371fe4e-a6db-4c46-b056-a4eea609f81d[/COLOR]

Boot0000* ubuntu    HD(1,GPT,[COLOR=#ff0000]c371fe4e-a6db-4c46-b056-a4eea609f81d[/COLOR],0x800,0x639c000)/File(\EFI\UBUNTU\SHIMX64.EFI)

```

---

### Post by DB4711 on 2017-03-09
Output

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT PARTUUID
sda      8:0    0 119.2G  0 disk            
&#9500;&#9472;sda4   8:4    0   7.2G  0 part [SWAP]     930acf9e-94ce-408d-9525-90f9284c88c2
&#9500;&#9472;sda2   8:2    0    28G  0 part            af7a0736-0e45-4310-b318-f488f08644f7
&#9500;&#9472;sda3   8:3    0  83.8G  0 part            49d43c05-b3ba-499f-85e1-042501708d9c
&#9492;&#9472;sda1   8:1    0   334M  0 part            078635fc-9a98-409c-bc70-4f5a9670e63a

So it is the ID of the EFI partition.

I dont understand why it is not easy going to make an image of an entire hard disk and restore it again... strange

I also tried to repair boot with boot repair. but it is not possible because the tool tells me i have to disable secure boot... and that is not possible in BIOS. Entry is not editable.

---

### Post by DB4711 on 2017-03-11
To ensure I am doing all steps correct I installed Ubuntu again and made then again an image with "alternative stable - 20170220-yakkety" and again restored it:

I get the same secure boot error as before...

I am at one's wits' end.

---

### Post by oldfred on 2017-03-11
Did you try with Secure Boot off?

Yes if originally installed with Secure Boot on, it should work, but perhaps system sees something changed so then it thinks it is not Secure anymore.

---

### Post by DB4711 on 2017-03-11
I am not able to turn off secure boot in BIOS.

this is really annoying...

---

### Post by oldfred on 2017-03-11
Some hide the setting or do not make it clear that it is Secure boot setting.
One of my systems had it under the CSM setting. Another had "Windows" and "Other" where Other was secure boot off.

---

### Post by DB4711 on 2017-03-12
In BIOS I see that secure boot is on. I can not change that value. But underneath there's an entry labeled "delete all secure boot variables" or similar. I did that. Then secure boot is not enabled anymore.

Then I reinstalled Ubunutu, made an image, wrote back and voila: it runs.

I still have no idea what's wrong with my environment. But now I can use the image restore as expected. Without secure boot... but I don't think it is really essential...

---

### Post by oldfred on 2017-03-12
You should not have to delete the secure boot variables.
Do it also have a setting to restore them from defaults, just in case in the future you do want Secure boot?

I do not use Secure boot and currently have no plans to. But who knows about the future.

---

