---
title: "ubuntu 14.04 + uefi = no bootable device"
date: 2015-09-01
forum: Installation &amp; Upgrades
---

### Post by kirasole on 2015-09-01
I'm absolutely done trying to install ubuntu to a new laptop. It's Acer Aspire ES1-131, I got it with Win8, disabled Security boot, left UEFI mode on, then made an Ubuntu 14.04.3 flash usb. Booted with it, used GParted to delete all partitions, made GPT table, than made 100 Mib of fat32 for EFI and other ext4 partitions for ubuntu. Installed ubuntu, rebooted and... nothing. "No bootable device", and there is only my flash usb stick in the boot list. I ran boot-repair and it changed nothing. 
[http://paste.ubuntu.com/12245631/](http://paste.ubuntu.com/12245631/)

Also I noticed that changes I do with efibootmgr are all gone after rebooting.
"efibootmgr -v" looks like this:
```
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0001,0000
Boot0000* USB HDD: VerbatimStore n Go Drive    ACPI(a0341d0,0)PCI(14,0)USB(1,0)HD(1,800,77f7df,fae5c804-518a-4f6c-b083-58b5c51908ab)RC
Boot0001* ubuntu    HD(1,800,32000,fc73d5d8-9a27-4d8b-8fd9-c066d7ecaa1b)File(EFIubuntugrubx64.efi)
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC
```

I also tried to set Bootnext to 1 manually, but after reboot I got "default boot device missing or boot failed".

So, what is the problem or how can I find it?

---

### Post by kirasole on 2015-09-01
LOL, suddenly, it was solved with this [http://askubuntu.com/a/653202/445571](http://askubuntu.com/a/653202/445571) and boot-repair again :)

---

