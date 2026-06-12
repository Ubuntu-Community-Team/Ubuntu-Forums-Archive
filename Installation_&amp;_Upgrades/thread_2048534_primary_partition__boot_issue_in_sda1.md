---
title: "primary partition / boot issue in sda1"
date: 2012-08-26
forum: Installation &amp; Upgrades
---

### Post by pierreu1 on 2012-08-26
Hi There,

I feel I need to re-install ubuntu (due possibly fix a fan failure since upgrading using 4 different manners did not work).

I checked using gparted what my system looks like and I have:

sda1 (ext4) mounted as / 73 GB / boot (40 BG is used)
sda2 that has the swap linux (sd3) / 3GB

Can I actually re-install Linux cleanly? What will happen to my boot file if I were to wipe things completely. (I do not have the machine recovery disk/windows).

I do have an external drive (1 TB with my backup : 100 GB)/NTFC.

Because of viruses, I would rather clean my system off completely. No rootkits according to rootkit hunter/chkrootkit. Phew!

Any idea on how to do this?

Thanks!

---

### Post by darkod on 2012-08-27
Can you list the partitions you have more precisely? One line, one partition.

You mention both / and /boot in the same line, I don't understand this:
> sda1 (ext4) mounted as / 73 GB / boot (40 BG is used)
sda2 that has the swap linux (sd3) / 3GB

Yes, you can make a clean install using existing partitions. You will need to use the manual partitioning and tell the installer which partition to use as what. It will not touch other partitions, just the ones you specify, so it has nothing to do with windows restore partitions, if that was your question.

---

### Post by pierreu1 on 2012-08-27
> **darkod said:**
> Can you list the partitions you have more precisely? One line, one partition.

You mention both / and /boot in the same line, I don't understand this:


Yes, you can make a clean install using existing partitions. You will need to use the manual partitioning and tell the installer which partition to use as what. It will not touch other partitions, just the ones you specify, so it has nothing to do with windows restore partitions, if that was your question.

Thank you.

I have made a screenshot of my partitions so this can help you better. I am concerned about the boot (destroying it).

---

### Post by oldfred on 2012-08-27
Do you have your /home backed up. And a backup to NTFS may not work or work well as NTFS does not support ownership & permissions.

You have your instal in sda1 with / (root) and the boot flag. Grub does not use boot flag, but some BIOS require it, so we still suggest you have it. Windows has to have a boot flag to know which partition to boot from.

You can use manual install or auto install and totally overwrite current. I always prefer manual install as then I can control sizes of partitions better, but in your case it really does not matter.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

---

### Post by pierreu1 on 2012-08-28
> **oldfred said:**
> Do you have your /home backed up. And a backup to NTFS may not work or work well as NTFS does not support ownership & permissions.

You have your instal in sda1 with / (root) and the boot flag. Grub does not use boot flag, but some BIOS require it, so we still suggest you have it. Windows has to have a boot flag to know which partition to boot from.

You can use manual install or auto install and totally overwrite current. I always prefer manual install as then I can control sizes of partitions better, but in your case it really does not matter.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

Oh! Very helpful! Thanks so much! Auto install is probably what I am going to use then because I just want to have a working system!! 

I saw on disk utility a way to edit the external drive to whatever EXT,... What will happen to the content of the drive if I do this? Will it wipe the content out?

BTW, if I may, my clamtk is not seeing the mounted external drive when selecting scan a device. Is it because of some permission settings on the drive? NTFS issue? It can scan a file or directory within the drive though! Strange! No?

---

