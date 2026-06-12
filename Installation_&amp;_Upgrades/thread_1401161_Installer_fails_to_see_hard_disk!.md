---
title: "Installer fails to see hard disk!"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by Snowflake128 on 2010-02-07
I have a VERY weird problem. The Install program is failing to see the hard disk! 

Now heres the really weird bit. The live cd can see the drive just fine. I have created partitions using gparted and the disktool also sees the drive just fine but as soon as I go back to the installer it shows no hard disk!

It's a SATA drive which I suspect might be a part of the problem.

Is there a way I can install without the install program?

Is there a way to make the install program see the drive?

This is ubuntu 9.10 desktop.

Hope you can help! :)

---

### Post by darkod on 2010-02-07
If the drive has been used in raid, some settings remain and this happens. Even if it wasn't, sometimes settings remains are there.
Boot the live desktop, and if this is your only hdd it would be called /dev/sda, in terminal execute:

sudo dmraid -E -r /dev/sda
sudo apt-get remove dmraid

That will get rid of them. Start the install process again and it should be fine.
If the drive is /dev/sdb, or /dev/sdc, etc, just modify the first command.

PS. DO NOT do this if you are actually running raid. It will DESTROY the array.

---

### Post by Snowflake128 on 2010-02-07
> **darkod said:**
> If the drive has been used in raid, some settings remain and this happens. Even if it wasn't, sometimes settings remains are there.
Boot the live desktop, and if this is your only hdd it would be called /dev/sda, in terminal execute:

sudo dmraid -E -r /dev/sda
sudo apt-get remove dmraid



THANKYOU Darkod!!!

Genius!

It's now all up and running great! I just need to work out how to put an XP entry into Grub, but I'm hoping that will be easy!

Phew!

It barfed all over the first command BTW but after I removed dmraid all seemed to be good!

Thanks again! :)

---

