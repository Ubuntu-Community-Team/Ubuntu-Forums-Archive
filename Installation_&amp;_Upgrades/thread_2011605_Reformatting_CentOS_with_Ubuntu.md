---
title: "Reformatting CentOS with Ubuntu"
date: 2012-06-27
forum: Installation &amp; Upgrades
---

### Post by corey210 on 2012-06-27
I currently have a computer with both Windows7 and CentOS, however my friend has shown me Ubuntu and I have become addicted. So I want to swap CentOS with Ubuntu... However, everytime I try to do this, the booting page (I boot from USB) will only let me overwrite the Windows7 portion... Is there a way that I can overwrite centOS or will I have to find my Windows7 cd and rewrite everything and then install ubuntu? Sounds like overkill, please help!

---

### Post by darkod on 2012-06-27
Just select Something Else (the manual installation method) and when it shows you the list of partitions:
Select the root partition of CentOS (the bigger one), click the Change button below. Change Use As into ext4, select mount point /, tick the format box.
Select the swap partition on the disk, click the Change button, change Use As into swap area. There is no mount point for swap.

If you have a separate /home partition, you can use it too with mount point /home. Whether you format it or not is your choice but some program settings might conflict with ubuntu if you don't format it.

For the bootloader device selection, select /dev/sda (the disk MBR).

That should be it.

---

### Post by corey210 on 2012-06-27
Thanks so much, I must have done something a little differently... But it works and I love it! good to have Ubuntu back on!

---

