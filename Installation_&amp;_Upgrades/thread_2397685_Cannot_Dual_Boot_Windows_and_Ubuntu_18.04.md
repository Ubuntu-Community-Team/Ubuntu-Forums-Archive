---
title: "Cannot Dual Boot Windows and Ubuntu 18.04"
date: 2018-08-01
forum: Installation &amp; Upgrades
---

### Post by davidchenyt on 2018-08-01
After installing Ubuntu 18.04 the system does not show the grub menu but defaults to Ubuntu 18.04 directly.

I have already run boot-repairer. The URL for the report is [http://paste.ubuntu.com/p/WRVBD7YtTM/](http://paste.ubuntu.com/p/WRVBD7YtTM/)

As I am a newbie, any help I can get to fix this problem will be greatly welcomed.

Thanks!

---

### Post by oldfred on 2018-08-01
Does not look like a standard Windows UEFI boot configuration.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

But you still have an UEFI boot of Windows in the UEFI  boot menu.
But it has in it the GUID of an ESP - efi system partition that does not now exist.
You should only have one ESP per drive. Was Windows booting from another drive now disconnected or did you delete some required partitions for Windows? (See above).

You will need your Windows repair disk or Windows installer with repair console to reinstall Windows boot files into new ESP.

If you do not have Windows repair/recovery flash drive.
[https://answers.microsoft.com/en-us/windows/forum/windows_10-windows_install-winpc/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085](https://answers.microsoft.com/en-us/windows/forum/windows_10-windows_install-winpc/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085)

You should always backup system before any major system change. So if you spent any time configuring Ubuntu, be sure to back it up before repairing Windows.

---

