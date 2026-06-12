---
title: "Installing Windows with Ubuntu 7.04"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by punkkid219 on 2008-03-30
I have installed Ubuntu before but, I have installed windows to.

But heres my problem I am willing to Give Ubuntu another chance. but I need some help. I have windows installed without any Partitions So do I need to install Windows then Partition it then install Ubuntu or Can I install Ubuntu with windows without Partitioning it?

Also Ive heard the name GRUB loader thrown around a lot when I install ubuntu with windows im going to need some kind of app to chose with OS I want to boot could someone help me with this?

Much Thanks guys!!:guitar:

---

### Post by Pumalite on 2008-03-30
Vista or XP?

---

### Post by pseudo-random on 2008-03-30
You need to have two partitions, one windows, another ubuntu.
You can do this from the ubuntu live CD.
GRUB can be configured by editing your /boot/menu.lst file.
Instructions are in the file.
I recommend searching for a tutorial on 'dual booting windows and ubuntu'.

---

### Post by Pumalite on 2008-03-30
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by mikewhatever on 2008-03-30
Follow this guide [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing).

---

### Post by Pumalite on 2008-03-30
Here is another one:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by punkkid219 on 2008-03-30
Ok, I think Ive decided im going to wipe the Windows Partition then Partition it So Ill have two 20GB Partition Ill install Ubuntu then Windows

---

### Post by Pumalite on 2008-03-30
You have to install Windows first at the beginning of the drive. Ubuntu last.

---

### Post by punkkid219 on 2008-03-30
I have Windows installed I just have no Partitions with it but the drive isn't full

---

### Post by kastelo on 2008-04-02
and if i want to install windows whith ubuntu installed and don't loose any thing

---

### Post by Pumalite on 2008-04-02
Backup eveything before installing:
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by housam on 2008-04-02
> **punkkid219 said:**
> I have Windows installed I just have no Partitions with it but the drive isn't full

resize the partition which has windows to give ubuntu a room for installation .
using the partitioning tool in the live cd can resize this windows partition to leave an unallocated space which can be used to create two partitions for ubuntu.( one for the root ext3 format with mount point (/) and the other for the swap ( 1GB is ok ) )
before doing anything, defrag windows partition 2-3 times and backup your data.

---

### Post by Joeb454 on 2008-04-02
I think the OP might want to look into Wubi?

It allows you to install Ubuntu as you would any other Windows app :)

---

