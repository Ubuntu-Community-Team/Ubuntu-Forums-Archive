---
title: "Cannot boot Ubuntu 12.04.1 LTS"
date: 2012-10-02
forum: Installation &amp; Upgrades
---

### Post by Vectorian on 2012-10-02
Hello every one,

I am having troubles with starting my Ubuntu 12.04.1 LTS being installed along Vista as Vista boots automatically without giving the boot options. You probably saw many other similar problems but I just cant fix it by myself because every case is very different and its solutions do not fully apply to the one I have.

Here is the information I gathered for ya:

Boot Info Script log file: [http://paste.ubuntu.com/1256743/](http://paste.ubuntu.com/1256743/)[FONT=Arial] (boot-repair has been executed as well).[/FONT]

[FONT=Arial]This is what [/FONT]gksu gedit [FONT=Courier New]/etc/fstab[/FONT][FONT=Arial] says:[/FONT]
> overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0[FONT=Arial]
[/FONT]
[FONT=Courier New]sudo fdisk -l[/FONT]
> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1c4c4b75

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Hidden NTFS WinRE
/dev/sda2   *     3074048   316418047   156672000    7  HPFS/NTFS/exFAT
/dev/sda3       316418048   550567919   117074936    7  HPFS/NTFS/exFAT
/dev/sda4       550567934   625139711    37285889    f  W95 Ext'd (LBA)
/dev/sda5       558958592   625139711    33090560   83  Linux
/dev/sda6       550567936   558958591     4195328   82  Linux swap / Solaris

I think the problem might be the unmounted /dev/sda5 partition so I made a screenshot of GParted:
[http://img21.imageshack.us/img21/1199/gpartedscr.png](http://img21.imageshack.us/img21/1199/gpartedscr.png)

As you may have noticed, I'm completely new to Linux.

Thanks in advance!!

---

### Post by darkod on 2012-10-02
In live mode the partition is unmounted by default, nothing strange there.

The bootinfo results look fine, can you tell us what exactly is happening when you try to boot now?

Grub2 is on the MBR as it should be, and the config files are good.

Do you get the grub2 boot menu at start?
If yes, what exactly is happening when you try to boot ubuntu, and when you try to boot vista?

---

### Post by Vectorian on 2012-10-02
Well, looks like boot-repair did the trick. I just rebooted and noticed the grub2 menu appears now. However, in the beginning I could start Ubuntu only by inserting the Live CD - otherwise Vista started normally as if there was no Ubuntu at all (--> no grub). Anyway, I'm still glad to hear that I did everything right during the installation. Thanks.

---

