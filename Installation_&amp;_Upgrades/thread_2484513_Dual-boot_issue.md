---
title: "Dual-boot issue"
date: 2023-03-01
forum: Installation &amp; Upgrades
---

### Post by brtlbrtl on 2023-03-01
Hey There,

I have some booting issues with a dual-boot machine (ubuntu 22.04, win11). After doing some updates (ubuntu and windows) I got some 'Volume Corrupt' error before reaching the boot menu (cf. ErrorA.jpg, ErrorB.jpg). Booting defaulted to windows. At this point, after some googling, I tried boot-repair via Live-USB (paste.ubuntu.com/p/b3vn4CjYCZ/). Sadly, that did not solve my problem but led to another error message (grubx64.efi not found) (cf. ErrorC.jpg). I immediately tried boot-repair for a second time (paste.ubuntu.com/p/4P6KFhmXdH/), however, that did not help and left me with the same error and with the same behavior as before. I still cannot boot to ubuntu and always end up booting to windows. Any help is very warmly appreciated.

Cheerio, 
Brtl

---

### Post by oldfred on 2023-03-01
While UEFI technically may allow more than one ESP per drive, most systems only work with one per drive.
Remove partition p6 and entry in UEFI that uses p6 (0001).
Entry 0002 on line 36 actually looks ok. Does it work?

Some systems have UEFI settings to lock ESP or lock updates. And UEFI updates may reset to defaults, so even if you changed setting before, you may need to redo those changes.
What brand/model system?

sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

---

### Post by tea for one on 2023-03-01
[COLOR="#0000FF"]Line 52[/COLOR] - grub-install: warning: EFI variables cannot be set on this system.
[COLOR="#0000FF"]Line 53[/COLOR] - grub-install: warning: You will have to complete the GRUB setup manually.

For manual Grub set up, you can try this from a live (Try Ubuntu) session:-

```
sudo mount /dev/sdXY /mnt
sudo mount /dev/sdXX /mnt/boot/efi
for i in /dev /dev/pts /proc /sys /sys/firmware/efi/efivars /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
grub-install /dev/sdX (or grub-install /dev/sdXX)
grub-install --recheck /dev/sdX
update-grub  

```
Note : sdX = disk | sdXX = efi partition | sdXY = system partition

Disk = nvme0n1
EFI partition = nvme0n1p1
System partiton = nvme0n1p8

---

### Post by brtlbrtl on 2023-03-02
I was able to change the UEFI NVME Drive BBS Priorities during startup to Boot0002 i.e. the new/uncorrupted ubuntu entry for p1. That was actually wild guessing as both ubuntu entries were named exactly the same. However, that did the trick and allowed me to boot to my ubuntu installation. Thank you for your suggestions, they helped a lot! 

sudo efibootmgr -v now shows:

BootCurrent: 0002
Timeout: 2 seconds
BootOrder: 0002,0000,0001
Boot0000* Windows Boot Manager  HD(1,GPT,834346b4-84a9-41b7-97b1-d03677c97f50,0x800,0x82000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFIWINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* ubuntu        HD(6,GPT,c10f3508-1903-4097-bb29-966b41002664,0x74705200,0x117701)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0002* ubuntu        HD(1,GPT,834346b4-84a9-41b7-97b1-d03677c97f50,0x800,0x82000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO

As far as I got it, I could safely delete Boot0001 via 'sudo efibootmgr -b 0001 -B' in order to get things a little cleaned up, right?

---

### Post by tea for one on 2023-03-02
As you are currently booted using 0002, then it is safe to remove 0001 via efibootmgr.

Perhaps, consider removing partition nvme0n1p6 as mentioned by oldfred in post 2?

---

### Post by brtlbrtl on 2023-03-06
Thanks again for helping me out, I deleted config 0001 and removed partition nvme0n1p6 successfully, now everything is fine again.

---

