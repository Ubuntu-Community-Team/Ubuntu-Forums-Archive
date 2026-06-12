---
title: "USB no longer recognized by bios after creating live disk"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by zedfrugnug on 2010-10-19
I was trying to install maverick from USB flash drive, and used the live disk creator in lucid.
Before creating the live disk, my bios would recognize the usb drive as a option to boot from. Now it doens't show anymore in the bootoptions.
Another computer would boot from the drive. Also tried another USB flash drive, (without first creating a live disk from it) and this one did show up in the bootoptions.

I formatted the drive, and tried again without result.
Also tried resetting the bios to default settings without result.

Apperently the live disk creator changed something on the drive, wich makes my bios not recognize it, and which isn't changed by formatting..


Does anyone have any ideas?

Thanks

---

### Post by lechien73 on 2010-10-19
If the USB disk boots ok on another computer, then I would suggest updating the BIOS on your motherboard. You can usually download BIOS updates from your motherboard's manufacturer, and then run a simple utility to flash it to the chip.

---

### Post by zedfrugnug on 2010-10-19
I did install ubuntu before on the same computer with the same USB disk.
Also because this USB disk and other disks do appear in the bootoptions before turning them into a live disk, something must have changed when doing this. Actually I also tried using another USB disk, which now doesn't boot either..

I thought it would be easier and less risky figuring out what this is, and changing it back, then flashing my bios.

The flash-utility that acer provides for my veriton 1000 is rather archaic, and difficult. I've already read a post of someone who borked his system with it.. 

Also tried looking in GParted If could find any difference between this disk, and others that stil boot. But no dice.

---

### Post by Mossey on 2010-10-19
Have you checked the Bios settings to see if USB support is still enabled. Most MB will default to disabled. Mount the drive - turn on  and boot to Bios - Go to advanced Bios features or similar then under Hard Disk boot priority the disk should be seen there if it doesn't recognize it there it won't boot from the USB until the drive is recognized.

---

### Post by zedfrugnug on 2010-10-19
When I insert another USB disk that has not been turned into a live disk the bios does recognize it. So I guess USB boot is still enabeled in the bios.

To clarify my problem:
In advanced settings in my bios under hard boot priority the USB disk does not show up as an option to boot from, but other USB disks do..

---

### Post by zuerston on 2010-10-19
I usually delete the (all) partitions and everything ,then reformat it when it is acting weird. I think I used gparted oe whatever,don't see it in 10.10 menu! just disk utility,don't know if that would work ,try I guess.

---

### Post by zedfrugnug on 2010-10-19
Tried reformatting with GParted, but does not work..:(

---

