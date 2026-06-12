---
title: "error: no such device: Dual Boot Windows 10 Unbuntu 14.04.3"
date: 2015-10-12
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2015-10-12
Hello,

I just cloned my dual boot system with EasyGIG IV version 4.38 and I received the following error message when I selected Windows 10 from the boot menu.

```

error: no such device: A6CC3S81CC354D35
Setting partition to type 0x7

Press any key to continue

```

I also had to repair Windows Startup with the installation disc; and luckily, when I was finally able to boot, all my files and settings were undamaged. I also ran "chkdsk /f" and rebooted twice for good measure. I also checked the partition with GParted and there were no problems reported with any of the partitions and the boot flag was correctly set on the correct partition. For good measure I also reset Windows. This didn't get rid of the above error message.

I suspect the above error message originates from Grub. What does it mean and what can I do to get rid of it?

Thanks Hannibal

---

### Post by yancek on 2015-10-12
If you cloned and then moved both systems to another computer or another hard drive the error means you have an entry in grub.cfg for the windows partition on the old drive.  That is the UUID for the old partition.  You can find the partition UUID with:  sudo blkid

---

### Post by oldfred on 2015-10-12
Have you unplugged old drive if still in same computer?
You cannot have duplicate UUID or GUIDs which cloned drive creates.

Or if only new drive UUID should be the same and grub should work.
May then be best to see details:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

