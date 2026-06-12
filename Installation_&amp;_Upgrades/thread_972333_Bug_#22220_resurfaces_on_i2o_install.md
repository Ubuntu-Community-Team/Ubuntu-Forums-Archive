---
title: "Bug #22220 resurfaces on i2o install"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by eye-wipe on 2008-11-05
Can anyone else confirm the re-emergence of Bug #22220 in hw-detect on Intrepid Desktop/Server/Alternate CDs?

This bug causes a kernel panic at the start of the install with error messages

iop0: Device already claimed
iop0: DMA/IO allocation for I2O controller failed

The same happens when trying to run the LiveCD

I believe it is caused by the installer loading the Adaptec dpt_i2o module and then the kernel i20_core module attempts to load on the same controller.

See[https://launchpad.net/ubuntu/+source/hw-detect/+bug/22220]("https://launchpad.net/ubuntu/+source/hw-detect/+bug/22220")
This was fixed in 6.04 (by Colin Watson?? or Ben Collins??)

The only workaround I know is to do an inplace upgrade from an earlier version - but if it doesnt work I could be left with a non-booting system. Has anyone tried this?

H/Ware is an Intel M/B with Adaptec 2100S I2O controller RAID 0+1
4 SCSI disks

Any help/comments/suggestions??

Thanks in advance

---

