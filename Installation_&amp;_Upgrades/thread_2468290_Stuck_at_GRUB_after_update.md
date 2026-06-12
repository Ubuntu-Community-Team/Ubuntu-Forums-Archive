---
title: "Stuck at GRUB after update"
date: 2021-10-24
forum: Installation &amp; Upgrades
---

### Post by Hex on 2021-10-24
I've updated and rebooted my 20.04 LTS (recent clean install), only to discover it's stuck at GRUB.

This is a two SSD RAID1 setup - md0 is swap, md1 is root, there is a separate boot partition on each drive.

I can find root on (md/1,gpt1) and I can find efi on both (hd0,gpt1) and (hd1,gpt1).

On (md/1,gpt1) I have /boot/vmlinuz-5.4.0.88-generic and /boot/vmlinuz-5.4.0.89-generic.

I've tried several configurations, but I end up at an initramfs prompt.

Any help is greatly appreciated, I've been struggling for hours.

---

### Post by oldfred on 2021-10-24
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

Boot-Repair can get confused between LVM & RAID and if LVM is full drive encrypted, you must mount LVM & decrypt it first.
Probably should mount both LVMs before running Boot-Repair.

---

### Post by Hex on 2021-10-25
Thank you for your reply. I've disconnected all non-essential drives and left only the 2 SSDs that work as RAID1:

[https://paste.ubuntu.com/p/KD7XHCmJY8/](https://paste.ubuntu.com/p/KD7XHCmJY8/)

p.s. I don't use encryption.

---

### Post by oldfred on 2021-10-25
Do not know RAID.

But default boot entry in UEFI is 000F, should be 0000 or 0002. 
But the ones using grubx64.efi or bootx64.efi should also work. 
They all should be using the same grub.cfg to configfile to the full grub.cfg in your install. But that shows an UUID that does not exist?

> search.fs_uuid [COLOR=#ff0000]5e3b2151-2360-488f-a983-61b5721a7216[/COLOR] root mduuid/[COLOR=#ff0000]630de7b0e62c32ca5b6d9ef87edf8b3f [/COLOR]
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


I might just try reinstalling grub.
I believe Boot-Repair works with your RAID, but you may have to chroot into install and reinstall grub that way.

---

### Post by Hex on 2021-10-25
So try boot-repair or reinstall grub. Not sure how to do the latter - point me in the right direction, please?

I wonder why this problem even appeared...

Edit: I tried fixing it, here's the output:

[https://paste.ubuntu.com/p/9fKFd6H6Rh/](https://paste.ubuntu.com/p/9fKFd6H6Rh/)

---

### Post by Hex on 2021-10-25
[deleted]

---

### Post by oldfred on 2021-10-25
It updated the grub.cfg in sda1, but not in sda2, probably because its RAID and only installs to one drive.
You may need to copy sda1 to sda2.

Errors seem to be related to sdc, so not important as that is just live installer.

If you select 0000 which does not show *, so may not be in UEFI boot menu. Not seen that as it looks like that has correct GUID for sda's ESP.
See if you can set active with efibootmgr ( -a option and reset boot order with -o option)
man efibootmgr

example, I think you want 0, C & D as valid options with correct UUID for sda1's ESP:
Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
 sudo efibootmgr -o 0,1,2

---

### Post by Hex on 2021-10-25
I've managed to boot, but for some reason now /boot/efi is on sdb1. I've copied all filed from sdb1 to sda1, because they were newer.

When I run efibootmgr -v, I get:

> BootOrder: 0001,000B,0005,000D,0000,0012,0013,0002,0004,0009,0011
Boot0000  ubuntu	HD(1,GPT,9817f059-d900-4820-bf09-c4b40de48207,0x800,0x3b9000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* ubuntu	HD(1,GPT,9817f059-d900-4820-bf09-c4b40de48207,0x800,0x3b9000)/File(\EFI\ubuntu\shimx64.efi)
Boot0002  ubuntu	HD(1,GPT,4d46c7f4-a415-420b-9c0f-b74273aba245,0x800,0x3b9000)/File(\EFI\ubuntu\shimx64.efi)
Boot0004  Network Card 	BBS(Network,,0x0)AMGOAMNO........k.R.e.a.l.t.e.k. .P.X.E. .B.0.2. .D.0.0.........................rN.D+..,.\...........<..Gd-.;.A..MQ..L.R.e.a.l.t.e.k. .P.X.E. .B.0.2. .D.0.0......AMBO
Boot0005  UEFI: Built-in EFI Shell 	VenMedia(5023b95c-db26-429b-a648-bd47664c8012)AMBO
Boot0009* Hard Drive 	BBS(HD,,0x0)AMGOAMNO........o.A.D.A.T.A. .S.U.6.5.0....................A...........................>..Gd-.;.A..MQ..L.J.2.8.4.0.2.3.1.5.1.3.2. . . . . . . . ......AMBOAMNO........o.A.D.A.T.A. .S.U.6.5.0....................A...........................>..Gd-.;.A..MQ..L.J.2.8.4.0.2.3.1.3.4.5.7. . . . . . . . ......AMBOAMNO........o.H.D.S.7.2.2.5.1.6.V.L.S.A.8.0....................A...........................>..Gd-.;.A..MQ..L. . . . . . .N.V.D.6.E.3.D.C.9.D.L.N.D.E......AMBO
Boot000B* UEFI OS	HD(1,GPT,9817f059-d900-4820-bf09-c4b40de48207,0x800,0x3b9000)/File(\EFI\BOOT\BOOTX64.EFI)
Boot000D  UEFI OS	HD(1,GPT,4d46c7f4-a415-420b-9c0f-b74273aba245,0x800,0x3b9000)/File(\EFI\BOOT\BOOTX64.EFI)
Boot0011* Unknown Device 	BBS(8,,0x0)AMGOAMNO..........S.e.a.g.a.t.e. .B.a.c.k.u.p.+. .H.u.b. .B.K. .D.7.8.1....................A...................................L..Gd-.;.A..MQ..L.S.e.a.g.a.t.e. .B.a.c.k.u.p.+. .H.u.b. .B.K. .D.7.8.1......AMBO
Boot0012  ubuntu	HD(1,GPT,4d46c7f4-a415-420b-9c0f-b74273aba245,0x800,0x3b9000)/File(\EFI\Ubuntu\grubx64.efi)
Boot0013  ubuntu	HD(1,GPT,9817f059-d900-4820-bf09-c4b40de48207,0x800,0x3b9000)/File(\EFI\Ubuntu\grubx64.efi)


I don't understand why there are repeating entries, but then again I know nothing about the boot process. Is there something I should do, given that the system boots properly?

---

### Post by oldfred on 2021-10-25
You normally get an Ubuntu entry for both shimx64.efi & grubx64.efi. Shim works for both Secure boot on or off. Grub entry only works with Secure boot off.
You usually also get a fallback or drive boot entry that uses /EFI/Boot/bootx64.efi. Similar to entry used to boot any external drive & live installers.

Again do not know RAID, but since two ESPs, you may get double entries.

UEFI uses GUID aka partUUID.

You can compare partUUID to UEFI entries & if any not valid delete from UEFI with efibootmgr -b.
sudo efibootmgr -v
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

---

### Post by Hex on 2021-10-26
I understand, thank you. You've been really helpful and saved me several days reinstalling services (something I did ten days ago...), I really appreciate your professional help!

Marking as solved, thank you again!

---

