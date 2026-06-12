---
title: "No grub after installation of 18.04 server"
date: 2018-10-09
forum: Installation &amp; Upgrades
---

### Post by spookybathtub on 2018-10-09
I've created a USB installer for 18.04.1 server using Etcher on a Mac.  I'm trying install Ubuntu to another USB drive.  The installer goes well with no errors, and I choose "full disk" to install to my 32GB USB drive.  But when I try to boot to this new drive, it doesn't work.  The PC just says "non-system disk or disk error".
I put the drive in another system (CentOS in VirtualBox) and it appears to not have grub installed:
```
file -s /dev/sdb
/dev/sdb: x86 boot sector: partition 1: ID=0xee, starthead 0, startsector 1, 60063743 sectors, extended partition table (last)\011, code offset 0x63
```

I try to install grub:
```
grub2-install /deb/sdb
Installing for i386-pc platform.
Installation finished. No error reported.
```

After this, file -s shows the same thing and it still won't boot.  Any ideas what's wrong here?

---

### Post by oldfred on 2018-10-09
UEFI or BIOS? 
You are installing grub-pc, so system must be set to boot in BIOS boot mode.

What brand/model system?

Server does not have live mode, but good to have live installer as repair tool anyway.
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Just run the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

