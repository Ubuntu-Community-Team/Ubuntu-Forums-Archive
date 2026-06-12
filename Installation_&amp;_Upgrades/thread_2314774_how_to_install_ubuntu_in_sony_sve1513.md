---
title: "how to install ubuntu in sony sve1513"
date: 2016-02-23
forum: Installation &amp; Upgrades
---

### Post by davidtuti2 on 2016-02-23
Hi,
I have windows 10 in my vaio sony sve1513. 
Long time that I don't install ubuntu.
Is possible to install with my windows 10 without problems, I mean only following the installer and create a partition ext4 and swap ?
thanks and sorry for my English!

---

### Post by Bucky Ball on 2016-02-23
It is, but you need to be aware of a few things. UEFI was not perhaps around last time you installed Ubuntu. Please confirm if you are intending to install in UEFI mode on a newer machine or BIOS mode (the way you would have done it five years ago) on a no UEFI motherboard machine.

This will make a difference to how you go about it.

(If [this is the machine]("https://docs.sony.com/release/SPECS/SVE1513KCXS_mksp.pdf") you have, that looks nice and not that old.)

---

### Post by davidtuti2 on 2016-02-24
> **Bucky Ball said:**
> It is, but you need to be aware of a few things. UEFI was not perhaps around last time you installed Ubuntu. Please confirm if you are intending to install in UEFI mode on a newer machine or BIOS mode (the way you would have done it five years ago) on a no UEFI motherboard machine.

This will make a difference to how you go about it.

(If [this is the machine]("https://docs.sony.com/release/SPECS/SVE1513KCXS_mksp.pdf") you have, that looks nice and not that old.)

Thanks, the BIOS is UEFI.
Should I do something new to can install it?
Thanks

---

### Post by Bucky Ball on 2016-02-24
You might want to have [a quick read of this]("https://help.ubuntu.com/community/UEFI#General_principles"), but basically;

- Make sure you are using a 64bit version of Ubuntu
- Boot into Win and make sure that hibernate/fastboot are off (or the hard drive will hibernate and not shutdown completely)
- It is different with different BIOSs, but follow that guide in the link for the BIOS and make sure you are booting the install media in UEFI prior to saving changes and exiting the BIOS
- Choose 'Something Else' when you get to the partitioning section and create / and /swap (and leave what's already there) in free space or assign mountpoints to partitions you created earlier

Note: Unlike in the instructions on the link, I recently installed after installing Win 8 and didn't create or do anything about the EFI partition. There was one in there from the Win install, I left it alone and Ubuntu 'automagically' used it. 

Let us know if you hit a brick wall and we'll see what we can do.

There are variations on all this you will find online and from other users here.

---

### Post by davidtuti2 on 2016-02-24
> **Bucky Ball said:**
> You might want to have [a quick read of this]("https://help.ubuntu.com/community/UEFI#General_principles"), but basically;

- Make sure you are using a 64bit version of Ubuntu
- Boot into Win and make sure that hibernate/fastboot are off (or the hard drive will hibernate and not shutdown completely)
- It is different with different BIOSs, but follow that guide in the link for the BIOS and make sure you are booting the install media in UEFI prior to saving changes and exiting the BIOS
- Choose 'Something Else' when you get to the partitioning section and create / and /swap (and leave what's already there) in free space or assign mountpoints to partitions you created earlier

Note: Unlike in the instructions on the link, I recently installed after installing Win 8 and didn't create or do anything about the EFI partition. There was one in there from the Win install, I left it alone and Ubuntu 'automagically' used it. 

Let us know if you hit a brick wall and we'll see what we can do.

There are variations on all this you will find online and from other users here.

Hi, I can't find fast boot in my bios, but I have windows 10 without hibernate.
I install ubuntu x64 with Rufus in my usb with option  GPT for Uefi.
Then I reboot my Sony Vaio with assist button and I select boot from usb and the computer have a bootloop .
Could you help me please?
Thanks

---

