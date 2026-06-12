---
title: "Boot repair error"
date: 2018-09-26
forum: Installation &amp; Upgrades
---

### Post by maitanemuba on 2018-09-26
Hi everyone!

I am trying to install Ubuntu in my laptop along with Windows 10. I thought I had succeeded quite easily, I even managed to log in once but after having logged in Windows just to check everything was okay, I couldn't get into Ubuntu. A Grub terminal would open all the time instead of booting Ubuntu.

I have been looking for solutions and tried Boot-Repair. I followed the steps as indicated and everything seemed to work alright, but when trying to reboot again, I cant boot Ubuntu. Hence, following the recommendations of Boot-Repair, I copy-paste here the URL the program has provided me with

[https://paste.ubuntu.com/p/42rC5R9wFK/](https://paste.ubuntu.com/p/42rC5R9wFK/)

in case anyone could help me. I am not new to Ubuntu, but I am far from understanding what I am doing and I just rely on forum comments and suggestions. Hopefully someone could help me with this issue. I am otherwise thinking of deleting the partition and starting it all over again, although I don't know if this is a naive approach or I am walking on the tightrope with my computer. 

I have the feeling each step brings me closer to destroying it... Does someone have any idea why it is not working as it should? Thank you very much in advance!

---

### Post by oldfred on 2018-09-26
Script has not been fully updated to show the newer NVMe drives.

You may have Windows hibernated/fast start up on. You need to have that off. Note that Windows updates will turn it back on, so you need to then boot directly from UEFI and turn it off.

In some places you show nvme0n1p6 as Linux and others it is not shown at all. It looks like Boot-Repair tried fsck & then NTFS fixes on p6 (which would not work, anyway). But partition not fixed?

Post this:
sudo gdisk -l /dev/nvme0n1

At some point you have Ubuntu installed as it still has a boot entry in UEFI.
What brand/model system? What video card/chip?

You could turn UEFI Secure Boot off, but I do not think that is issue, now. If you originally installed with it off, that could be issue then as UEFI Secure Boot is now on per script.

You could try full fsck, but if it cannot correctly see p6, it may not work.
       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s), I think I have nvme set correctly.
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/nvme0n1p6
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/nvme0n1p6

---

