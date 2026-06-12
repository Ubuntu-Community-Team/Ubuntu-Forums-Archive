---
title: "Dual booting on 2 different drives.."
date: 2011-04-19
forum: Installation &amp; Upgrades
---

### Post by kskwerl on 2011-04-19
Hey everyone, lets say that i have 2 60GB SSD. I they are both blank. How would you go about installing Windows 7 and Ubuntu. I would like to keep them on separate disks. Which would I install first? Is there anything special I have to do?

Also, if I was going to install them together on 1 60GB SSD which would I install first/special instructions/etc?:popcorn:

Thank you.

---

### Post by Mark Phelps on 2011-04-19
I don't have SSDs but I've done this similar thing several times -- this is what I recommend:

1) Install each OS to its own drive.  Have only that drive in the PC during the installation and setup.  This prevents accidental overwrite or corruption of the "other" OS.
2) Connect both drives but configure PC to boot from the Ubuntu drive.
3) Once inside Ubuntu, open a terminal and enter "sudo update-grub".  This will generate a new GRUB menu and include an entry (or two) for Windows 7.

Note: Clean installs of Windows 7 on empty drives result in two default partitions: boot and OS.  The OS_Prober in GRUB sometimes thinks these are BOTH Windows 7 OSs and creates two menu entries as a result.

If this happens, it is generally best to select the first Windows 7 entry in the boot menu.

---

### Post by kskwerl on 2011-04-19
> **Mark Phelps said:**
> I don't have SSDs but I've done this similar thing several times -- this is what I recommend:

1) Install each OS to its own drive.  Have only that drive in the PC during the installation and setup.  This prevents accidental overwrite or corruption of the "other" OS.
2) Connect both drives but configure PC to boot from the Ubuntu drive.
3) Once inside Ubuntu, open a terminal and enter "sudo update-grub".  This will generate a new GRUB menu and include an entry (or two) for Windows 7.

Note: Clean installs of Windows 7 on empty drives result in two default partitions: boot and OS.  The OS_Prober in GRUB sometimes thinks these are BOTH Windows 7 OSs and creates two menu entries as a result.

If this happens, it is generally best to select the first Windows 7 entry in the boot menu.

Thank you for the reply. So it doesn't matter whether I install Win 7 or Ubuntu first? Just that I should only have the drive that I'm using plugged in for that particular installation?

Example.

1. 60GB SSD ***x*** (plugged in)
2. Unplug other 60GB SSD ***y***
3. Install Win 7 to 60GB SSD ***x***
4. Shut down computer
5. Unplug 60GB SSD ***x***
6. Plug in 60GB SSD ***y***
7. Install Ubuntu to 60GB SSD ***y***
8. Shut down computer
9. Plug in 60GB SSD ***x***
10. Power on, boot into Ubuntu and update grub?

---

### Post by oldfred on 2011-04-19
Yes but drive order can be important and you have a 50% chance.

Windows will install and think it is the first drive - drive 0. 

Ubuntu will install and think it is the first drive hd0 or sda.

Ubuntu boots from UUIDs so drive number is not critical. Windows will get confused it it is not drive 0. 

So plug the windows drive in so BIOS sees it as the first drive. If both SSDs are identical they will not have a lot of difference in BIOS. My two identical 160GB hard drives took me a while to understand. I was just changing boot order in BIOS intially.

---

### Post by kskwerl on 2011-04-19
> **oldfred said:**
> Yes but drive order can be important and you have a 50% chance.

Windows will install and think it is the first drive - drive 0. 

Ubuntu will install and think it is the first drive hd0 or sda.

Ubuntu boots from UUIDs so drive number is not critical. Windows will get confused it it is not drive 0. 

So plug the windows drive in so BIOS sees it as the first drive. If both SSDs are identical they will not have a lot of difference in BIOS. My two identical 160GB hard drives took me a while to understand. I was just changing boot order in BIOS intially.

Nice nice, thanks again for all your help! :D

---

