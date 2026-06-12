---
title: "install on ssd"
date: 2022-01-04
forum: Installation &amp; Upgrades
---

### Post by jgw on 2022-01-04
I just bought a HP Compaq 8200 Elite and want to install ubuntu on an ssd.  I have tried to install on a hard drive and had no problem so I thought I would go on the ssd route.  I have, I think (never sure) attached a picture of my ssd from Disks so you can see how its currently setup.  Any help on this one would be appreciated.

Thank you........................

---

### Post by oldfred on 2022-01-04
This is my external SSD. I put a larger NVMe as internal drive and had M.2 SSD, now in USB adapter.
I have both my old Bionic (Ubuntu) & a Focal (Kubuntu) install. Bionic will become Jammy soon. Those were my main working installs before new installs to NVMe drive. External SSD now only has some data as most was on HDD. And now most on NVMe drive. With HDD as backups & test installs.

[FONT=monospace][COLOR=#000000]lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid[/COLOR]
[/FONT]
```

[FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]sdb                232.9G                                                   [/COLOR]
&#9500;&#9472;sdb1      vfat     510M        M2_ESP    m2_esp                          D966-440A 
&#9500;&#9472;sdb2      ext4    31.3G        m2_ssd    m2_ssd                          ab8e9088-d764-4d92-ad83-3374b314b9ac 
&#9500;&#9472;sdb4      ext4    25.4G        bionic    bionic                          c29fc361-ea05-420b-b919-850aeef65dd4 
&#9492;&#9472;sdb5      ext4   127.4G        m2_data   m2_data                         0c374965-53c6-437c-a2ad-f0508486f9d5
[/FONT][/COLOR][/FONT]
```

You do need to partion in advance and must do a work around to have grub2 boot loader installed to external drive.

Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive.

---

### Post by ubfan1 on 2022-01-04
Assuming there's nothing on the ssd you want to save, even before deleting/adding partitions, change the partition table to gpt.  Looks like it's now msdos partitioning from the extended partition you display.

---

### Post by jgw on 2022-01-06
Thank you for the replies.

I changed the partition table and then installed Ubuntu 20.04.3 with no problems.   The installation wanted to reformat partitions, etc. so, actually, my question was even necessary (I suspect)

---

