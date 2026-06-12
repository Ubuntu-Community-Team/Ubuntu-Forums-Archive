---
title: "not booting windows after installing ubuntu 11.10"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by greathtg on 2011-12-22
i installed ubuntu 11.10 on my dell laptop alongside windows 7. but after installing it, it's not giving me an option of booting windows 7 or ubuntu. It's directly booting ubuntu. any help ?

---

### Post by Quackers on 2011-12-22
In Ubuntu try opening a terminal and run ```
sudo update-grub
```
You should see the Windows Loader recognised as grub.cfg is run. If so, reboot and you should see a grub menu giving you the choice of which OS to boot.

---

### Post by emmomalick on 2011-12-22
> **greathtg said:**
> i installed ubuntu 11.10 on my dell laptop alongside windows 7. but after installing it, it's not giving me an option of booting windows 7 or ubuntu. It's directly booting ubuntu. any help ?
You have to re-install your GRUB. Follow the steps from here.

[http://www.tuxgarage.com/2011/01/re-installing-grub2.html](http://www.tuxgarage.com/2011/01/re-installing-grub2.html)

---

### Post by Quackers on 2011-12-22
> **emmomalick said:**
> You have to re-install your GRUB. Follow the steps from here.

[http://www.tuxgarage.com/2011/01/re-installing-grub2.html](http://www.tuxgarage.com/2011/01/re-installing-grub2.html)

That is sometimes required, but usually when Windows is installed after Ubuntu.

---

### Post by darkod on 2011-12-22
Did you delete any partitions before installing it? You might have deleted the small win7 partition with the boot files.

Follow the link in my signature to run the boot info script and post the results as explined there. It should show more details.

---

### Post by emmomalick on 2011-12-22
> **Quackers said:**
> That is sometimes required, but usually when Windows is installed after Ubuntu.
Yeah, may be it is. 

Just updating grub is the easiest way to solve it. It adds the Windows 7 Bootloader automatically to the grub.cfg file. 

I am Right?

---

### Post by Quackers on 2011-12-22
Yes, that's right - assuming that there are no other problems such as missing boot files (or partition) or os-prober not being installed.

---

### Post by emmomalick on 2011-12-22
:) I got it. Thanks.

---

### Post by Mark Phelps on 2011-12-22
> **emmomalick said:**
> :) I got it. Thanks.

You mean you understand the solution? Or, you were able to fix it?

If the second, please share how you fixed it.  That will help others enormously in the future with similar problems.

thanks

---

### Post by gordintoronto on 2011-12-22
If you've never done this before, it's also possible that you wiped out Windows when you installed Ubuntu.

---

### Post by emmomalick on 2011-12-23
No I mean that I understand the solution of this problem clearly.

---

### Post by greathtg on 2011-12-26
Yeah. I had windows xp on that partition, so i deleted it and installed ubuntu on it. and updating grub didn't help. still booting directly into ubuntu.

---

### Post by darkod on 2011-12-26
> **greathtg said:**
> Yeah. I had windows xp on that partition, so i deleted it and installed ubuntu on it. and updating grub didn't help. still booting directly into ubuntu.

Finally, the OP replied. :)

If you had both XP and 7 at the same time, and later you deleted the XP partition, you probably deleted the 7 boot files too. Windows works in mysterious ways, it combines the boot files if you have more than one version.

When you install XP, the boot files are together on C:. When you later add 7, it puts two boot files that it needs on the partition where other boot files are, in this case the XP partition. The user is not even aware of this and it never asks you if you want to do it this way.
Later when you delete the XP partition, the 7 boot files are gone. And Ubuntu searches for boot files, doesn't find any, so it thinks there is no other OS present.

Boot ubuntu and open Gparted (you might need to install it). In Gparted find the disk with 7 and the partition which is the C: in 7. Then right-click, select Manage Flags, and set the boot flag on it.
Then use the win7 dvd and the option Repair This Computer few times. If you are lucky it will repair the boot files.
In case this deletes grub (because I don't know your exact setup), ask here first about restoring grub on the MBR if you don't know how to do it. Don't do the mistake many make by installing second ubuntu right away. There is a very elegant way to restore grub.

---

