---
title: "Ubuntu 16.10 Unable to Boot under Secureboot After OS Update"
date: 2016-11-05
forum: Installation &amp; Upgrades
---

### Post by ytxmobile on 2016-11-05
My laptop model is HP ENVY 4-1220tx Ultrabook. I installed Ubuntu 16.10 with SecureBoot enabled.

Yesterday I installed an OS Update from Ubuntu Software. Today, when I tried to boot my computer into Ubuntu under SecureBoot, it fails to authenticate the EFI file and therefore cannot boot.

Now I can only boot by turning off SecureBoot.

I have checked the file [HTML]/var/log/apt/history.log[/Html] and found related records:

[HTML]Start-Date: 2016-11-04  22:28:23
Commandline: aptdaemon role='role-upgrade-system' sender=':1.3522'
Upgrade: grub-common:amd64 (2.02~beta2-36ubuntu11, 2.02~beta2-36ubuntu11.1), grub2-common:amd64 (2.02~beta2-36ubuntu11, 2.02~beta2-36ubuntu11.1), grub-efi-amd64-bin:amd64 (2.02~beta2-36ubuntu11, 2.02~beta2-36ubuntu11.1), grub-efi-amd64:amd64 (2.02~beta2-36ubuntu11, 2.02~beta2-36ubuntu11.1), grub-efi-amd64-signed:amd64 (1.74+2.02~beta2-36ubuntu11, 1.74.1+2.02~beta2-36ubuntu11.1), shim:amd64 (0.9+1465500757.14a5905.is.0.8-0ubuntu3, 0.9+1474479173.6c180c6-0ubuntu1)
Remove: shim-signed:amd64 (1.21.3+0.9+1465500757.14a5905.is.0.8-0ubuntu3)
End-Date: 2016-11-04  22:30:18[/HTML]

I have also tried reinstalling the package shim-signed but encountered the following error:

