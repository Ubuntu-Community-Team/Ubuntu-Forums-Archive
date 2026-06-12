---
title: "baffled by partitioning"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by elbow rub on 2008-06-26
It's been a very long time, since Breezy that I've messed with Ubuntu. I tried to partiton, but was umncertain. I then read over and over on ubnutu.com, the section explaining how to partition. Tried again and nothing. So can someone please help me out, please. 

When it goes into the partitioning area, this is what I get:
/dev/sda
    /dev/sda1 ntfs            126 GB unknown
    /dev/sda5 ntfs            123 GB
    freespace                 8 MB

What I did, was edited /sda5 to create my swap, which I wanted to give 4 GB to. Once I continued, it wouldn't proceed and gave me an error saying I didn't have the disk space, I think. I know I'm missing something very obvious to this, Breezy didn't leave me with questions, but now I have them.

Please any help will be appreciated.

Thank you,

elbow rub

---

### Post by logos34 on 2008-06-26
Can you boot frm the ubuntu live cd and post your fdisk output?

applications>terminal:

[B]sudo fdisk -l
[/B]

Also, open gparted (System>admin>parttition editor)

What does it show (used space %)?

---

### Post by elbow rub on 2008-06-26
Thank you very much for your response, I was able to do that.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15323   123081966    7  HPFS/NTFS
/dev/sda2           15324       30393   121049775    f  W95 Ext'd (LBA)
/dev/sda5           15324       30393   121049743+  82  Linux swap / Solaris

---

### Post by logos34 on 2008-06-26
Use gparted to delete the /swap (sda5).  Create a new swap ~2 x your ram (up to 1 GB ram), and 1 x ram thereafter.  Then start the installation again and choose 'guided--use largest continuous free space' option.  It should put root on the rest of the space inside sda2.

---

### Post by elbow rub on 2008-06-26
Sorry, I'm not sure what you mean by using gparted to delete the swap

thanks

er

---

### Post by logos34 on 2008-06-26
open gparted as described above.  Click on swap and press delete.  Then either create a 'new' one or just go ahead with the installation and choose guided install.

---

### Post by lisati on 2008-06-26
> **elbow rub said:**
> Sorry, I'm not sure what you mean by using gparted to delete the swap

thanks

er
On the Live CD there's a program Gparted (found in the System->Administration menu) that lets you tinker with the partitions.

You might need to turn swapping off and unmount the swap partition before making changes to it. This can be done through GParted.

EDIT: **IMPORANT**: take your time deciding what to do with partitions, and make sure you have a backup of important data.

---

### Post by elbow rub on 2008-06-26
Thank you all for the help, it worked. Now to refresh my memory.

Thank you

Er

---

