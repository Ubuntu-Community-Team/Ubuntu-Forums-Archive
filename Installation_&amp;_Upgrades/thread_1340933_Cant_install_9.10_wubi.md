---
title: "Cant install 9.10 wubi"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by antonthe on 2009-11-29
i found this old laptop yesterday, and decided to play around with wubi installer. but it wont install. everything goes fine until i am prompted to reboot the computer. i do so, and nothing happens, ubuntu installer doesnt start after reboot, just boots normal windows xp. what could be the problem?
i ran the chkdsk on the partition i am installing ubuntu on, but it didnt help

---

### Post by antonthe on 2009-11-29
bump

---

### Post by darkod on 2009-11-29
> **antonthe said:**
> i found this old laptop yesterday, and decided to play around with wubi installer. but it wont install. everything goes fine until i am prompted to reboot the computer. i do so, and nothing happens, ubuntu installer doesnt start after reboot, just boots normal windows xp. what could be the problem?
i ran the chkdsk on the partition i am installing ubuntu on, but it didnt help

You are aware that wubi installs sort of "virtual" ubuntu inside windows right? The partition you are mentioning should be ntfs and visible from windows.
On the other hand, the boot menu after restarting should have showed you option for ubuntu. Does it just boot into xp normally? If you go in add/remove programs in windows is there ubuntu entry like an app?

PS. Other options to use ubuntu on the laptop to see how it works is to boot with ubuntu cd and select Try Ubuntu option. That will not make any change on the laptop, it just runs ubuntu from the cd.

---

### Post by phillw on 2009-11-29
> **antonthe said:**
> i found this old laptop yesterday, and decided to play around with wubi installer. but it wont install. everything goes fine until i am prompted to reboot the computer. i do so, and nothing happens, ubuntu installer doesnt start after reboot, just boots normal windows xp. what could be the problem?
i ran the chkdsk on the partition i am installing ubuntu on, but it didnt help

Did you install according to this ? [http://wubi-installer.org/](http://wubi-installer.org/)

Regards,

Phill.

---

### Post by antonthe on 2009-11-29
> **darkod said:**
> You are aware that wubi installs sort of "virtual" ubuntu inside windows right? The partition you are mentioning should be ntfs and visible from windows.
On the other hand, the boot menu after restarting should have showed you option for ubuntu. Does it just boot into xp normally? If you go in add/remove programs in windows is there ubuntu entry like an app?

PS. Other options to use ubuntu on the laptop to see how it works is to boot with ubuntu cd and select Try Ubuntu option. That will not make any change on the laptop, it just runs ubuntu from the cd.
the partition is ntfs and visible from windows. but no ubuntu option is showing on the startup. just boots into xp normally, and theres ubuntu entry in the add/remove.

followed the instructions from wubi-installer.org, yeah.

---

### Post by darkod on 2009-11-29
If it's in add/remove it should be installed. Have no idea why windows didn't add it to boot menu.
Personally, I hate wubi. Unless you really have specific reason, I would say remove it using add/remove like any windows app.
Then if you just want to try Ubuntu boot with the cd and select Try Ubuntu option. That will allow to work from the cd.
If you decide you want it, install proper dual boot. It will work much faster, and wubi will start creating problems later on. It's difficult to make linux work inside windows. Ubuntu shouldn't have even tried it IMHO.

---

### Post by antonthe on 2009-11-29
oh ic. i guess it has something to to with windows boot manager. trying to find out now.

can i install normal ubuntu to a partition, while keeping windows unchanged? is there a guide(the one for dummies)?

---

### Post by darkod on 2009-11-29
Of course you can, that's the point of dual booting. You wouldn't have dual OS if windows gets destroyed right. :)

The ubuntu installer can do everything for you but there are few steps I prefer to do manually first, it helps. The main thing is resizing (shrinking) your windows partition because at the moment windows is taking your whole HDD and there is no free unpartitioned space to create ubuntu partition in it.

If you are running windows now you can open Disk Management and check which partitions you have right now, their size and free space. I recommend removing the wubi install first because that will free the space dedicated to wubi.

Easiest way to open Disk Management is: windows button + R, in the small windows type diskmgmt.msc and hit Enter. It will display your partitions, sizes and free space. What are they?

---

### Post by antonthe on 2009-11-29
i got a c: 9/27 gb and d: 27/29gb right now(free/total)

---

