---
title: "Grub 2: Disk not found error after adding menu entry in 40_custom"
date: 2013-04-05
forum: Installation &amp; Upgrades
---

### Post by actetylcholine on 2013-04-05
Hi,

I'm trying to add a new entry to the Grub 2 boot menu. The goal is to have the option to boot into a live linux OS called [Bankix]("http://www.heise.de/download/ct-bankix.html") (derived from Ubuntu 12.04 and geared towards safe online banking). Bankix is installed on a SD memory card on /dev/sdc1. From what I understand, I need to edit /etc/grub.d/40_custom to make a new entry appear in the Grub 2 boot menu. I added the following:


menuentry 'Bankix' {
    insmod chain
    set root=(hd2,1)
    chainloader +1
}


When I select this option from the Grub 2 menu on startup, I get an error: disk 'hd2,1' not found. I'm at a loss as to why Grub 2 can't find the memory card. I'm using Ubuntu 12.10 with Windows 8 dual boot. Can anybody help?

Thanks, Thomas

---

### Post by darkod on 2013-04-05
I'm not sure if it will solve your issue, but if the Bankix bootloader is installed on the MBR of the card, /dev/sdc, and not on the partition /dev/sdc1, the entry should be like:
set root=(hd2)

Since the bootloader is on the MBR of the disk, you don't specify the partition. If the bootloader is on the partition on the other hand, the (hd2,1) was correct.

Did you check whether grub2 has sdc referenced as hd2? If the card was not present it could have not created a mapping hd2 for it. I think you can make grub2 remake the device map with:
sudo grub-mkdevicemap

Make sure the card is plugged in when you run that.

---

### Post by actetylcholine on 2013-04-05
Thanks Darko for the quick reply! Since I tried both your suggestions, I'm not sure which one did the trick, but at least now I get a different error message :/ Will create a new thread for that though. Thanks again!

---

### Post by oldfred on 2013-04-05
The other issue is grub's drive number. I have several drives and normally boot from sdc. Then with grub sdc is hd0, and then BIOS/grub numbers drives in same order as ports on motherboard or sda is hd1. But if I boot sda then that is hd0.
And my system gets mixed up as I skipped a port and sometime my USB flash drive is sdc and sometimes sdf which also changes hd number in grub. Or I use from grub menu e and have to change hd3 to hd5 or something to make it work.

---

