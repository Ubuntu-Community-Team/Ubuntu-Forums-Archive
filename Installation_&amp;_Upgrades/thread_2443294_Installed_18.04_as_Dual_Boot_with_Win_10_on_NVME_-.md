---
title: "Installed 18.04 as Dual Boot with Win 10 on NVME - Only accessable via BIOS Boot menu"
date: 2020-05-13
forum: Installation &amp; Upgrades
---

### Post by Tony_Bennett on 2020-05-13
My System:
Tomahawk B450 Max motherboard with Ryzen 3600 cpu
16 GB Corsair DDR4 memory
1 TB Samsung 970 EVO Plus NVME m.2

Windows 10 installed first... successfully

Ubuntu installed next... successfully... I thought

Following install, a reboot took me straight into Windows.

I was able to find that the Bios (UEFI) Boot Menu (via F11 at boot up)
provided two options:  Windows Boot Manager and Ubuntu

Selecting the Ubuntu took me straight to Grub2 menu... 
I chose Ubuntu and booted successfully into Ubuntu... which worked fine.

I re-ran "sudo update-grub"  and got the following:

```
trb@TOMMY-1:~$ sudo update-grub
[sudo] password for trb: 
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.3.0-51-generic
Found initrd image: /boot/initrd.img-5.3.0-51-generic
Found linux image: /boot/vmlinuz-5.0.0-23-generic
Found initrd image: /boot/initrd.img-5.0.0-23-generic
Found Windows Boot Manager on /dev/nvme0n1p2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
```

However, a reboot afterwords still took me straight into Windows.

Here are some of the contents of the EFI directory (as seen from Ubuntu):
```
root@TOMMY-1:/boot/efi# ls -l /boot/efi/EFI
total 3
drwx------ 2 root root 1024 May 13 10:21 Boot
drwx------ 4 root root 1024 May  5 01:15 Microsoft
drwx------ 3 root root 1024 May 13 10:21 ubuntu

root@TOMMY-1:/boot/efi# ls -l /boot/efi/EFI/Boot
total 2489
-rwx------ 1 root root 1334816 May 13 17:51 bootx64.efi
-rwx------ 1 root root 1213032 May 13 17:51 fbx64.efi

root@TOMMY-1:/boot/efi# ls -l /boot/efi/EFI/ubuntu
total 3713
-rwx------ 1 root root     108 May 13 17:51 BOOTX64.CSV
drwx------ 2 root root    1024 May 13 10:20 fw
-rwx------ 1 root root   75992 May 13 10:20 fwupx64.efi
-rwx------ 1 root root     117 May 13 17:51 grub.cfg
-rwx------ 1 root root 1116536 May 13 17:51 grubx64.efi
-rwx------ 1 root root 1269496 May 13 17:51 mmx64.efi
-rwx------ 1 root root 1334816 May 13 17:51 shimx64.efi

```

I'm up for suggestions.

---

### Post by VMC on 2020-05-13
Try  grub-install?

---

### Post by oldfred on 2020-05-13
And if you go back into f11, does it not still show ubuntu as boot entry?
That should work.

Then from within Ubuntu post this:
sudo efibootmgr -v

Note that Windows updates will turn fast start up back on, and then grub will not boot Windows. You will have to use f11. 
And those updates may make Windows first in boot order.
Reinstall of grub makes grub first in boot order, so you often have to manage boot order.
Most systems will let you use efibootmgr to set boot order, some only let you change it using UEFI settings menu.
See also
man efibootmgr

---

### Post by Tony_Bennett on 2020-05-14
Thanks for the response, OldFred.

During boot up, pressing F11 brings up the boot menu which contains:
```
Windows Boot Manager (Samsung SSD 970 EVO Plus 1TB)
ubuntu (Samsung SSD 970  EVO Plus 1TB)
Enter Setup

```

I selected "ubuntu", and booted into Grub, and selected "Ubuntu" from it.

Within Ubuntu I entered "sudo efibootmgr -v" and got the following:
```
sudo efibootmgr -v
[sudo] password for trb:
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0000,0001
Boot0000* Windows Boot Manager  HD(2,GPT,6f5b61c0-cf1c-4414-bc56-4cb4de62b22d,0x109000,0x31800)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...,................
Boot0001* ubuntu        HD(2,GPT,6f5b61c0-cf1c-4414-bc56-4cb4de62b22d,0x109000,0x31800)/File(\EFI\UBUNTU\SHIMX64.EFI)

```

I then rebooted, and instead of the expected grub menu, it still boots straight into Windows.

What should I do next?

---

### Post by Tony_Bennett on 2020-05-14
Reading the efibootmgr man page gave me the idea to simply set the boot order, the "-o" argument.
So I ran this:
```
trb@TOMMY-1:~$ sudo efibootmgr -v -o 0001,0000
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0000
Boot0000* Windows Boot Manager  HD(2,GPT,6f5b61c0-cf1c-4414-bc56-4cb4de62b22d,0x109000,0x31800)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...,................
Boot0001* ubuntu        HD(2,GPT,6f5b61c0-cf1c-4414-bc56-4cb4de62b22d,0x109000,0x31800)/File(\EFI\UBUNTU\SHIMX64.EFI)

```

Expecting to reboot into a grub menu...
No go... straight into Windows.

Used F11 to boot into Ubuntu, and ran this:
```
trb@TOMMY-1:~$ sudo efibootmgr -v
[sudo] password for trb: 
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0000,0001
Boot0000* Windows Boot Manager    HD(2,GPT,6f5b61c0-cf1c-4414-bc56-4cb4de62b22d,0x109000,0x31800)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...,................
Boot0001* ubuntu    HD(2,GPT,6f5b61c0-cf1c-4414-bc56-4cb4de62b22d,0x109000,0x31800)/File(\EFI\UBUNTU\SHIMX64.EFI)

```

So it seems, if I am reading this right, the boot order is getting reset during a reboot..!!

Suggestions....??

---

### Post by Tony_Bennett on 2020-05-14
Well it turned out the UEFI (bios) contained an setting called "UEFI Hard Disk Drive BBS Priorities".
Which contained:
```
Boot Option #1 [Windows Boot Manager...]
Boot Option #2 [ubuntu ... ]
```

It appears the UEFI/BIOS is using this setting, instead of the setting I made with efibootmgr.

I changed the order (ubuntu first, windows manager second), saved, exited, and it booted into Grub menu..
Where I could boot into ubuntu (successfully) or into Windows (successfully).

Everything is now working as expected.

---

