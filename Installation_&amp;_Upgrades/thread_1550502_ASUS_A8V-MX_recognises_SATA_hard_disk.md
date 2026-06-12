---
title: "ASUS A8V-MX recognises SATA hard disk"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by Trismegister on 2010-08-11
This is a solution to a problem that has bugged me for months but I finally got around to solving.
I hope this will be useful to anyone using Ubuntu with GRUB2 who has the same problem.

I am running Ubuntu 10.4 Lynx which did not recognise the newly-installed SATA HDD.
In fact, booting up would face me with a recovery shell.

The solution is to add the pci=nomsi kernel parameter

To do this you need to edit the /etc/default/grub file and add the kernel parameter as follows:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="pci=nomsi"

``` 
then run: ```
sudo update-grub
```

I edited this after having installed Ubuntu  with the SATA device *disabled* in the BIOS settings.
Then I added the kernel parameter and rebooted after having set the device to SATA. 

Notes:
[LIST=1]
[*]MSI, or **Message Signaled Interrupts**, in PCI 2.2 and later and PCI Express, are an alternative way of generating an interrupt. Evidently Ubuntu and the ASUS motherboard didn't agree on this occasion.
[*]The Legacy GRUB solution from which I adapted my solution is on [http://ubuntuforums.org/showthread.php?t=934469]("this thread")
[*]More about **GRUB2** and **Legacy GRUB** at this article: [https://help.ubuntu.com/community/Grub2]("this article")
[*]The _Advanced >> Chipset >> Southbridge >> Serial ATA Controller_ setting in the machine's BIOS Setup, is set to _SATA_
[/LIST]

---

### Post by sinurge on 2010-08-11
This problem occurs with Fedora/Mint/Suse as well for the same board. I have the same moboard. This has been posted and is not only for this mb.

---

