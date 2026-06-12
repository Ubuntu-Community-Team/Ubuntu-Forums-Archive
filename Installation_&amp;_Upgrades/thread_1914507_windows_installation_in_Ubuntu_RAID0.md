---
title: "windows installation in Ubuntu RAID0"
date: 2012-01-24
forum: Installation &amp; Upgrades
---

### Post by volido on 2012-01-24
This is my first time  with Linux but I'm absolutelly determined to move into it. All my office is on vista 64 since 2007 and i cannot stand it anymore.
To start i would like to do a clean installation in a hpxw8200 with two SCSI HD36GB in. I'm thinking to install root and swap in RAID0 form Linux software disabling  raid from the BIOS( this machine won't contain data, only applications) .  This computer probably will need  to have a windows installation next to Ubuntu in close future for very specific context. I'm thinking in a light XP32b. 
should I do a partition in NTFS to host future XP OS during the Ubuntu installation? can this NTFS partition be in RAID 0?  Has this is option any sense or  windows should be installed  in a virtual machine once Ubuntu is working?. please feel free to suggest better configurations, this is the first time I'mm jumping out of the window and all ideas are very welcome.

---

### Post by darkod on 2012-01-24
You can't dual boot if you use linux software raid. Windows can't understand it and it will see simply two separate disks.

Depending how you use the machine. I would say the XP inside a VM is a good option because that way you don't have to restart from one OS into the other. On the other hand, depending on your use you might want to restart and boot XP on its own, not a VM. But as I said this means you can't use software raid.

About using the softraid, take this into account too: the /boot folder can't be on raid0. You will have to leave out a small part of the disks (500MB is enough) and set /boot as mount point there. You can use the 500MB partition on one disk as /boot, or configure both 500GB partitions as a softraid raid1. As far as I know, it doesn't mind being on raid1, only raid0 makes problems.

Another thought, I am sure you already investigated, in raid0 your data is not safe. If one disk goes, everything goes. Depending how important the data (the applications on it) will be, you might want to consider raid1 and not raid0.

If you need any help, feel free to ask. One link to start you off with software raid (it's a bit old, but good):
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by volido on 2012-01-27
Thank you very much for your advice ...the installation works perfect.
I'm amazed with this new Linux experience....
Following your proposal I thing  the idea of the Virtual box is much more interesting that the dual boot... so I'm  going  to do it  for the installation of an XP-32 avoiding the dual boot option. The last time I used this XP cd was 2001...:p:p crazy.
Respect to virtualization I was thinking in the Wine option but Im not sure it will work for something like 3d's-Max,or Adobe's maybe I'm wrong...Im a little worried about graphic acceleration in a virtual context...anyway I'm reading about Virtual-box and looks very suitable and the appropriate solution for my scheme. 
Thank you again for your help.
best

---

