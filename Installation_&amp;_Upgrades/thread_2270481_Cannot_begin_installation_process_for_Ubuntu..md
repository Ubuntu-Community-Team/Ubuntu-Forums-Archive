---
title: "Cannot begin installation process for Ubuntu."
date: 2015-03-23
forum: Installation &amp; Upgrades
---

### Post by thomas_4 on 2015-03-23
Hi this is the first time I have tried to install the Ubuntu OS. I created a bootable USB drive formatted as FAT32 and included the most recent Ubuntu OS in it. When I tried to boot from the USB, it went dark and there was a white flashing underscore. Has anyone encountered this issue before? If so, is there a common solution? I included a picture of the screen I'm stuck at.
[ATTACH=CONFIG]260859[/ATTACH]

---

### Post by thomas_4 on 2015-03-23
And sorry for the obvious noobiness when posting... I didn't know it was gonna post both of those photos lol.

---

### Post by Mark Phelps on 2015-03-23
What kind of system are you using to create the USB stick? Linux or Windows?

If you're using Windows, then consider using the Universal USB Installer at pendrivelinux.com.  I've used that repeatedly and it works great.  It does its own reformatting of the USB stick.

---

### Post by yancek on 2015-03-23
The flashing cursor usually means a problem with the creation of the bootable flash.  It could also be that the iso download was bad so do an md5 checksum on the iso to verify the download was good and post back and let us know what software you used to create the bootable flash.

---

### Post by bardo2 on 2015-03-23
> **thomas_4 said:**
>  I created a bootable USB drive formatted as FAT32 and included the most recent Ubuntu OS in it.

Doesnt make sense to me. Ubuntu relies on filesystem permissions, just as windows does with NTFS. FAT32 doesnt have those.

Even if you had no boot problem, you would have lost valuable information in the process. Apart from that i agree to previous poster: There appears to be something wrong with the installation media (or with a BIOS setting).
But myself still uses ISO's, which are somewhat straitforward to use (even without a CD drive), so sorry - no experience with USB. :-(

---

