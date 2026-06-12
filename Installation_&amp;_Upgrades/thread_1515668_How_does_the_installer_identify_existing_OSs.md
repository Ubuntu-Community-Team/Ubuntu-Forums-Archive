---
title: "How does the installer identify existing OSs?"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by Elusive Pete on 2010-06-22
During the Ubuntu installation, what does it use to identify which disk  has an operating system already on it?

The reason I ask is  because I accidentally wiped my Windows 7 hard disk today. I had been  attempting to install Ubuntu 10.04 on my other (empty) hard disk, and I  selected the disk which the installer said didn't have an OS already on  it. Turns out I didn't choose wisely. :(

I *think* the  problem was that my Windows installation was on disk0 (sda) and the  Windows bootloader had inexplicably been put on disk1 (sdb). I didn't  previously know this... I just bought the PC this way, having given  instructions to the shop that I wanted one disk for Windows, and one  left spare. It's only after picking through the sadly unbootable  wreckage that the fact revealed itself.

Would Ubuntu have used  the location of the bootloader to identify the location of an existing  OS? If so, that might explain why I selected the wrong disk to wipe!  Either way, I'll know to examine my partitions more carefully in future.


(In  case it's relevant, my PC originally came with WinVista, but I upgraded  to Win7 last year.)

---

### Post by darkod on 2010-06-22
Unfortunately for you, you got it right (after the mistake). It can only search according to the boot files (loader). The actual system partition can be on another disk, although for windows it rarely is.

In step 4 the top colored bar is showing the current partitions and usually it should point you to the correct disk. Also, the drop menu under Erase and use whole disk, even when it's greyed out is showing the selected disk I think. And the size of the disk next to the linux name like /dev/sda. That should also help you figure out the disk which is currently selected, unless you have same size disks.

Did ubuntu install over windows? Did you boot and use ubuntu a lot after that?

If you didn't use the computer much there is big chance you can save the windows partition with testdisk. You can hardly make it worse anyway.

PS. If you want to try and save it, use the computer as little as possible, use the ubuntu cd to boot into live mode, Try Ubuntu option, and it will run from the cd. Don't boot from hdd.

---

### Post by Don Barzini on 2010-06-22
> **Elusive Pete said:**
> During the Ubuntu installation, what does it use to identify which disk  has an operating system already on it?

The reason I ask is  because I accidentally wiped my Windows 7 hard disk today. I had been  attempting to install Ubuntu 10.04 on my other (empty) hard disk, and I  selected the disk which the installer said didn't have an OS already on  it. Turns out I didn't choose wisely. :(

I *think* the  problem was that my Windows installation was on disk0 (sda) and the  Windows bootloader had inexplicably been put on disk1 (sdb). I didn't  previously know this... I just bought the PC this way, having given  instructions to the shop that I wanted one disk for Windows, and one  left spare. It's only after picking through the sadly unbootable  wreckage that the fact revealed itself.

Would Ubuntu have used  the location of the bootloader to identify the location of an existing  OS? If so, that might explain why I selected the wrong disk to wipe!  Either way, I'll know to examine my partitions more carefully in future.


(In  case it's relevant, my PC originally came with WinVista, but I upgraded  to Win7 last year.)

When you install Ubuntu it always best to use **Manual** partitioning. That way it doesn't do anything you don't tell it to do.

When you re-install.... install Windows first.

When installing numerous operating systems where one is going to be Windows, it is always best to install Windows first.

---

### Post by Elusive Pete on 2010-06-22
Thanks for the replies. As it happens, I actually did use manual  partitioning, but I was obviously telling it to do the wrong thing!
 
 Thankfully I didn't boot into Ubuntu at all after this went down. I had  installed it without GRUB, intending to boot into Windows and edit the  Windows boot loader afterwards. Of course, given that Ubuntu ended up  writing over Windows, I couldn't boot at all. A blessing in disguise!
 
 I've since installed Win7 afresh on disk1 -- my formerly empty disk --  so I'm at least up and running again. A quick scan shows lots of  recoverable data on disk0, which is good. (3 million cheers for backups  of critical data though!)

---

### Post by darkod on 2010-06-22
You can't boot ubuntu from windows without grub. If you planned to use EasyBCD or similar, it only helps you to create entry for ubuntu in windows bootloader but that entry just calls grub to continue the boot process.

With two disks and planning to have windows on one and ubuntu on the other, it's best to put grub2 on the MBR of the ubuntu disk. Everything else is a hassle because windows doesn't support booting it by default.

You can still keep windows MBR on the windows disk and in emergency boot into windows if grub2/ubuntu fails.

---

### Post by Elusive Pete on 2010-06-22
> **darkod said:**
> You can't boot ubuntu from windows without grub

Ah, good to know. Thanks.

I've been reading a few articles which recommend exactly what you're suggesting, so I'll definitely do that next time!

---

