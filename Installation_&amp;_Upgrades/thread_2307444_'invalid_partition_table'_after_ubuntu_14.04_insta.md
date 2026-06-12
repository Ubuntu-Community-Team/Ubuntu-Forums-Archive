---
title: "'invalid partition table' after ubuntu 14.04 installation"
date: 2015-12-25
forum: Installation &amp; Upgrades
---

### Post by Haotian_Yuan on 2015-12-25
Hey guys. I installed ubuntu14.04 with a USB storage device on dell T7910. 
When installing, i chose to format the hard driver to remove the windows system. But after i rebooted the computer after installation, it showed the word 'invalid partition table'. And i could not get into the ubuntu system.
Can anyone help me? Thanks very much.

---

### Post by MAFoElffen on 2015-12-25
So what was the computer that you installed to? Wondering if the sytstem is EFI or Legacy BIOS? What was the original version of Windows that it came installed with? 

Since this is a Fresh Install "Over" everything, this should be simple.m (And I will try to keep t that way for you.)

If this was an older PC, that originally came installed with Windows 7 or earlier, let's assume it is a Legacy BIOS and follow these instructions:

Boot from your LiveUSB > Use the try option > Select/Click the first Tile on the left side.

You will go to the Ubuntu Launcher, where there will be a search box at the top-center. > Click the mouse there. Type GParted. > Click on the GParted Icon.

After GParted statrts > if not on the disk you want to work with > Upper right is a select option box to select the correct disk.

Select Action > New partition Table > Action Apply > Select GPT or MBR (if !TB or Larger Disk, safe to use GPT) > Confirm.

Select the Upper left Tile again > In the Unity Launcher Search box, type install. > Select Install Ubuntu > Install again to the now blank disk. with the new partition table.

If newer, then we might be able to assume that it might be UEFI BIOS, in that case tell me and I will adapt the instructions for you...

---

