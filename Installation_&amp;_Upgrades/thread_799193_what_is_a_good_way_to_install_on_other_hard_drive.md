---
title: "what is a good way to install on other hard drive?"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by nerd0795 on 2008-05-18
I was recently thinking about installing ubuntu on my computer.

The thing is I don't want to have a 0.00001% chance of messing up windows vista home premium.  So I thought to my self why don't I add ubuntu to my second unused hard drive.  So what would be a good way to do that with full instructions I'm a huge noob to linux.

and have no chance of damaging windows.  I don't have an install disk.  Stupid company never gave me one.  They gave me an upgrade disk >.<

---

### Post by iaculallad on 2008-05-18
Try this [Link]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")

Actually, its easy installing Ubuntu on another drive with vista already installed on another drive.
Ubuntu offers/does all the work for you. From partitioning your second HDD to integrating vista on your Boot Menu.

---

### Post by VMC on 2008-05-18
> **nerd0795 said:**
> I was recently thinking about installing ubuntu on my computer.

The thing is I don't want to have a 0.00001% chance of messing up windows vista home premium.  So I thought to my self why don't I add ubuntu to my second unused hard drive.  So what would be a good way to do that with full instructions I'm a huge noob to linux.

and have no chance of damaging windows.  I don't have an install disk.  Stupid company never gave me one.  They gave me an upgrade disk >.<

Before you go any further, I would invest into a good backup program. My two venerable programs are Ghost and Acronis TrueImage. You can then clone your Windows partitions and keep in a safe place. I know this is Linux and their is a Linux way of doing backups but those two programs are fast AND secure. I can reimage my XP partition in under 5 minutes! If you don't know how to use them, their are tons of tutorials on both.

---

### Post by Em-Buntu on 2008-05-18
This is the way I have my system setup.
I much prefer to keep operating systems on their individual disks.
If you are new to this, I would suggest you backup your windows disk using either the windoes backup program, or a 3rd party backup.
Simply make a new smaller partition on your windows disk, maybe 5-10GB, and point the backup there.

The only way you can mess up your windows installation is to mistaken point Ubuntu to install on HD0 and partition and format over your windows installation.

When you start Ubuntu Live, it will see the windows disk (HD0) and your new disk (HD1). 
You should be able to distiguish which disk is which by noting the size of each.
For example, my Windows drive is 400GB (HD0), while my Ubuntu drive is 200GB (HD1).

Don't point the Ubuntu install to your Windows disk which should be HD0. The second disk should be HD1 assuming these are the only drives in your system. Point the install to HD1, but select the advanced option in the partition section to install grub on HD0. Grub will integrate the Windows boot option into it's menu and will read on reboot.

From there you should be good to go.

---

### Post by ugm6hr on 2008-05-19
Closed.

[http://ubuntuforums.org/showthread.php?p=4992192#post4992192](http://ubuntuforums.org/showthread.php?p=4992192#post4992192)

---

