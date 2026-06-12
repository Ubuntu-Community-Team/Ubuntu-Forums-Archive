---
title: "Triple Booting With Grub?"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by chazdg24 on 2012-02-13
I have Windows 7 and Ubuntu 11.10 installed.  If I wanted to install Windows 8 and triple boot with Grub running the show, how difficult would it be?  Installing another OS is the easy part.  It's the configuring Grub I am clueless about.

Any thoughts (and directions!) would be appreciated.

---

### Post by darkod on 2012-02-13
With the new grub2 there is no configuring. At lease for basic use.

But what you should know, is:
1. When installing more than one version of windows, it combines the boot files. So the win8 boot files will be added to win7 boot files. If you delete the win7 partition (or the System Reserved if it exists), you can't boot win8 either.
2. Installing windows will write windows bootloader on the MBR. You will need to boot with the ubuntu cd in live mode (have it at hand), and reinstall grub2 to the MBR. Then you will need to boot ubuntu and run:
sudo update-grub

That's it. But in this case it will not be a true triple boot in the grub menu. Because windows boot files will be combined, you will need to select win7 as now, and then windows bootloader will show up offering choice for win7 and win8.

You could avoid the above, with a procedure like:
1. Prepare the win8 ntfs partition from ubuntu. Format it as ntfs and use Gparted to set the boot flag on it.
2. Windows puts the boot files where the boot flag is, that way it will not combine them with win7. Install your win8.
3. Restore grub2 to the MBR, boot ubuntu and run the update-grub. You should have all three OSs listed in the grub menu this way.

---

### Post by oldfred on 2012-02-13
+1 on Darko's suggestions.

One addition. All bootable Windows installs have to be in primary partitions, that is part of the reason it moves a second installs boot files to the first install, as then the second can be a logical, but then never bootable on its own. (There is a work around to boot XP in a logical but not Vista/7)

---

### Post by chazdg24 on 2012-02-13
> **darkod said:**
> With the new grub2 there is no configuring. At lease for basic use.

But what you should know, is:
1. When installing more than one version of windows, it combines the boot files. So the win8 boot files will be added to win7 boot files. If you delete the win7 partition (or the System Reserved if it exists), you can't boot win8 either.
2. Installing windows will write windows bootloader on the MBR. You will need to boot with the ubuntu cd in live mode (have it at hand), and reinstall grub2 to the MBR. Then you will need to boot ubuntu and run:
sudo update-grub

That's it. But in this case it will not be a true triple boot in the grub menu. Because windows boot files will be combined, you will need to select win7 as now, and then windows bootloader will show up offering choice for win7 and win8.

You could avoid the above, with a procedure like:
1. Prepare the win8 ntfs partition from ubuntu. Format it as ntfs and use Gparted to set the boot flag on it.
2. Windows puts the boot files where the boot flag is, that way it will not combine them with win7. Install your win8.
3. Restore grub2 to the MBR, boot ubuntu and run the update-grub. You should have all three OSs listed in the grub menu this way.

Can you explain the 'boot flag' concept and how to go about it correctly.  I never heard of it before.

So if I install Windows 8 and reboot with my Ubuntu install disk and run "grub-update" in terminal, I won't get Grub to pick up all three OS's?

---

### Post by darkod on 2012-02-13
The boot flag is used in windows boot process and it simply serves as guidance to the bootloader where to continue the boot process, on which partition.
That's why only one partition can have the boot flag.

In Gparted you can manage flags (including boot), with right-click on a partition, and selecting Manage Flags.

No, if you simply install win8 update-grub will not add win8 to the boot menu. That has nothing to do with grub. It will add to the menu all OSs it can find (their boot files it can find). But because windows combines boot files for more than one version, it's not up to grub.
The only way to have the three OSs in the boot menu is for win8 boot files to go to its own partition, by moving the boot flag to it before you start the win8 install.

---

### Post by oldfred on 2012-02-13
Lots of detail on how Windows multiboots. You can just review pictures for a quick review.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by chazdg24 on 2012-03-01
I meticulously followed the instructions above using gparted and the flag for the Windows 8 partition.  Unfortunately, it does not work as once you try to install Grub as documented above, I get an error message saying that Ubuntu does not exist, is it mounted?  I mount it, but I still get the same error message when I try to to get Grub up and running.

Not solved.

---

### Post by darkod on 2012-03-01
What commands are you using to mount it and reinstall grub2?

Post the results of:
sudo fdisk -l (small L)

---

### Post by chazdg24 on 2012-03-01
I'll pass, thanks anyway.  I thought Gnome-shell was a travesty with the flickering due to the ATI driver issues.  Windows 8 is right up there as bizarre. At least the ATI driver works.

I am taking a break from Ubuntu and Mint as they really are not worth the effort.  Ubuntu has Unity...

Mint 12 has Gnome-shell...Cinnamon shows promise but is finicky.  Until the ATI drivers are sorted out, I won't bother - I think.  :)

Maybe I will change my mind in a few days.  Thanks for the help.

---

