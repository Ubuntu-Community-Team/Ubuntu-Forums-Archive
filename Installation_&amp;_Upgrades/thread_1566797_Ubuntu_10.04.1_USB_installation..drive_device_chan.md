---
title: "Ubuntu 10.04.1 USB installation..drive device changes after install."
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by johnson094 on 2010-09-02
I have loaded the Ubuntu 10.04.1 Live CD onto my HP p386i desktop. It loads easily and responds well in the "Try It" mode. I purchased a 16 gb USB Flash drive and did an install from the Live CD. After booting the CD ROM to the window where given a choice to "try" or "install", I inserted my flash drive into the USB port and selected "install". I had my 2 hard drives disconnected. 
 
At install point #4 I selected my USB drive and also selected manual partition . The partition displayed as follows:
 
Partition: /dev/sdf
/dev/sdf1 Type: EXT2 Mount at "/" Size=15,300mg Used=33
/dev/sdf2 Type: Swap Size= 718mg Used= 0
 
The flash drive I had was formatted as a FAT 32 but when I tried to continue on to install point #7, I got an error instructing me to change the partition type and suggested "EXT2" which I did.
 
At install point #7 I selected "Advanced" and chose to install GRUB to MRB into the flash drive.
 
Everything seemed to install ok. 
 
I removed the Live CD. Reconnected my hard drives, made sure CMOS boot preference was set to the USB drive, and rebooted. I got an error that "/dev/sdf" not found.
 
I replaced the Live CD, rebooted to the "Try It" copy and opened System-Administrator-Gpart. Looking at the partition manual for my flash drive, it showed:
 
/dev/sdg
/dev/sdg1 Ext2 15,000mb 
/dev/sdg2 Swap 718mb 
 
I am a real noobie (1 week) and haven't a clue what is happening. Could someone shed some light? Let me know if more info is needed.
 
Thanks in advance.

---

### Post by oldfred on 2010-09-03
Because you have plugged in the other hard drives the drive letter of the flash drive has changed.

On my system the letter is not important but the number that grub sees. Grub is supposed to use the UUID if the drive number is not correct. I installed from a flash drive to a flash drive. When I rebooted I removed the install drive and grub would not boot the flash drive as not found. The wrong number and it seemed the gap in numbers caused it to stop looking for the correct UUID.

Many systems require you to choose a hard drive to boot not a USB device with flash drives. My system has USB-HDD as a choice but flash drives appear under the hard drives not USB devices.

I had to use e to edit grub menu on first boot and change hd6 to hd5 to get my system to boot.

---

### Post by johnson094 on 2010-09-03
I believe in my CMOS under boot preference I had the HD, 16 gb USB drive, and Flash card reader.  I placed the USB at the top of the list .  It would run..CD ROM, USB, HD, then Flash Card reader.  I will take a look at that Grub menu.  If I format my USB drive, default is Fat 32, but I can format it to read like HD.  Would this help the situation?
 
Thanks for your reply.

---

### Post by oldfred on 2010-09-03
Grub2 boots from just about anything. Do you get a grub menu? If so you may have to use e to edit and adjust the (hd3,1) or whatever drive number it has so it sees the drive as the correct number. I had to change mine the first time to get it to work. But I knew mine worked as when used on my portable with only one drive it must have used the UUID as it worked without editing.


I have FAT32 for my 4GB flash to boot ISOs but my standard install in a 16GB flash is ext2. I also used FAT32 to create a windows recovery drive and then installed grub2 to boot the windows recovery.

---

