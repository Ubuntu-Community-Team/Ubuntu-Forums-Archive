---
title: "Installed Windows 7, now boots straight to Windows 7."
date: 2014-11-10
forum: Installation &amp; Upgrades
---

### Post by davidfischer42 on 2014-11-10
Hi:

All of the threads I read seem to be people who had Windows installed first, and installed Ubuntu after.   I have the opposite situation. 

I had ubuntu 14.04 installed on an SSD, I left 100 GB unallocated.

I then installed Windows 7 into the unallocated space.  It now boots to Windows 7, no boot options.

A lot of the threads talk about using UEFI to set the boot drive, but the both os are on the same drive, just different partitions.

I was hoping for an easy fix like reinstall the boot manager or something.

Thanks,

Dave

---

### Post by yancek on 2014-11-10
That is standard behavior for a windows installation.  It overwrites the master boot record and doesn't ask or inform the user that it is being done.  Just boot the Ubuntu installation medium and reinstall Grub.

[https://help.ubuntu.com/community/Grub2/Installing#Boot_repair_after_a_Windows_Upgrade_on_Ubuntu_14.04_.28non-RAID.29](https://help.ubuntu.com/community/Grub2/Installing#Boot_repair_after_a_Windows_Upgrade_on_Ubuntu_14.04_.28non-RAID.29)

---

### Post by davidfischer42 on 2014-11-13
Yes, that fixed it.  

I'm new to this whole uefi booting thing and feared it was not as simple as that.

---

