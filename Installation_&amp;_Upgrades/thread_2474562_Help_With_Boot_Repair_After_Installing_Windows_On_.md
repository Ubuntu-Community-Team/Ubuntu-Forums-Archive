---
title: "Help With Boot Repair After Installing Windows On Another HD"
date: 2022-05-02
forum: Installation &amp; Upgrades
---

### Post by victorams on 2022-05-02
Hello. I am a new user to Ubuntu, and need help with repairing my Ubuntu boot after installing Windows on another hard drive. My Linux Ubuntu is installed on a SSD (256GB) and I installed my Windows on a HD (2.0 TB). Since they were on different disks I did not think the Windows installation would cause problems on the linux installed on my SSD. Unfortunately, that does not seem to be the case. Now I cant boot on my linux. When I press F11 and boot on it, I get the message:

``
The filesystem size (according to the superblock) is 66584576 blocks
The physical size of the device is 65798144 blocks
Either the superblock or the partition table is likely to be corrupt!``
After searching the web on forums for solutions, I found out about the Boot Repair Tool ([https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)). I am currently on a Live USB Boot and have already installed it.

I have generated a paste bin with my data at [https://paste.ubuntu.com/p/svDy4H7GKG/](https://paste.ubuntu.com/p/svDy4H7GKG/).

The article, however, mentions a button that should appear with the label ``Recommended Repair``. That button does not appear for me (I only get the option of creating the BootInfo Summary).

I thought of using the Advanced Options and pressing Apply, but I fear that it may cause the loss of important data (I use my Ubuntu SSD for work, so I would really like to get that data back).

Could someone more experienced than me help me?

Thanks,
Victor Souza

---

### Post by oldfred on 2022-05-02
Boot-Repair typically updates grub menu or offers to reinstall grub.
Other fixes may need other tools.

Did you create a NTFS partition for Windows on sda? It does not have the typical UEFI Windows partitions.
And it must have seen the NVMe drive as default drive, so it installed its boot loader files into the ESP on the NVMe drive.
Not sure what Windows then does.

You may need fsck on the ext4 partition(s).  Or dosfsck on the ESP.
But run this first.
sudo gdisk -l /dev/nvme0n1
repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition nvme0n1p2 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/nvme0n1p2
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/nvme0n1p2

---

