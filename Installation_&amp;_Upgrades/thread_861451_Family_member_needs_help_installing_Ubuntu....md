---
title: "Family member needs help installing Ubuntu..."
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by makinasvp on 2008-07-16
Hi guys, when I first installed Ubuntu on my system, I had a blank HDD which made it very easy for me to install lol.
But now my uncle is very interested to install Ubuntu on his system, but the thing is he already has Windows XP installed in his computer. He has a 500GB HDD and it's being used for Win XP. Is there a simple way to install Ubuntu and have him dual-boot?
If yes, please let me know so I can take care of him.
Thank you!

---

### Post by jerome1232 on 2008-07-16
A: use wubi, just download a live cd pop it in while in windows is running, and use the wubi installer, if he doesnt' like it he can uninstall it like any windows program

B: boot off the live cd and when running the install there's an option to resize existing partition, it will shrink the existing ntfs partition and make room for ubuntu

---

### Post by Pumalite on 2008-07-16
This will help:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by makinasvp on 2008-07-16
Thanks a lot. That howtoforge article was awesome.

---

### Post by makinasvp on 2008-07-16
The reason why I ask is because he's tried to do it before and I don't know what went wrong but in the boot option, he could see both Ubuntu and Windows, but when he tried to launch Windows XP it would not boot. Why is that? Why couldn't windows XP boot?

I'm just trying to do this the right way for him because he had to reformat and re-install windows XP and lost all his data due to that... 

Any help would be greatly appreciated.

---

### Post by Pumalite on 2008-07-16
Do you have Ubuntu installed and working?

---

### Post by makinasvp on 2008-07-16
> **Pumalite said:**
> Do you have Ubuntu installed and working?

No I haven't done anything yet. I'm at his house right now and I've got the Ubuntu CD with me, and so far we haven't done anything. He's got Windows XP installed and that's all. Using his full HDD. 
So I would imagine first I need to use partition magic and resize his partition?

---

### Post by quantum-positron on 2008-07-16
No Ubuntu has its own partition re sizer. however for safety sake i would just install under windows. Just pop in cd auto run will pick it up and ask if you want to install and so on.

---

### Post by Pumalite on 2008-07-16
If you have only one drive, better get Gparted Live CD and 'shrink' XP ahead of time:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
Right click on XP and choose 'resize' from the menu.
The Gparted Live CD works with unmounted drives/partitions. A must in these cases.
Backup everything before you start.
It takes a while.

---

### Post by makinasvp on 2008-07-16
So to sum it up, all I need to do is:

-Resize his partition using partion magic or GParted
-Insert Ubuntu CD
-Click on Install
-Select "Manual" (when it comes to choosing partition)
-Create a "SWAP" partition of 512MB.
-Create a new partition and make it "ext3"
-Click on edit and change mount point to a forward slash /


Am I missing anything?

---

### Post by Partyboi2 on 2008-07-16
I would suggest using gparted not partition magic.
You may not need to use the manual option, there may be another option to use called "Guided use the largest continuous  space" which should use the free space that was created after you shrink down the windows partition with gparted. If not then go with the manual option.

---

### Post by Pumalite on 2008-07-16
Go Manual and create a 'New' partition of all the space minus 1 GB and give it a mount point of '/'. The rest for /swap, then press 'Forward'.

---

### Post by makinasvp on 2008-07-16
> **Partyboi2 said:**
> I would suggest using gparted not partition magic.
You may not need to use the manual option, there may be another option to use called "Guided use the largest continuous  space" which should use the free space that was created after you shrink down the windows partition with gparted. If not then go with the manual option.

But if I do that will the dual-boot be setup properly? Because I really want to make sure Windows XP can boot up after this, because all his files are in there.

---

### Post by Pumalite on 2008-07-16
Let Grub install to MBR (by default) and you'll have dual boot.
Backing up everything is usual in installing a new OS

---

### Post by makinasvp on 2008-07-16
> **Pumalite said:**
> Let Grub install to MBR (by default) and you'll have dual boot.
Backing up everything is usual in installing a new OS

What's MBR? lol

---

### Post by Pumalite on 2008-07-16
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

