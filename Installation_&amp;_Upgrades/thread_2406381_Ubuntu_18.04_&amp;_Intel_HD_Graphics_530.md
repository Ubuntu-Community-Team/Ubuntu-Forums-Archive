---
title: "Ubuntu 18.04 &amp; Intel HD Graphics 530"
date: 2018-11-20
forum: Installation &amp; Upgrades
---

### Post by masterprogrammer on 2018-11-20
Hi,
I have a AiO (HP ProOne 400 G2 20-inch Touch All-in-One PC): Graphics: "Intel HD Graphics 530".
[COLOR=#242729][FONT=Arial]I can install Ubuntu just with nomodeset mode. So now I have low resolution. In this case what to do I do? I install **Ubuntu 18.04**.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]"About" details: Graphics llvmpipe (LLVM 6.0, 256 bits). I also checked "Additional Drivers" which indicated, No additional drivers are available. No proprietary drivers are in use.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The output for "[/FONT][/COLOR][COLOR=#242729][FONT=Arial]sudo lshw | grep -A9 VGA"[/FONT][/COLOR][COLOR=#242729][FONT=Arial] is the following:
[/FONT][/COLOR]
description: VGA compatible controller
product: HD Graphics 530
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 06
width: 64 bits
clock: 33MHz
capabilities: pciexpress msi pm vga_controller bus_master cap_list
configuration: latency=0

---

### Post by oldfred on 2018-11-20
Do not think it is the Intel graphics that is the issue.
I have a Gigabyte motherboard, but same Intel video and it just works. I do not even use nomodeset to boot.

Have you updated UEFI from HP for your model?
Did you install in UEFI boot mode or BIOS boot?

If you do not use nomodeset what happens?

---

### Post by masterprogrammer on 2018-11-20
Hi,
Thanks for your reply.
> **oldfred said:**
> 
Have you updated UEFI from HP for your model?
No. I do not know. Please guide me.

> **oldfred said:**
> 
Did you install in UEFI boot mode or BIOS boot?
When I tried install Ubuntu, I selected "Legacy - hp PLDS DVDRW DU8AESH" in boot menu.

> **oldfred said:**
> 
If you do not use nomodeset what happens?
[FONT=Arial][COLOR=#242729]When I boot Ubuntu, it boots to a colorful screen and just change color of screen (red, green, blue).[/COLOR][/FONT]

[FONT=Arial][COLOR=#242729]Complete description of my install:
[/COLOR][/FONT]If I select "UEFI - hp PLDS DVDRW DU8AESH" in boot menu and then "install ubuntu" I see just colorful screen ([COLOR=#242729][FONT=Arial]red, green, blue[/FONT][/COLOR]).
If I select "Legacy - hp PLDS DVDRW DU8AESH" in boot menu and then:
1 - Press "F8"
2 - Press "F6"
3 - Select "nomodeset"
4 - Install Ubuntu.
5 - Every thing is OK but I have not good resolution.

---

### Post by oldfred on 2018-11-20
I would update UEFI first.

Some HP have needed acpi=off      instead of nomodeset as boot parameter.

---

### Post by masterprogrammer on 2018-11-21
> **oldfred said:**
> I would update UEFI first.
How? Please guide me.

> **oldfred said:**
> 
Some HP have needed acpi=off instead of nomodeset as boot parameter.
I tried it but I have same problem(colorful screen).

---

### Post by oldfred on 2018-11-21
You have to go to the HP site and support for your model system.
Usually under drivers or something similar are downloads. The drivers will all be for Windows but the BIOS/UEFI will be for your system.
You go into your UEFI and check version and see if most recent version is newer.
They usually also have instructions on how to update UEFI.

My motherboard has 3 ways to update. From within Windows, from a bootable FAT32 flash drive, and from within UEFI reading a FAT32 folder somewhere on system (I use my ESP).

Linux has started to have available updates from within Linux (similar to Windows, only a few brands so far. HP shows only model being tested for now.
       [https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

Someone with an HP just posted this in an older thread. Yours may be similar process.
[https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu](https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu)

---

