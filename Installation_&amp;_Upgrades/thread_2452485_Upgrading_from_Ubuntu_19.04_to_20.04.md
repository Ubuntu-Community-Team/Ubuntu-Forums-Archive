---
title: "Upgrading from Ubuntu 19.04 to 20.04"
date: 2020-10-23
forum: Installation &amp; Upgrades
---

### Post by joedirt6699 on 2020-10-23
hey all. I tried to update ubuntu 20.04 and when it rebooted I think something in grub broke and now it won’t boot. ive installed ubuntu live off a usb and installed boot repair. I did the recommended repair but this didn’t work

[https://paste.ubuntu.com/p/dcv3sqmMrN/](https://paste.ubuntu.com/p/dcv3sqmMrN/)

when I reboot I get the same
"error: symbol ‘grub_file_filters’ not found
entering rescue mode…
grub rescue>

please help.

---

### Post by tea for one on 2020-10-23
There is no direct upgrade path from 19.04 to 20.04.

Your Windows OS is hibernating (lines 34 - 36 in the report).

Suggestion:-

Disable, de-activate or remove device sda from your PC.

Can you boot into Windows, disable Fast Start Up and power off?

Then, post back here when your Windows OS is OK.

---

### Post by garvinrick4 on 2020-10-23
Ask oldfred is a bit of a mess he can give you best advice. 
[URL="https://ubuntuforums.org/member.php?u=852711"]oldfred

[/URL]

---

### Post by oldfred on 2020-10-23
Tea for one has reviewed Boot-Repair's report and is correct on first turning off Windows fast start up.
I am not as knowledgeable on LVM. If encrypted you have to manually mount before running Boot-Repair.
And Best with two drives to not run Boot-Repair's autofix. You want to keep Windows boot loader in MBR of Windows drive.
You often need to be able to directly boot Windows.
If Boot-Repair does not offer in Advanced mode to install syslinux boot loader to MBR of mmc drive, you can manually do it. 
But often better to use your Windows repair flash drive as other repairs may also be required.

Not sure which is correct, may depend on version of Linux used on which path is syslinux.
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/mmcblk0
sudo dd if=/usr/lib/syslinux/mbr/mbr.bin of=/dev/mmcblk0

What brand/model system?
Most with the mmc type drives are very lightweight systems. Is sda then an external drive?

---

### Post by tea for one on 2020-10-24
> **oldfred said:**
> What brand/model system?
Most with the mmc type drives are very lightweight systems. Is sda then an external drive?

Some of the newer lightweight netbooks/laptops come with two drives because I purchased a similar cheap 'n' cheerful model 15 months ago.

The [COLOR="#0000FF"]mmcblk0[/COLOR] drive is usually inaccessible and soldered to the motherboard.

The [COLOR="#0000FF"]sda[/COLOR] drive may be a M.2 form factor accessed (and removable) via a little door on the underneath of the laptop.

Of course, it could also be an external device and the OP should let us know.

---

