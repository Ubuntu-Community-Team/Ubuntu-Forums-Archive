---
title: "Dualboot Ubuntu and XP SP3 on two hard drives"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by fafm01 on 2008-08-30
I'm sure this has probably been posted somewhere so sorry for being redundant, but I have two hard drives and the first has WinXP and I want to put Ubuntu on the second.  The first time I tried installing it without messing around with any settings other than telling it to use my second hard drive, it gave me an error about Grub not being able to be installed and all that happens when I boot is it just goes into Windows as normal.  So then I tried changing something to try to make it load Grub onto the second hard drive and it looked like it worked at first but it still wouldn't boot into Ubuntu.  And I can't edit the menu.lst file while running the live CD because it says I don't have permission.  Is there something I'm missing?

Also, another less important question is why does Ubuntu not let me uninstall when I try to install it directly into Windows like with Wubi?

---

### Post by caljohnsmith on 2008-08-30
Can you switch your BIOS so the Ubuntu HDD is first in the boot order, instead of the Windows HDD? Because if you can boot the Ubuntu HDD first, just install Grub to the master boot record (MBR) of that HDD. Before you do the installation, do the following:
```
sudo fdisk -lu
```
Note which is your Ubuntu HDD; it should probably be /dev/sdb. Now when you go through the Ubuntu installer, when it gets to the final installation stage, if you click the "advanced" button you can specify which HDD to install Grub to. Put in there /dev/sdb (or whichever HDD it should be), instead of the default (hd0) that Grub normally uses. That way Grub gets installed to the MBR of the Ubuntu HDD, and all you have to do is make the Ubuntu HDD first in the BIOS boot order in order to boot it.

---

### Post by fafm01 on 2008-08-30
How do I install Grub to the MBR?  And where do I "sudo fdisk -lu"?  Do I load Ubuntu off of the LiveCD and use the terminal for that?  Would I have to keep the Ubuntu HDD first even after getting it installed?

I did try installing to /dev/sdb the second time when it finished the install but still didn't boot into Ubuntu or even give me the option to choose what to boot.  Thanks though, I'll try switching the boot order.

---

### Post by fafm01 on 2008-08-31
Switching the drive order didn't work but it did get me a Grub screen.  It just gave me an error message no matter what OS I tried to load from Grub.

---

### Post by confused57 on 2008-08-31
> **fafm01 said:**
> Switching the drive order didn't work but it did get me a Grub screen.  It just gave me an error message no matter what OS I tried to load from Grub.
You can try highlighting the first Ubuntu entry in your grub boot menu, press "e", highlight the line with root, press "e" again, then change root from (hdx,y) to (hd0,y), press "enter", then "b" to boot....root will show something like (hd1,0), so change it to (hd0,0).  Check back if this works, it's temporary, and you'll need to make a few other edits.

---

