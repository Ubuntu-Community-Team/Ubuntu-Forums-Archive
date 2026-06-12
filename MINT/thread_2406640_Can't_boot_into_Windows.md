---
title: "Can't boot into Windows"
date: 2018-11-23
forum: MINT
---

### Post by mithil467 on 2018-11-23
I installed Linux Mint on my PC today, which already had windows 10 installed. I created partitions for efi,swap and /. Now I am facing some issues and can't get back into windows 10. The GRUB menu shows linux mint and advanced options only. I checked inside the advanced options also but there is no windows 10. I have previously installed ubuntu and just today installed linux mint. I don't have much knowledge and am a newbie. Please help me.

---

### Post by oldfred on 2018-11-23
Moved to the Mint sub-forum.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you created a second ESP - efi system partition that could be the issue.
You can only have one ESP per device/drive. That is the FAT32 partition with boot flag.

---

### Post by mithil467 on 2018-11-24
Thanks for your reply @oldfred. While installing I got a notification that you might not be able to boot into any other operating system, but I didn't pay heed and proceeded the installation. Then I created a 300 MB partition for EFI as the installaton failed twice at installing grub part but then succeeded after creating that partition. Then my computer booted directly into Linux Mint without showing any options so I installed boot-repair and now it shows the GRUB with only linux and advanced options but not windows 10. I don't really know much about handling such issues, please help.

---

### Post by yancek on 2018-11-24
If you had windows 10 pre-installed, it likely already had an efi partition and there would have been no need to create another.  The Mint installer would have created a separate directory in the EFI partition for Mint.  The purpose of running boot repair as suggested would be to post information on your system and not try to make repairs.  Boot repair has an option to Create BootInfo Summary and that is what you need to select when you run it again.  When it finishes, it should show a link which you can post here so that members can view some details on your system and make suggestions to repair.

---

