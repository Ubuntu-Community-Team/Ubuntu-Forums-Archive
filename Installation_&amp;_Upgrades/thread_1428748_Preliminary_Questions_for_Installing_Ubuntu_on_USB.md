---
title: "Preliminary Questions for Installing Ubuntu on USB Flash Drive"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by Spirrwell on 2010-03-13
I have an 8 GB USB flash drive that's not really doing anything right now. So I decided I'd install Ubuntu on it. I want to do this so I can use Ubuntu on multiple computers. I'm not sure what Ubuntu version it is that I have on CD, but I checked properties of the wubi.exe and found out it was created October 26, 2009. Hope that helps. But when I install Ubuntu on my flash drive, will it change the bootloader on my computer from Vista Bootloader to GRUB bootloader? If so would turning off my hard drives fix this problem or is there something else I would have to do so I could limit GRUB to my USB flash drive? 

-----------------------------------

Thanks in advance!

---

### Post by phillw on 2010-03-13
> **Spirrwell said:**
> I have an 8 GB USB flash drive that's not really doing anything right now. So I decided I'd install Ubuntu on it. I want to do this so I can use Ubuntu on multiple computers. I'm not sure what Ubuntu version it is that I have on CD, but I checked properties of the wubi.exe and found out it was created October 26, 2009. Hope that helps. But when I install Ubuntu on my flash drive, will it change the bootloader on my computer from Vista Bootloader to GRUB bootloader? If so would turning off my hard drives fix this problem or is there something else I would have to do so I could limit GRUB to my USB flash drive? 

-----------------------------------

Thanks in advance!

Hi and welcome to the forums. I assuming that you are running ubuntu from within windows as you mention wubi. However that is no big deal.

Assuming the CD is 9.10 then boot with it using the 'do not alter my computer' option.
Then goto "Create USB Startup Disk" (or words to that effect, you'll find it under System --> Administration)

That will create a stand-alone usb-booting stick for you and will not make any changes to your existing set-up (no need to worry about grub)

You can only use 4GB for the saved files area, although you can format the remainder of the usb stick to ext3 / ext4 (or ntfs, if you want) and mount it as a seperate partition (e.g. call it data) you'll then be able to store stuff on that area and have it available whenever you plug the stick in.

Regards,

Phill.

---

