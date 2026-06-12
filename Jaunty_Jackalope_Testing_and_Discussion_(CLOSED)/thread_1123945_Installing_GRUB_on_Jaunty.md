---
title: "Installing GRUB on Jaunty"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tiagobt on 2009-04-12
I have a second generation MacBook and I'm trying to install Kubuntu Jaunty. In the previous versions, I'd go to the advanced installation options and choose to install GRUB on the partition where Linux is installed. In Jaunty, however, I can't choose the partition I want. The combo box provides a single option: installing GRUB on /dev/sda (the MBR). Is there a workaround for this issue?

Thanks,
Tiago

**Edit:** I've formatted the Linux partition as ext3 (not ext4).

**Edit 2:** I'm using Kubuntu Jaunty Beta.

---

### Post by tiagobt on 2009-04-12
Apparently, this is a known issue:
[http://kubuntuforums.net/forums/index.php?topic=3102394.0](http://kubuntuforums.net/forums/index.php?topic=3102394.0)

I'm just not sure this is Kubuntu-specific. I think the only option is choosing not to install the boot manager and installing GRUB later on using the live CD. Any other ideas?

---

### Post by tiagobt on 2009-04-12
If I choose not to install GRUB from the installer, the files /boot/grub/stage1 and /grub/stage1 are not even generated, so I'm not able to reinstall GRUB from the live CD.

I tried running the command **setup (hd0,2)** from the GRUB terminal, but it complained about the missing files I mentioned. I tried running the command **sudo grub-install '(hd0,2)'** from a regular console, but I got an error message saying that it could not find a device for /boot.

Anything else I can try?

---

### Post by pxwpxw on 2009-04-12
> **tiagobt said:**
> If I choose not to install GRUB from the installer, the files /boot/grub/stage1 and /grub/stage1 are not even generated, so I'm not able to reinstall GRUB from the live CD.

I tried running the command **setup (hd0,2)** from the GRUB terminal, but it complained about the missing files I mentioned. I tried running the command **sudo grub-install '(hd0,2)'** from a regular console, but I got an error message saying that it could not find a device for /boot.

Anything else I can try?

Use the jaunty alternate install CD, and choose Debconf priority low (expert mode). The stage install grub first installs grub files to the ubuntu OS, and after that it allows choice of target MBR or other partiton BS or none.

---

### Post by tiagobt on 2009-04-12
> **pxwpxw said:**
> Use the jaunty alternate install CD, and choose Debconf priority low (expert mode). The stage install grub first installs grub files to the ubuntu OS, and after that it allows choice of target MBR or other partiton BS or none.

OK, I'll give it a try. Thanks.

I'm just curious: is this the expected behavior in the Jaunty installer? What's the point on having a combo box with a single option? Should I report a bug in launchpad?

---

### Post by cyberdork33 on 2009-04-13
> **tiagobt said:**
> OK, I'll give it a try. Thanks.

I'm just curious: is this the expected behavior in the Jaunty installer? What's the point on having a combo box with a single option? Should I report a bug in launchpad?
I think this is a bug with the kubuntu version. I can choose the partition I want in Ubuntu proper.

However, as long as you are not also trying to install Windows, it should not matter that it is in the MBR... 

NOTE: Jaunty Final should also finally have the long-standing MBR Partition Table Bug fixed ([https://bugs.edge.launchpad.net/mactel-support/+bug/222126/](https://bugs.edge.launchpad.net/mactel-support/+bug/222126/))

---

### Post by tiagobt on 2009-04-14
> **cyberdork33 said:**
> I think this is a bug with the kubuntu version. I can choose the partition I want in Ubuntu proper.

However, as long as you are not also trying to install Windows, it should not matter that it is in the MBR... 

NOTE: Jaunty Final should also finally have the long-standing MBR Partition Table Bug fixed ([https://bugs.edge.launchpad.net/mactel-support/+bug/222126/](https://bugs.edge.launchpad.net/mactel-support/+bug/222126/))

I see. But I'm using Windows as well, so my only option is intalling GRUB to the Linux partition, right? By the way, is the "long-standing MBR partition table bug" related to the issue I'm having? Will it be easier to install Ubuntu and Windows after this bug is fixed?

---

### Post by cyberdork33 on 2009-04-14
> **tiagobt said:**
> I see. But I'm using Windows as well, so my only option is intalling GRUB to the Linux partition, right?
Not only, but best. If you install GRUB to the MBR over the Windows loader, then you have to use GRUB to start Windows. (If you install it to the partition, you will be able to boot Windows or GRUB from rEFIt).

> **tiagobt said:**
> By the way, is the "long-standing MBR partition table bug" related to the issue I'm having?
I don't think it would prevent GRUB from installing. It just messes up the partition tables when you do an install leaving the Mac unbootable (until you sync the tables up again).

> **tiagobt said:**
> Will it be easier to install Ubuntu and Windows after this bug is fixed?yes, but I wouldn't wait for it. It isn't that serious, and I think you will still have this issue even if it was fixed.

---

