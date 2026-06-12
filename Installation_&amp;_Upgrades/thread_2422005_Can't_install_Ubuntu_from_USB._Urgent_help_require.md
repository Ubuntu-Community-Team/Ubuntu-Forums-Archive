---
title: "Can't install Ubuntu from USB. Urgent help required."
date: 2019-06-30
forum: Installation &amp; Upgrades
---

### Post by zain-97 on 2019-06-30
dual-boot uefi 18.10 acer
I use an Acer laptop. I wanted to install Ubuntu alongside windows on a dual boot. I did so successfully. I realised that the partition space I had for Ubuntu was not enough so I decided to delete the partition on windows disk manager and create a bigger partition to install Ubuntu on. Now when I try to install Ubuntu from my bootable USB it gives me this error:

Failed to open \EFI\BOOT\mmx64.efi - Not Found Failed to load image \EFI\BOOT\mmx64.efi - Not Found Failed to start MokManager: Not Found Something has gone seriously wrong: import_mok_state() failed : Not Found

What should I do?

---

### Post by yancek on 2019-07-01
Not sure I'm reading your post correctly.  Did you delete the Ubuntu partitiion from windows?  Are you able to boot windows?  We'll need more info and boot repair should provide that.  Boot the Ubuntu install usb and go online to the boot repair site below, use the 2nd option on that page to download the ppa to install boot repair and run it per instructions on the page.  Select the Create BootINfo Summary option and do NOT try to make any repairs.  When it finishes, you should get a link to post here which will provide enough information on your system that someone should be able to suggest a solution.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Impavidus on 2019-07-01
18.10 is almost end-of-life. Don't install it. Use 18.04 LTS or 19.04 instead.

---

