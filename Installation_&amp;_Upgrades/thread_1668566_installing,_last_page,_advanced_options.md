---
title: "installing, last page, advanced options"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by pjmlmas on 2011-01-16
I already have Ubuntu 10.041 and windows xp installed as dual-boot.
I am installing another version of Ubuntu in a logical partition.

On the last page of the live install guide, there are advanced options.
There is a check box next to install boot loader.
I already have boot loader from previous Ubuntu installation, correct?
What were to happen if I un-check this box?

The reason I ask is there were grub updates from previous Ubuntu install. I am wary of leaving this checkbox set, especially if not needed.

---

### Post by Quackers on 2011-01-16
What version are you installing?
In 10.04 you can untick that box and the bootloader will not install, if memory serves me right!
Then if you reboot you should get to the older Ubuntu, where you can run ```
sudo update-grub
``` which should pick up your new installation and add it to the grub menu.
Maybe somebody else could confirm this?

---

### Post by ajgreeny on 2011-01-16
I don't think you can stop grub being installed completely, as Quackers is suggesting, but if you wish to continue with the current grub, you can either put grub on a different disk from the old version, if you have two or more disks, or you can choose to put it on the new ubuntu root partition.  Grub on a root partition is not normally recommended, but is not a problem if you have only one disk and use grub from another installed OS.

Having done that ```
sudo update-grub
``` in your old OS will pick up the new one, as Quackers suggests, and allow you to boot that from the old grub.

---

### Post by Quackers on 2011-01-16
I thought installers prior to 10.10 allowed the user to choose not to install grub. I know that 10.10 doesn't allow that, but I'm sure I remember such an option in 10.04 :-)

---

### Post by ajgreeny on 2011-01-17
I must double check that again then, but I don't remember seeing any option to not install grub, just every partition and each disk.  If I'm wrong, I apologise.

---

### Post by Frogs Hair on 2011-01-17
The install grub checkbox appeared on the screen during Wubi installations of 10.04. I was helping a friend with Wubi and I remember not checking the option.

---

### Post by pjmlmas on 2011-01-17
i checked 10.10. It only gives option on where to install bootloader (sdaXX)

Just info about bootloader install...this means that when installing new instance of Ubuntu, the MBR will ALWAYS be overwritten, from my understanding of GRUB2?
MBR -> point to newest Ubuntu install's bootloader?

Worry, because I though about option of putting on Fedora/CentOS AND downgrading all Ubuntu installs to GRUB.

---

### Post by Quackers on 2011-01-17
In the 10.10 installer there is no option to not install a bootloader. It has been removed. I believe, though, that it is a valid option in versions 10.04 and before.
Grub2 will pick up other operating systems.

---

### Post by dino99 on 2011-01-17
*** the MBR will ALWAYS be overwritten, from my understanding of GRUB2? ***

this point is not very clear on grub2 side. Have had some issues that lets me thinking its not true. Anyway install grub2 again in the same place as first (might be /dev/sda, not sdax), then into a terminal:

sudo dpkg-reconfigure grub-pc

a dialog box will popup: deselect the checked box and validate. So now all the grub are removed. Run again the command above and check to install it on /dev/sda.

---

