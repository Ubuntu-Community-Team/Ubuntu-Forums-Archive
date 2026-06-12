---
title: "Error Upgrading linux-restricted-modules-2.6.20-15-generic"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by xoom on 2007-04-24
I'm getting the following error. I thought I had resolved it previously by making my boot partition larger but it doesn't look like that did it.


~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-restricted-modules-2.6.20-15-generic (2.6.20.5-15.20) ...
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/i2c/busses/i2c-isa.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/i2c/busses/i2c-prosavage.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/i2c/busses/i2c-ocores.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/i2c/busses/i2c-via.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/i2c/busses/i2c-savage4.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/i2c/busses/i2c-i801.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/i2c/busses/i2c-i810.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/i2c/busses/i2c-piix4.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/i2c/busses/i2c-parport-light.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/i2c/busses/i2c-parport.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/i2c/busses/i2c-pca-isa.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/i2c/busses/i2c-stub.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/i2c/busses/scx200_acb.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/i2c/busses/scx200_i2c.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/i2c/busses/i2c-sis630.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/i2c/busses/i2c-nforce2.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/ide/ide-pnp.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/ide/ide-disk.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/ide/ide-tape.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/ide/ide-floppy.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/ide/ide-cd.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/char/tpm/tpm_bios.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/char/tpm/tpm.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/char/tpm/tpm_infineon.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/char/tpm/tpm_nsc.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/char/tpm/tpm_tis.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/char/tpm/tpm_atmel.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/char/ipmi/ipmi_watchdog.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/char/ipmi/ipmi_si.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/char/ipmi/ipmi_devintf.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/char/ipmi/ipmi_poweroff.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/char/cyclades.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/edac/e7xxx_edac.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/edac/r82600_edac.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/edac/i82875p_edac.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/drivers/edac/i82860_edac.ko is not an elf object
Segmentation fault (core dumped)
dpkg: error processing linux-restricted-modules-2.6.20-15-generic (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.20-15-generic; however:
  Package linux-restricted-modules-2.6.20-15-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-restricted-modules-2.6.20-15-generic
 linux-restricted-modules-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by xoom on 2007-04-24
anyone?

---

