---
title: "Ubuntu Server 12.04 set up on a software RAID 5 won't boot."
date: 2013-09-27
forum: Installation &amp; Upgrades
---

### Post by Brad_Lauk on 2013-09-27
Here's the skinny. I'm setting up a Samba server on Ubuntu Server 12.04, and wanted to get a software RAID 5 going on it. I manually set up 3 separate RAID partitions. One for an EFI boot, another for the actual fileshare server install and then a swap file. However, when I finish the install and reboot, it takes me to a screen for the BIOS/Motherboard saying no boot device is found.

I did some digging and read that this is because of a bug on 12.04 related to GRUB not somehow working. I don't know much about Ubuntu or Linux but I had also read that you can manually configure GRUB from a live cd. Does anybody have a link to, or can just tell me how I could go ahead in doing this?


Specs are

[LIST]
[*]MSI B75MA-E33
[*]4GB RAM
[*]3 x 1TB WD Black drives
[/LIST]

Thanks for your time!

---

