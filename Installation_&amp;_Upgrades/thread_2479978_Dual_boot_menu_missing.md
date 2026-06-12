---
title: "Dual boot menu missing"
date: 2022-10-14
forum: Installation &amp; Upgrades
---

### Post by zkab on 2022-10-14
I have a Windows11 computer where I installed Ubuntu 22.04 LTS along with Windows.
Problem is that I don't see boot menu and Windows11 is booting every time.
I have changed in 'grub-customize' that Ubuntu should be the preferred boot ... but still Windows11 boots ... it seems that Windows11 is hard-wired to boot.
How can I get the boot menu so I can choose which OS to boot?
Do I have to change in Windows11 to get the boot menu?

---

### Post by oldfred on 2022-10-14
What brand/model computer?

Some like HP, only change boot order by going into UEFI settings and changing it there.
HP - escape + F9 for UEFI boot menu, F10 for UEFI/bios settings

Most systems accept efibootmgr changes to UEFI boot order. Grub also uses efibootmgr to update order when installing.

---

### Post by zkab on 2022-10-14
I have GTR5 5900HX
[https://www.bee-link.com/catalog/product/index?id=364](https://www.bee-link.com/catalog/product/index?id=364)

It comes with Windows11 Pro preinstalled

---

### Post by oldfred on 2022-10-14
Looks like an interesting little computer.

In UEFI settings you should be able to change boot order.

If that does not work, we may need to see if correctly installed.
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by oldfred on 2022-10-14
Several Motherboards & systems with AMD need [B]acpi=off.

[/B]MSI GE63 Update UEFI then acpi=off not required
[https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues](https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues) & 
ryzen acpi=off only 1 cpu, needs nomodeset & then nVidia driver insteadGigabyte
[https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu](https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu)
 Asus ZenBook Pro 14 UX480 Black screen acpi=off required, but 19.10 not required
[https://askubuntu.com/questions/1138820/black-screen-after-grub-selection-boot-from-usb-liveClass](https://askubuntu.com/questions/1138820/black-screen-after-grub-selection-boot-from-usb-liveClass)
Asus ZenBook UX431FN w/MX150  edid version issue  Black screen
[https://ubuntuforums.org/showthread.php?t=2420705](https://ubuntuforums.org/showthread.php?t=2420705)
HP Pavilion desktop Desktop TP01-2XX needs acpi=off
[https://ubuntuforums.org/showthread.php?t=2479919](https://ubuntuforums.org/showthread.php?t=2479919)

---

### Post by zkab on 2022-10-16
Here comes output from 'boot-info'

[https://paste.ubuntu.com/p/5PTgmS97cZ/](https://paste.ubuntu.com/p/5PTgmS97cZ/)

---

### Post by yancek on 2022-10-16
Lines 73-84 shows the output of efibootmgr and line 79 shows the boot order which has windows as first boot.  If you don't change that in the BIOS it will continue to boot windows.  You may be able to change it with efibootmgr but you should definitely be able to do it in the BIOS firmware.  Make the change permanent by doing it in the BIOS rather than with a one time boot option key.  I don't know your hardware so can't tell which key(s) you need to use.

---

### Post by oldfred on 2022-10-16
See line 79, it says the Windows entry is first.
Normally when grub installs it uses efibootmgr to change boot order to make Ubuntu entry first.

What key do you use to boot USB flash drive?
That same key should show UEFI boot menu and both Ubuntu & Windows in your system.
Does Ubuntu then boot?

Some systems require you to change UEFI boot order by going into UEFI settings, often f2 or del key, but varies by vendor.

This works with most systems.
Check current order & hex number of each entry , will be same as shown in report:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
 sudo efibootmgr -o 0,1,5,3,4
see also 
man efibootmgr

---

### Post by tea for one on 2022-10-16
> **zkab said:**
> I have changed in 'grub-customize' that Ubuntu should be the preferred boot ... but still Windows11 boots ... it seems that Windows11 is hard-wired to boot.
[https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html](https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html)
I think that you should be aware of the changes that grub-customizer has made to your files in /etc/grub.d/
Line 246 - drwxr-xr-x 4 root root  4096 Oct 14 08:11 backup

---

### Post by oldfred on 2022-10-16
I do not think grub customizer changes UEFI boot order.
Unless you change that with either UEFI Settings or efibootmgr, you will never get to a grub menu.

---

### Post by zkab on 2022-10-18
*sudo efibootmgr* -v gives me:

```
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0001,0000,0003,0004
Boot0000* ubuntu	HD(1,GPT,dfd352c3-7ee8-4169-8c54-6c8efcc81358,0x800,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* Windows Boot Manager	HD(1,GPT,dfd352c3-7ee8-4169-8c54-6c8efcc81358,0x800,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....O...............
Boot0003* UEFI: PXE IPv4 Realtek PCIe 2.5GBE Family Controller	PciRoot(0x0)/Pci(0x1,0x3)/Pci(0x0,0x0)/MAC(7070fc006f27,0)/IPv4(0.0.0.00.0.0.0,0,0)..BO
Boot0004* UEFI: PXE IPv4 Realtek PCIe 2.5GBE Family Controller	PciRoot(0x0)/Pci(0x2,0x1)/Pci(0x0,0x0)/MAC(7070fc006f28,0)/IPv4(0.0.0.00.0.0.0,0,0)..BO
```

I understand *sudo efibootmgr -o 0,1,3,4* will result that Ubuntu will start after boot

---

### Post by zkab on 2022-10-19
I tested with *sudo efibootmgr -o 0,1,3,4* and it worked temporarly ... but after reboot I was back at square one.

```
forsete@beelink:~$ sudo efibootmgr -v
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0001,0000,0003,0004
Boot0000* ubuntu	HD(1,GPT,dfd352c3-7ee8-4169-8c54-6c8efcc81358,0x800,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* Windows Boot Manager	HD(1,GPT,dfd352c3-7ee8-4169-8c54-6c8efcc81358,0x800,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....O...............
Boot0003* UEFI: PXE IPv4 Realtek PCIe 2.5GBE Family Controller	PciRoot(0x0)/Pci(0x1,0x3)/Pci(0x0,0x0)/MAC(7070fc006f27,0)/IPv4(0.0.0.00.0.0.0,0,0)..BO
Boot0004* UEFI: PXE IPv4 Realtek PCIe 2.5GBE Family Controller	PciRoot(0x0)/Pci(0x2,0x1)/Pci(0x0,0x0)/MAC(7070fc006f28,0)/IPv4(0.0.0.00.0.0.0,0,0)..BO

forsete@beelink:~$ sudo efibootmgr -o 0,1,3,4
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0001,0003,0004
Boot0000* ubuntu
Boot0001* Windows Boot Manager
Boot0003* UEFI: PXE IPv4 Realtek PCIe 2.5GBE Family Controller
Boot0004* UEFI: PXE IPv4 Realtek PCIe 2.5GBE Family Controller

forsete@beelink:~$ sudo efibootmgr -v
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0001,0003,0004
Boot0000* ubuntu	HD(1,GPT,dfd352c3-7ee8-4169-8c54-6c8efcc81358,0x800,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* Windows Boot Manager	HD(1,GPT,dfd352c3-7ee8-4169-8c54-6c8efcc81358,0x800,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....O...............
Boot0003* UEFI: PXE IPv4 Realtek PCIe 2.5GBE Family Controller	PciRoot(0x0)/Pci(0x1,0x3)/Pci(0x0,0x0)/MAC(7070fc006f27,0)/IPv4(0.0.0.00.0.0.0,0,0)..BO
Boot0004* UEFI: PXE IPv4 Realtek PCIe 2.5GBE Family Controller	PciRoot(0x0)/Pci(0x2,0x1)/Pci(0x0,0x0)/MAC(7070fc006f28,0)/IPv4(0.0.0.00.0.0.0,0,0)..BO
```

After reboot:

```
forsete@beelink:~$ sudo efibootmgr -v
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0001,0000,0003,0004
Boot0000* ubuntu	HD(1,GPT,dfd352c3-7ee8-4169-8c54-6c8efcc81358,0x800,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* Windows Boot Manager	HD(1,GPT,dfd352c3-7ee8-4169-8c54-6c8efcc81358,0x800,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....O...............
Boot0003* UEFI: PXE IPv4 Realtek PCIe 2.5GBE Family Controller	PciRoot(0x0)/Pci(0x1,0x3)/Pci(0x0,0x0)/MAC(7070fc006f27,0)/IPv4(0.0.0.00.0.0.0,0,0)..BO
Boot0004* UEFI: PXE IPv4 Realtek PCIe 2.5GBE Family Controller	PciRoot(0x0)/Pci(0x2,0x1)/Pci(0x0,0x0)/MAC(7070fc006f28,0)/IPv4(0.0.0.00.0.0.0,0,0)..BO
forsete@beelink:~$ 

```

One thing I noticed was that boot time was a little bit longer than before ... seems it is impossible to change boot order !!!

---

### Post by oldfred on 2022-10-19
Can you change boot order in UEFI settings (not the UEFI boot menu)?

---

