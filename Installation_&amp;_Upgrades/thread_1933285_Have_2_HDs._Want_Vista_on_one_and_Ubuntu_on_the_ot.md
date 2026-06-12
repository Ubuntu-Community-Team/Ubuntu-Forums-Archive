---
title: "Have 2 HDs. Want Vista on one and Ubuntu on the other."
date: 2012-02-29
forum: Installation &amp; Upgrades
---

### Post by mdubs on 2012-02-29
I have 2 HDs in my computer. One is the 500GB that came with the new PC and the other is a 160GB that I salvaged from my previous PC.

These are both SATA drives and are both currently hooked up to the motherboard.

What I want to do is install Ubuntu on the 160GB drive and leave Vista completely alone. I don't even want it to ask which OS to boot to when I start the PC. My wife isn't tech savvy in the least and freaked when I brought up the idea of a dual boot system. I'm fine going through the boot options on start up to select the second drive to boot from.

Now, I have not found a way to do this that I fully understand. If I try the installer from the bootable USB that I have, it wants to install the OS to the 160GB drive but the bootloader to the 500GB drive. This isn't what I want.

I don't know if I can go through the "something else" menu to accomplish my goal... If so, a short primer with partition sizes and all would be appreciated.

Otherwise, my more brute force method would be to remove the 500GB drive and then go through the install process with only the 160GB drive visible to the installer. Then I would reconnect the main drive and alter the boot order to look at the main drive first, thus booting to Vista unless otherwise interrupted. Will this idea work?

I really appreciate any help.

---

### Post by darkod on 2012-02-29
You have few options, and you already stated them.

1. In this case, disconnecting the vista disk during the ubuntu install sounds easier. Unless you want a setup with specific partition sizes or separate /home partition (which helps you with future clean installs). If you do want this, go with Something Else.

2. Something Else. As minimum ubuntu works with two partitions, root and swap. Having a separate /home partition is helpful, but is entirely optional. The partition planning would go like:
root partition, 10-15GB, primary, ext4, mount point /
/home partition, size depends, primary, ext4, mount point /home
swap partition, 2GB or 1.5 x RAM if you plan to hibernate, logical, doesn't use mount point

The above calculation depends:
The swap size whether you plan to hibernate or not, if not about 2GB is enough. Otherwise usually you would want 1.5 x RAM size.
The /home partition size depends on swap size and root size, basically whole of the disk - root - swap.

In the Something Else option there is drop down box under the partition list where you can select where to install the bootloader. So even with both disks plugged in, you can select where to install grub2 without any problem.

---

### Post by Mark Phelps on 2012-02-29
Strongly support the approach that darkod recommends -- in disconnecting the other drive while installing Ubuntu.  That will prevent any "accidental" overwriting of anything on your Vista drive.

When you install Ubuntu to its own drive, it will install GRUB there as well.  But when you reconnect the Windows drive, you will have to use the BIOS to select which OS, because GRUB will not have an entry for Windows.

Have you considered that you can configure GRUB as follows:
1) Have the default selection being Windows
2) NOT show a menu when booting.

That accomplishes what you want (Windows by default) but still leaves you the option of holding down the SHIFT key when you boot and selecting Ubuntu when the GRUB menu displays.

---

### Post by mdubs on 2012-02-29
Awesome. Thanks to both of you for the help.

I think I will just unplug the main drive for the installation. That sounds like it is the safest way to get to the end goal.

Mark, I didn't know that I could set grub up that way. I think I'll leave it for now so that the wife really just has no clue what is going on. I have the option of pressing F12 while the system is starting up and that lets me choose the boot device. 

Thanks again for your help gentlemen!

---

