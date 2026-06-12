---
title: "Can I use Windows 7 bootloader to boot Ubuntu 12.04?"
date: 2012-05-21
forum: Installation &amp; Upgrades
---

### Post by LMDevlin on 2012-05-21
Hi guys,

So after a long hiatus from using Ubuntu, I have returned to it by putting spare 160GB SATA hard drive into my PC and putting Ubuntu 12.04 on it. I figured installing it on a second hard drive was the safest/easiest way to do it. I installed it using the regular installation CD downloaded from the website.

An article I read on the web recommended that, when it came to installing the bootloader during the Ubuntu installer, I should put it onto the **second hard drive- the one I would be installing Ubuntu onto**. I proceeded with this, and checked that I could boot Windows 7 fine. I then used EasyBCD's GRUB 2 option to install GRUB 2, but it does not automatically detect Ubuntu, and instead tries to boot off what looks like every device and partition I have before failing.

However, if I simply use the BIOS boot menu to select the second disk, it loads into GRUB 2, and gives me all the Ubuntu options, *plus* options for Windows 7. Go figure.

I tried to use plain old GRUB and NeoGRUB in EasyBCD, but neither of those options work.

I suspect I was following some bad instructions, or I simply made a mistake somewhere, but was I supposed to have replaced the Windows 7 bootloader with GRUB 2, or is there yet still hope that I can use the Windows 7 bootloader and add a *working* Ubuntu entry to it?

I have read other threads on this forum before posting here, but I'm having trouble finding a thread which resolves my specific issue. Apologies if there is one already.

My disk setup is as follows:

Drive 0
Partition 1 (NTFS - G: System Reserved - 100MB)
Partition 2 (NTFS - C: Windows 7 - 931GB)

Drive 1
Partition 1 (Ext4 - Ubuntu - 149GB)
Partition 2 (Swap - 4GB)

Any help you can offer would be most appreciated.

---

### Post by darkod on 2012-05-21
And what's wrong with simply using grub2 from the second disk? It can boot both ubuntu and windows, plus it still leaves windows bootloader on the first disk that can boot windows in emergencies if something happens to grub2.

For EasyBCD issues you should better visit their forum, they should have best knowledge how the program works.

---

### Post by wilee-nilee on 2012-05-21
Standard protocol is the MS boot on the MS HD grub boot on the linux HD, boot with the LInux HD having grub show both boot is easy. If you remove the linux MS still boots, if you boot from its HD. If you cannot get the Linux HD to read the windows then use the boot script to debug. You just have the Linux first read to have this ease of travel, you can even change the grub menu to default to windows boot

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Look in extracted packaga for instructions on running, post if needed.

---

### Post by LMDevlin on 2012-05-22
Y'know what? I don't know why I didn't think of simply switching the order my disks were booting in.

I'm happy with that, thanks for the responses.

---

