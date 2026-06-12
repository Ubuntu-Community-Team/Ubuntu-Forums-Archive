---
title: "No boot into Windows after running boot-repair"
date: 2012-12-03
forum: Installation &amp; Upgrades
---

### Post by camsolo on 2012-12-03
I am trying to set up a dual-boot computer with Ubuntu 12.10 and Windows  8. After running boot-repair, I am unable to boot into Windows. When I  try to do so, I receive the following error messages:

error: can't find command `drive map'.
error: invalid EFI path.

My (latest) boot info report is here: [http://paste.ubuntu.com/1407603/](http://paste.ubuntu.com/1407603/)

I have been struggling with this for several days and have run boot-repair many times. Here are some older reports:

[http://paste.ubuntu.com/1397570/](http://paste.ubuntu.com/1397570/)
[http://paste.ubuntu.com/1397966/](http://paste.ubuntu.com/1397966/)
[http://paste.ubuntu.com/1404467/](http://paste.ubuntu.com/1404467/)
[http://paste.ubuntu.com/1404517/](http://paste.ubuntu.com/1404517/)
[http://paste.ubuntu.com/1404750/](http://paste.ubuntu.com/1404750/)
[http://paste.ubuntu.com/1407482/](http://paste.ubuntu.com/1407482/)
[http://paste.ubuntu.com/1407603/](http://paste.ubuntu.com/1407603/)

---

### Post by YannBuntu on 2012-12-03
> Hi Yann,

Many thanks for your speedy reply!

I have followed your instructions.

The new URL is:
[http://paste.ubuntu.com/1407726/](http://paste.ubuntu.com/1407726/)

After rebooting, GRUB gives me three options for Windows:

Windows UEFI loader
Windows Boot UEFI bootx64.efi.bkp
Windows (on /dev/sda5)

I tried the first one, and booted successfully into Windows. I haven't tried the other two. I checked that I can still boot into Ubuntu, and I can. So my problem seems to be solved! But I would like to know what the other two options are.

"Windows UEFI loader" and "Windows Boot UEFI bootx64.efi.bkp" were created by Boot-Repair and should both boot Windows.

"Windows (on /dev/sda5)" was created by GRUB. Please try it and tell me what it does.

> p.s. I am confused by this message from boot-repair:

Please do not forget to make your BIOS boot on sda1/EFI/unbuntu/grubx64.efi

I don't know how to do this.

You don't have anything more to do, because your BIOS is already correctly setup.

---

### Post by camsolo on 2012-12-03
> **YannBuntu said:**
> 
"Windows (on /dev/sda5)" was created by GRUB. Please try it and tell me what it does.


It returns these errors:

```
error: can't find command `drivemap'.
error: invalid EFI file path.
```

---

### Post by YannBuntu on 2012-12-03
ok, then you can login to your Launchpad.net account (create one if you haven't yet), then go on this page:[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
click "Does this bug affect you?" --> Yes

---

### Post by bandeszka on 2012-12-05
I have got exactly the same problem. I have a samsun laptop with a preinstalled win 8. When I installed ubuntu 12.10 then I cannot boot ubuntu first. So I boot from the Ubunto install disk. And then I repaired the boot with bootrepaire, but the"recommended repaire" did not work for me and it messed up the entire boot process. Then in the bootrepaire advanced option I set the secure boot that fixed half of the issue. So I can boot Ubuntu but I cannot boot Win 8. Selecting the Windows UEFI from the grub's list I receive the "can't find drivemap command" message.
More information: With bootrepaire "recommended repaire" may messed up the BIOS also since I received "IMAGE FAILED TO VERIFIED WITH *ACCESS DENIED*" error message.

Please inform me about the bug entry.

---

### Post by YannBuntu on 2012-12-05
Hello, and welcome among us! :)

> **bandeszka said:**
> I have got exactly the same problem. I have a samsun laptop with a preinstalled win 8. When I installed ubuntu 12.10 then I cannot boot ubuntu first. So I boot from the Ubunto install disk. And then I repaired the boot with bootrepaire, but the"recommended repaire" did not work for me and it messed up the entire boot process. Then in the bootrepaire advanced option I set the secure boot that fixed half of the issue. So I can boot Ubuntu but I cannot boot Win 8. Selecting the Windows UEFI from the grub's list I receive the "can't find drivemap command" message.
More information: With bootrepaire "recommended repaire" may messed up the BIOS also since I received "IMAGE FAILED TO VERIFIED WITH *ACCESS DENIED*" error message.

Please inform me about the bug entry.

Your situation is different (your "Windows UEFI" entry fails, but camsolo's one doesn't).
Please could you create your own new thread [THERE]("http://ubuntuforums.org/newthread.php?do=newthread&f=333") (then indicate the link here, so we can follow-up) ?
Also, please indicate the URL provided by the Recommended Repair, it will help us to help you.

---

### Post by bandeszka on 2012-12-10
I would create one but it seems I do not have permission to create a tag.

"You do not have permission to create tags. You may only use existing tags."

---

### Post by bandeszka on 2012-12-10
Sorry, I did it. 
[http://ubuntuforums.org/showthread.php?p=12397838#post12397838](http://ubuntuforums.org/showthread.php?p=12397838#post12397838)
Please check it.

---

