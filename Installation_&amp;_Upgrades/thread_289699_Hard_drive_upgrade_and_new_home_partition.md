---
title: "Hard drive upgrade and new /home partition"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by mibikerguy on 2006-10-31
I have successfully installed a larger HDD to my Dapper install and all seems to be working well. Using the Psychocats directions re "creating a seperate /home partition in Ubuntu"([http://www.psychocats.net/ubuntu/separatehome)](http://www.psychocats.net/ubuntu/separatehome)), I have successfully created the partition, formatted it to ext3 and can reboot and become operational with no error messages or problems. However, my question is:

Does the \home file physically get moved to the new partition when using the Psychocats instructions? I ask this because when using the file browser or partition manager to review the contents of the new partition, I see no indication of any used space.

All suggestions welcome.

Tom

---

### Post by Coelocanth on 2006-10-31
It does, but you need to have designated your new partition on the new hard drive. For example, let's assume your old, original drive is hda. If the new drive is hdb, you need to have used that as the target for your newly-made partition. From your description of your problem, I'd guess you made the new partition on your old drive and just resized your Ubuntu install on that drive to accomodate it.

*edit* forgive me if I've misunderstood.

---

### Post by mibikerguy on 2006-10-31
Thanks for the reply.
My process was as follows:
(1) Installed new drive and rebotted from "Ubuntu Live" disk; (2) Format new disk to ext3; (3) Use "dd if=/dev/sda of=/dev/sdb" which produced a "bootable image"; (4) Remove "old drive"; (5) Make active and format to ext3 the "extra" space on the "new" larger drive; (6) Apply the instructions from Psychocats using the drive designations found in the Gnome Partition Editor (ie. /dev/sda1 and /dev/sda3).

It seems that when I applied the directions there was no physical move of the /home file to the newly formatted partition of the larger "new" drive.

Tom

---

