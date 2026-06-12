---
title: "grub-probe mapping error in GRUB2"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by twescott on 2010-01-06
I am having trouble upgrading from old grub to grub-pc.  I have a clean install of 9.10 on a system with a new ASUS motherboard with Nvidia RAID configured as RAID 0.

Although I read the page on SATA pseudo-RAID, this doesn't seem to apply, as both 9.10 and Windows XP installed cleanly without any additional drivers required.

I did notice that contrary to the documentation, 9.10 installed with grub v0.97, not the new one as claimed.  It is working fine, but just to be ornery, I'm trying to upgrade to the new one, and this is where I ran into trouble.

Whenever I try to run grub-upgrade, I get an error from grub-probe that 'no mapping exists for' my raid partition.  Apparently grub-probe can deal with the device, but not with the fs_uuid, as follows:

twescott@latitude:~$ sudo grub-probe -t device /boot/grub
/dev/mapper/nvidia_fcacbeib5

twescott@latitude:~$ sudo grub-probe -t fs_uuid /boot/grub
grub-probe: error: no mapping exists for `nvidia_fcacbeib5'

The system seems to be recognizing the RAID with no problems, as in:

twescott@latitude:~$ sudo blkid
/dev/mapper/nvidia_fcacbeib1: UUID="28D83EB2D83E7DDE" TYPE="ntfs" 
/dev/mapper/nvidia_fcacbeib2: UUID="4344165e-07c3-4da6-b640-da9bf964a74e" TYPE="swap" 
/dev/sda: TYPE="nvidia_raid_member" 
/dev/sdb: TYPE="nvidia_raid_member" 
/dev/mapper/nvidia_fcacbeib5: UUID="3bcc8912-dda1-4bf2-a7d3-b759cb33fcb1" TYPE="ext4" 

I'm thinking the problem may be in my grub device.map file, which only lists the SATA raw device aliases, but I may be completely wrong:

twescott@latitude:~$ cat /boot/grub/device.map
(hd0)    /dev/sda
(hd1)    /dev/sdb

Does anyone have any suggestions?  Thanks in advance!

---

### Post by meierfra. on 2010-01-06
Rename  or delete the device.map. Then "update-grub" will be forced to generate a new one.
(edit:  I  reread your post and I am no longer sure that  this will work)

---

### Post by twescott on 2010-01-06
<grin>.. You were right, it rebuilt device.map exactly as it was before.  Thanks for the help anyway, every attempt teaches me something!

---

### Post by Kzin on 2010-03-05
Similar issue, but my 9.10 comes with grub-pc(GRUB2) I am going from the console during install. Going to install grub legacy just to get the system going.  Pls let me know if you figure anything out.

---

### Post by Kzin on 2010-03-05
I found a pretty hacker workaround.

-I ran the Ubuntu Alternate installer (regular one doesn't work with my video card)
-Got to the point where it drops out of the install due to grub2 install failure.
-Went thru steps in fakeraidhowto to mount the /target (mount -t proc proc etc etc etc etc)
-moved my /etc/apt/sources.list to /etc/apt/sources.bak
-created new sources.list with
deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) lucid main
-apt-get update
-apt-get install grub-pc

Worked like a charm, I was able to select my nvidia raid instance instead of /dev/sd0 /dev/sd1.

---

### Post by Kzin on 2010-03-05
Oh yea, I should mention that I used the console (alt+ctrl+F1) and that when I was done I returned to the installer and let it finish.

---

