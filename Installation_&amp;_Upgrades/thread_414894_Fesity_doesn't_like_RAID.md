---
title: "Fesity doesn't like RAID?"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by erolagnab on 2007-04-20
Hi all,

As soon as Feisty was out, I downloaded and tried to install on my server.... but things didn't work out very well...

My server runs RAID 5 on SCSI harddisk and uses Adaptec 2000s RAID Card, during the installation, Feisty didn't complain anything, but after the reboot, it couldn't start up and showing some errors like:

dpti: adpt_config_hba: pci request region failed
Could not Init an I2O RAID device
........<serires of buffer I/O error>
ldm_validate_partition_table(): disk read failed
........<serires of buffer I/O error>

I've googled and found a bug here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/22220](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/22220)

Not sure this has been fixed in Feisty or do I need to configure something else before installation?

Very appreciate for any help ... I just can't let one of my server idle for too long ...

Thanks for reading this

Trung

PS: Dapper also failed and ended up with the same error

---

### Post by erolagnab on 2007-04-21
Upz.... plz help, Ubuntu team ...

---

