---
title: "Dual boot Win8.1/Ubuntu 14.04 boots directly to Windows after update"
date: 2015-05-21
forum: Installation &amp; Upgrades
---

### Post by s.boone35223 on 2015-05-21
I recently updated Ubunutu (and Windows).  Likely, after Win update and reboot, GRUB bypassed as CPU boots directly to Windows.  Secure Boot is disabled and BIOS UEFI is enabled.  I ran Boot Repair Suggested Options but issue not resolved [http://paste.ubuntu.com/11254929/]("http://paste.ubunutu.com/11254929/").  I have attempted to run sudo efibootmgr -v from Ubuntu live USB but cannot access Root from Terminal.  Help.  Thanks.

---

### Post by oldfred on 2015-05-21
What brand/model system?

Can you use one time boot key, often f10 or f12 to see boot options and use one of the ubuntu entries. One is shim and one is grub. Shim is if you have seccure boot on.

Did you install Ubuntu twice. You have two swap partitions?

You also are missing a Windows highly suggested partition. Did you delete that?
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by ubfan1 on 2015-05-21
You might also check that the Windows power options "fast boot" is turned off.  Some Windows updates turn it back on, and that short-circuits the boot process.

---

### Post by s.boone35223 on 2015-05-22
My computer is a Toshiba Satellite C50-A.  F12 boots to a HDD, USB, DVD option menu (no help).  Fast boot is turned off.  As to configuration, long story but I did a second install of Ubuntu and then installed Windows due to a similar dual boot issue I could not work through.  The set-up worked as I wanted (GRUB menu with Ubuntu default and Windows 8.1 options) until one of the two system updates.a

UPDATE:  I booted while holding the F12 key again.  The HDD menu option does take me to a sub-menu with Windows and Ubuntu.  I can get to Ubunutu although not as cleanly as before.  Any suggestions to get my computer to bring back the Grub menu without having to use the F12 method?

Thanks.

---

### Post by oldfred on 2015-05-22
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by jason2 on 2015-05-24
I am having a similar issue with a Toshiba Satellite E45t-4100. Grub was working fine with my 14.04/Win 8.1 dual boot setup this morning before I installed some updates for Ubuntu. I tried boot-repair twice with no luck, then did a boot summary report. Hopefully it's an easy fix, as I don't want to reinstall Ubuntu.

[http://paste.ubuntu.com/11328814](http://paste.ubuntu.com/11328814)

---

### Post by oldfred on 2015-05-24
@jason2
Better to start own thread. The only reason I have not moved it (yet?) is that it may be similar issue to the OP. Only because both are Toshiba. Often issues are the same by brand, but model can make differences also.

Your boot order is set to boot 3 first which is the SSD entry. A drive boot entry uses the /EFI/Boot/bootx64.efi folder & file, not the Windows or Ubuntu folders & files to boot. Many  with Toshiba have copied grub to /EFI/Boot, renamed bootx64.efi as backup(which it looks like Boot-Repair already did) and rename grubx64.efi or shimx64.efi to be bootx64.efi. Then the hard drive/SSD entry will boot grub/Ubuntu not Windows.
But can you set Ubuntu to be first in boot order, or does Windows reset boot order and cause the issues?
More details on copy files or other work arounds in link in my signature below.
From Boot-Repairs use of:
sudo efibootmgr -v
 ```
BootOrder: [COLOR=#ff0000]0003[/COLOR],0002,0001,0000,0008,0004,0009
Boot0000* Windows Boot Manager    HD(2,200800,32000,e34622ba-f72a-11e3-b0f8-afa01c2ac830)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...2................
Boot0001* UEFI: IP4 Realtek PCIe GBE Family Controller    ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(201a06d8ebd2,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot0002* UEFI: IP6 Realtek PCIe GBE Family Controller    ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(201a06d8ebd2,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot[COLOR=#ff0000]0003[/COLOR]* UEFI: Samsung SSD 840 EVO 250GB    ACPI(a0341d0,0)PCI(1f,2)03120a000000ffff0000HD(2,200800,32000,e34622ba-f72a-11e3-b0f8-afa01c2ac830)..BO
Boot0004* ubuntu    HD(2,200800,32000,e34622ba-f72a-11e3-b0f8-afa01c2ac830)File(EFIubuntushimx64.efi)
Boot0008* Windows Boot Manager    HD(2,200800,32000,e34622ba-f72a-11e3-b0f8-afa01c2ac830)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0009* UEFI: PNY USB 2.0 FD 1100    ACPI(a0341d0,0)PCI(14,0)USB(2,0)HD(1,800,3cf0000,00000000)..BO
```

---

### Post by jason2 on 2015-05-24
Thanks oldfred,

I couldn't figure out how to change the boot order. The bios on my Toshiba will only let me change the hardware device, HHD, USB, etc... I was able to get the Grub menu back after going through the advance boot-repair options. The only thing I changed was I unchecked the Secure Boot option in the Grub Options tab, as I have Secure Boot disabled. Not sure if it was the best thing to do, but it worked. 


...I would normally have posted a new thread. It's just that I found [[COLOR=#000000]s.boone35223[/COLOR]]("http://ubuntuforums.org/member.php?u=1889161")'s issue to be very similar to mine, and we both have Toshiba laptops.

---

### Post by oldfred on 2015-05-24
There should be another UEFI boot menu that lets you select which UEFI entry to boot. If secure boot is on, then only secure boot systems are shown.

Perhaps changing a setting in grub caused it to rerun the UEFI update to make ubuntu entry first.

List entries:
       sudo efibootmgr -v

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

      
  change the BootOrder variable with efibootmgr's -o option
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)

---

