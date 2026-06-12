---
title: "is there a way to work with multiple MBRs ?"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by zero7404 on 2008-10-16
i have windows vista installed on my internal hdd's (raid 0), and also have ubuntu 8.10 installed on an external usb hdd. i installed ubuntu by physically disconnecting my internal hdd's and only using the external hdd for installation.

so now i have 2 sets of drives: a raid 0 array that's got it's own mbr for windows, and an external drive that's got it's own mbr for ubuntu.

the way i control which OS i boot to is by powering down and connecting/disconnecting the device, as i have my bios set to boot from USB first and raid0 second.

is there a way i can either modify GRUB or windows bootloader to allow one bootloader to point to another ? so that i can choose to boot to whichever OS i want without fiddling with the USB cable ?

this would be really convenient...

---

### Post by cariboo on 2008-10-16
Have a look here:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

and scroll down to Installing on external or RAID hard disks

Jim

---

### Post by zero7404 on 2008-10-16
that's really helpful, thanks ! 
now, since windows is on a raid array, would i need to enable dmraid before i make changes to grub ?

---

### Post by zero7404 on 2008-10-16
i followed the steps outlined in this section [https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)

but this procedure is not working right. the raid 0 array consists of 2 sata drives, i installed dmraid and gparted showed me the array as follows:

/dev/mapper/isw_ecfcjijjgh_RAID0 (this is the entire raid array)
/dev/mapper/isw_ecfcjijjgh_RAID01 (this is the windows partition)

what i am not sure about is what the designator hd1 means in the grub entry for Windows (as per above tutorial). it says in the tutorial that i should replace hd1 with sd1 if this is a second SATA drive on which windows is installed. i did this and i get error 23 when i try to select windows from the grub boot menu.

how would i determine what each raid disk is designated as (sd0, sd1, sda, etc) ?

EDIT:

nevermind, i went back into menu.lst and changed back replaced the windows entry as it is shown in the tutorial (hd1 wherever hd1 is shown) and now i can dual boot with grub when the external hdd is connected ! fantastic...

---

