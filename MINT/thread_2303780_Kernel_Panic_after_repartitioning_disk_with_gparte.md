---
title: "Kernel Panic after repartitioning disk with gparted."
date: 2015-11-21
forum: MINT
---

### Post by johny7 on 2015-11-21
Hi,
i have a dell inspiron 5523, which has two drives on hdd(call it sda) and one ssd(call it sdb). My system is dual boot UEFI with a large part of it being windows 8(around 332GB) and a small being linux mint(72GB). My system had a swap space on sdb and on sda i have two partitions on sda9 which has all the system files and one on sda10 which has the home folder files. Recently i wanted to pass some space from sda9 to sda10 because the first was set up with 60GB and the second with only 7.7GB. So i used gparted live cd and moved 30 GB from sda9 to sda10. After the procedure finished with no problem, when rebooting again and choosing the Linux.Mint.Cinammon option i got a kernel panic printing the following:

```

Kernel panic - not syncing: Attempted to kill init! exitcode:0x00007f00
CPU: 2 PID: 1 Comm: sh Not tainted 3.16.0-38-generic #52~14.04.1-Ubuntu

Call Trace:
dump_stack +0x45/0x56
panic+0xc8/0x1fc
do_exit+0xa57/0xa60
do_group_exit+0x3f/0xa0
SyS_exit_group+0x14/0x20
System_call_fastpath+0x1a/0x1f

Kernel Offset: 0x0 from 0xffffffff81000000 (relocation range: 0xffffffff80000000-0xffffffffbfffffff)
drm_kms_helper: panic ocurred, switching back to text console

```

I have tried to fix grub with grub repair but after succesfully doing that i've seen no change(the error stays the same).

When trying to boot manually following the instructions of :

[https://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux](https://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux)

i get the following error:

```

Targeted filesystem doesn't have requested /sbin/init.
/bin/sh: 0: can't access tty: Job control turned off
#

```

Note that when on grub command line i write ls i get partitions in the form of (hd0,gpt9) -> sda9

I am desperately trying to find a solution since i have been trying for five days to fix it.
That's why i decided to ask here.
If you need any information in order to determine the error that i can reach, i will of course give it to you.
Thanks in advance.
John

---

### Post by oldfred on 2015-11-21
Moved to Mint sub-forum, not sure what is unique with Mint.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

