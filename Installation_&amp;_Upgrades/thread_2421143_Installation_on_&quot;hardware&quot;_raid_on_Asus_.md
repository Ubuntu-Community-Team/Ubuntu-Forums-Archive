---
title: "Installation on &quot;hardware&quot; raid on Asus M4N78pro"
date: 2019-06-17
forum: Installation &amp; Upgrades
---

### Post by thiemo-kellner on 2019-06-17
Hi all

Lately I wanted to install most recent lubuntu (19.04) onto a "hardware" raid of an Asus M4N78pro mainboard. I downloaded the iso and dded it on a USB stick. I could boot into the live environment and start the installer. However, the raid partitions do not show up then, I only see sda partitions. On the other hand, I can see the raid partitions in the /dev/mapper directory when I do not start the installer. After starting the installer they are gone. I have a Windows parallel installation I do not want to erase. That's the reason I use the "hardware" raid of the mainboard.

Can I use the installer somehow to install on the "hardware" raid?

If no, is there another way to install lubunto on a configuration like mine?

Kind regards

Thiemo

---

### Post by SeijiSensei on 2019-06-17
If it's real hardware RAID the device would appear as a single disk. For instance, I maintain a server with a LSI Logic controller. The array appears as /dev/sda.

If this is a "fake" RAID controller, you may need a special driver, which may or may not exist for Linux.

---

### Post by oldfred on 2019-06-17
Do not know RAID, nor use it.

RAID is better supported with the server installer and then you can add the desktop of choice.

I have this link.
[https://askubuntu.com/questions/660023/how-to-install-ubuntu-14-04-16-04-64-bit-with-a-dual-boot-raid-1-partition-on-an](https://askubuntu.com/questions/660023/how-to-install-ubuntu-14-04-16-04-64-bit-with-a-dual-boot-raid-1-partition-on-an)

This is now very old, probably not useful.
       [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04 and later.

---

### Post by thiemo-kellner on 2019-06-18
Thanks for your advice and links. I already figured that it is (also) seen as sda/sdb. I think about installing on the non windows partitions as usual software raid this weekend.

---

