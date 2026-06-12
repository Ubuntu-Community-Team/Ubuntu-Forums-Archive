---
title: "Laptop cannot reboot just boot"
date: 2015-10-07
forum: Installation &amp; Upgrades
---

### Post by ineuw on 2015-10-07
My single OS laptop will only boot but cannot reboot.

The OS is Xubuntu 14.04.3 32bit installation on a 64bit system. The boot is set to BIOS and I created a Boot repair report here: [http://paste.ubuntu.com/12698763/](http://paste.ubuntu.com/12698763/) 

Everything is completely updated but reboot just hangs. Otherwise it works fine.

The laptop is an Acer Aspire 64bit, Intel N3540 64bit CPU, 4GB ram and 500gb, bootable with either UEFI or BIOS.

Help would be most appreciated and please ignore the signature below. It refers to my desktop.

---

### Post by gordintoronto on 2015-10-08
"Cannot reboot" what happens? You click on "Restart," and then what?

---

### Post by ineuw on 2015-10-09
@gordintoronto, it goes through the steps of shutting down, screen goes blank, and it just hangs. After searching this forum, I found a post with a similar problem and will try it tomorrow, (loaned the laptop to a friend) it just might be the addition of GRUB_CMDLINE_LINUX="noefi". I hope this will fix it.

After the crash, I had to set the BIOS to "Legacy" because UEFI would not access the USB key for Boot Repair. With BRr I created the partitions as indicated by the pastebin report but kept getting the message "Warning. Partition table identifier GPT (GUID) detected on "/ dev / sda"! fdisk does not support GPT. Use GNU Parted." I looked in GParted could not understand what had to be done. Installed Xu14.04 using a USB key. It gave me the same message about my partition scheme but continued to install. The pastebin report was created with boot repair from within Xubuntu.

I forgot to include this earlier: BIOS Information, vendor: Insyde Corp. version: V1.08, The company has not released any firmware updates.

---