[HTML]$ sudo apt install shim shim-signed
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  grub-common grub-efi-amd64-bin grub2-common os-prober
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  grub-common grub-efi-amd64-bin grub2-common os-prober shim shim-signed
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,704 kB of archives.
After this operation, 20.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://us.archive.ubuntu.com/ubuntu yakkety/main amd64 grub-common amd64 2.02~beta2-36ubuntu11 [1,751 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu yakkety/main amd64 grub2-common amd64 2.02~beta2-36ubuntu11 [526 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu yakkety/main amd64 os-prober amd64 1.70ubuntu3 [18.8 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu yakkety/main amd64 shim amd64 0.9+1465500757.14a5905.is.0.8-0ubuntu3 [442 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu yakkety/main amd64 grub-efi-amd64-bin amd64 2.02~beta2-36ubuntu11 [652 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu yakkety/main amd64 shim-signed amd64 1.21.3+0.9+1465500757.14a5905.is.0.8-0ubuntu3 [315 kB]
Fetched 3,704 kB in 1s (2,134 kB/s)  
Preconfiguring packages ...
Selecting previously unselected package grub-common.
(Reading database ... 299379 files and directories currently installed.)
Preparing to unpack .../0-grub-common_2.02~beta2-36ubuntu11_amd64.deb ...
Unpacking grub-common (2.02~beta2-36ubuntu11) ...
Selecting previously unselected package grub2-common.
Preparing to unpack .../1-grub2-common_2.02~beta2-36ubuntu11_amd64.deb ...
Unpacking grub2-common (2.02~beta2-36ubuntu11) ...
Selecting previously unselected package os-prober.
Preparing to unpack .../2-os-prober_1.70ubuntu3_amd64.deb ...
Unpacking os-prober (1.70ubuntu3) ...
Selecting previously unselected package shim.
Preparing to unpack .../3-shim_0.9+1465500757.14a5905.is.0.8-0ubuntu3_amd64.deb ...
Unpacking shim (0.9+1465500757.14a5905.is.0.8-0ubuntu3) ...
Selecting previously unselected package grub-efi-amd64-bin.
Preparing to unpack .../4-grub-efi-amd64-bin_2.02~beta2-36ubuntu11_amd64.deb ...
Unpacking grub-efi-amd64-bin (2.02~beta2-36ubuntu11) ...
Selecting previously unselected package shim-signed.
Preparing to unpack .../5-shim-signed_1.21.3+0.9+1465500757.14a5905.is.0.8-0ubuntu3_amd64.deb ...
Unpacking shim-signed (1.21.3+0.9+1465500757.14a5905.is.0.8-0ubuntu3) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for install-info (6.1.0.dfsg.1-8) ...
Setting up shim (0.9+1465500757.14a5905.is.0.8-0ubuntu3) ...
Setting up os-prober (1.70ubuntu3) ...
Setting up grub-common (2.02~beta2-36ubuntu11) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Processing triggers for systemd (231-9ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up grub-efi-amd64-bin (2.02~beta2-36ubuntu11) ...
Setting up grub2-common (2.02~beta2-36ubuntu11) ...
Setting up shim-signed (1.21.3+0.9+1465500757.14a5905.is.0.8-0ubuntu3) ...
Installing for x86_64-efi platform.
Installation finished. No error reported.
No DKMS packages installed: not changing Secure Boot validation state.[/HTML]
How can I resolve this problem?

How should I deal with the DKMS part?

---

### Post by ubfan1 on 2016-11-05
Either the /EFI/Boot/bootx64.efi got rewritten (from shimx64,efi to  grubx64.efi), and/or the nvram entry booting ubuntu got rewritten from  /EFI/ubuntu/shimx64.efi to /EFI/ubuntu/grubx64.efi.  Take a look and fix  the first case by copying the shimx64.efi back to the bootx64.efi.  Fix  the second case with efibootmgr.  Seems someone else just had this problem too.

---

### Post by ytxmobile on 2016-11-05
> **ubfan1 said:**
> Either the /EFI/Boot/bootx64.efi got rewritten (from shimx64,efi to  grubx64.efi), and/or the nvram entry booting ubuntu got rewritten from  /EFI/ubuntu/shimx64.efi to /EFI/ubuntu/grubx64.efi.  Take a look and fix  the first case by copying the shimx64.efi back to the bootx64.efi.  Fix  the second case with efibootmgr.  Seems someone else just had this problem too.

May you clarify how I should use efibootmgr?
I am new to ubuntu and need more details explaing how to do that.
Thank you.

---

### Post by oldfred on 2016-11-05
Check entry is there.
sudo efibootmgr -v  

See also 
man efibootmgr

If you really want UEFI Secure boot you need to be booting with shimx64.efi, not grubx64.efi. And if copied to bootx64.efi that must be shim, not grub.


 HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by ytxmobile on 2016-11-05
> **oldfred said:**
> Check entry is there.
sudo efibootmgr -v  

See also 
man efibootmgr

If you really want UEFI Secure boot you need to be booting with shimx64.efi, not grubx64.efi. And if copied to bootx64.efi that must be shim, not grub.


 HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

I have run [HTML]sudo efibootmgr -v[/HTML] and got the following:
[HTML]BootCurrent: 003D
Timeout: 0 seconds
BootOrder: 3000,3001,3002,2001,2002,2003
Boot0000* Windows Boot Manager    HD(2,GPT,4c62bd16-5881-4f91-a4e3-f5e1088db1b2,0xe1800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...M................
Boot0001* Ubuntu    HD(2,GPT,4c62bd16-5881-4f91-a4e3-f5e1088db1b2,0xe1800,0x32000)/File(\EFI\ubuntu\grubx64.efi)RC
Boot0002* EFI HDD Device (HGST HTS545050A7E380)    PciRoot(0x0)/Pci(0x1f,0x2)/Sata(1,32768,0)/HD(10,GPT,79febc10-3efa-01d1-085e-f73c7d9fe800,0x2a59d800,0xd85800)RC
Boot2001* USB Drive (UEFI)    RC
Boot3000* Internal Hard Disk or Solid State Disk    RC
Boot3001* Internal Hard Disk or Solid State Disk    RC
Boot3002* Internal Hard Disk or Solid State Disk    RC

[/HTML]

What should I do next?

---

### Post by oldfred on 2016-11-05
HP often does not let you use the Ubuntu entry which is grub, or you must have Secure Boot off.
It used to add 2 entries one grub and the other shim.

Can you boot any of the Internal Hard Disk entries. Not sure if they are BIOS defaults or UEFI defaults.
UEFI fallback or hard drive entry is /EFI/Boot/bootx64.efi, and Boot-Repair says it copied shimx64.efi to be that fallback entry.

---

### Post by ytxmobile on 2016-11-05
> **oldfred said:**
> HP often does not let you use the Ubuntu entry which is grub, or you must have Secure Boot off.
It used to add 2 entries one grub and the other shim.

Can you boot any of the Internal Hard Disk entries. Not sure if they are BIOS defaults or UEFI defaults.
UEFI fallback or hard drive entry is /EFI/Boot/bootx64.efi, and Boot-Repair says it copied shimx64.efi to be that fallback entry.

If I ENABLE SecureBoot &#8594; I can boot from none of the two entries
If I DISABLE SecureBoot &#8594; I can boot from both of the two entries

---

### Post by oldfred on 2016-11-05
I would just leave Secure boot off (I do).

But you need a shim boot entry if you want to boot in Secure boot mode. And then I am not sure Ubuntu entry works with HP?

If bootx64.efi is really shimx64.efi where sdX is drive sda and -p Y is partition number like 1, 2 or 3 typically.
 sudo efibootmgr -c -g -d /dev/sdX -p Y -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'  

      
 sudo efibootmgr -c -l "\EFI\UBUNTU\SHIMX64.EFI" -L ubuntuSE -d /dev/sdX -p Y
where /dev/sdX is the disk and Y is the partition number.

---

### Post by ytxmobile on 2016-11-05
> **oldfred said:**
> I would just leave Secure boot off (I do).

But you need a shim boot entry if you want to boot in Secure boot mode. And then I am not sure Ubuntu entry works with HP?

If bootx64.efi is really shimx64.efi where sdX is drive sda and -p Y is partition number like 1, 2 or 3 typically.
 sudo efibootmgr -c -g -d /dev/sdX -p Y -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'  

      
 sudo efibootmgr -c -l "\EFI\UBUNTU\SHIMX64.EFI" -L ubuntuSE -d /dev/sdX -p Y
where /dev/sdX is the disk and Y is the partition number.

I have done what you told me.
I got a boot entry titled ubuntuSE in my boot device order menu.
However, I still can only boot with Secure Boot DISABLED.

---

### Post by ubfan1 on 2016-11-05
Sometimes the actual name/label is checked, requiring that it be "Windows Boot Manager".  Use efibootmgr to change the label from "ubuntuSE" to "Windows Boot Manager" and try booting that.

---

