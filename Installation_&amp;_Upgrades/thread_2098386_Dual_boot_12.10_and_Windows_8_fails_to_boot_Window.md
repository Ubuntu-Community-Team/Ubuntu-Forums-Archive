---
title: "Dual boot 12.10 and Windows 8 fails to boot Windows"
date: 2012-12-26
forum: Installation &amp; Upgrades
---

### Post by ezraw on 2012-12-26
System loads Ubuntu just fine, but reports the following error when I boot Windows.

[http://paste.ubuntu.com/1467596/](http://paste.ubuntu.com/1467596/)

Depending on which option I choose at boot, I get one of the following errors:

file path: cannot load image
or
secure boot forbids loading module...


Can anyone give help solve this?

---

### Post by oldfred on 2012-12-26
It looks like Boot-Repair added correct efi chain load entries. Grub has a bug.
New entry that should work
> Windows UEFI loader
Old entries that will not work:
> Windows 8 (loader) (on /dev/sda4)

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

    
When using the UEFI loader entry are you still getting errors?

---

### Post by ezraw on 2012-12-26
Thanks for your reply.

Yes, I get errors on all entries, including the UEFI loader.

The specific error is

/EndEntire
file path:.. [long path here]....
error: cannot load image

---

### Post by oldfred on 2012-12-26
You did shrink Windows a lot. Did you do that from Windows MMC, gparted or the Ubuntu installer? Best to use Windows MMC & reboot several times as Windows has to run chkdsk or make other repairs on a resize. Sometimes when done from outside Windows it has issues and will not start its chkdsk automatically.

You have a lot of boot options with Lenovo. Can you boot Windows directly from UEFI menu. Or run repairs?

```
BootOrder: 0019,0007,0018,0000,0001,0002,0003,0008,0009,000A,000B,000C,000D,000E,000F,0011,0010,0012
Boot0000  Setup
Boot0001  Boot Menu
Boot0002  Diagnostic Splash Screen
Boot0003  Lenovo Diagnostics
Boot0004  Startup Interrupt Menu
Boot0005  ME Configuration Menu
Boot0006  Rescue and Recovery
Boot0007* USB CD
Boot0008* USB FDD
Boot0009* ATAPI CD0
Boot000A* ATA HDD0
Boot000B* ATA HDD1
Boot000C* ATA HDD2
Boot000D* USB HDD
Boot000E* PCI LAN
Boot000F* ATAPI CD1
Boot0010  Other CD
Boot0011* ATA HDD3
Boot0012  Other HDD
Boot0013* IDER BOOT CDROM
Boot0014* IDER BOOT Floppy
Boot0015* ATA HDD
Boot0016* ATAPI CD:
Boot0017* PCI LAN
Boot0018* Windows Boot Manager
Boot0019* ubuntu
```

---

### Post by ezraw on 2012-12-26
I shrunk Windows using the Windows MMC and then rebooted a few times.

Not sure if this is relevant, but I did use the Ubuntu Secure Remix iso. 

Can you provide steps for booting Windows directly from UEFI menu? I'm not sure where to find this.

---

### Post by oldfred on 2012-12-26
From a total power down or cold boot.

Lenovo
BIOS Utility F2 or blue “Thinkpad” button
Boot Menu F12

That should get you into UEFI/BIOS.

Every UEFI menu looks different.

---

### Post by ezraw on 2012-12-26
If I turn off secure mode it will boot into Windows from the UEFI menu.

---

### Post by oldfred on 2012-12-26
And with secure boot off will Ubuntu boot from grub menu & Windows boot from grub menu?
Some say they find it works with secure boot on or off, others seem to have to have it off.
Ubuntu is using the Microsoft key, so it should work with secure boot on.

       [http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/)

---

