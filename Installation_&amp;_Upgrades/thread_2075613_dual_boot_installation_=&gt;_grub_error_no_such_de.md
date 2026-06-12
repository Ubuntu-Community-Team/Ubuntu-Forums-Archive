---
title: "dual boot installation =&gt; grub error no such device"
date: 2012-10-24
forum: Installation &amp; Upgrades
---

### Post by Janchi on 2012-10-24
Hi all.
I have problem with my dual boot installation.
I have two HDD, first is 400 GB SATA with two partitions. On first is windows 7 and on second data. The second is 80 GB IDE with some data. So I decided to install Ubuntu on the second drive. I booted Live CD and run installation. In menu where you choose where to install I choosed something other and I made two partitions on the second drive(installation and swap). In the drop-down menu where you choose to install bootloader was choosed the first sata drive(which is also first boot in BIOS) so I leave that as it. Evrything was going good, but when i rebooted i got this error: ```
error: no such device ba689948-fce3-499a-9d73-caf7c3e77e3b
grub rescue>
```
So I tried to repair it with Windows installation cd but it didn't solve it. I also ran Live CD again and removed the installed Ubuntu. And last I ran [[COLOR="DarkOrange"]boot-repair-disk[/COLOR]]("http://sourceforge.net/p/boot-repair-cd/home/Home/") which also didn't help. So now I dont' know what to do. It would be nice if you can help me. Thanks

P.S. Sorry for my English

---

### Post by darkod on 2012-10-24
You shouldn't have deleted ubuntu right away, now there is nothing to troubleshoot.

Boot the cd in live mode (Try Ubuntu), open terminal and post the output of:
sudo parted -l (small L)

---

### Post by Janchi on 2012-10-24
Thanks for fast reply. I'm posting here output from sudo parted -l:

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SAMSUNG HD400LJ (scsi)
Disk /dev/sda: 400GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32,3kB  105GB  105GB  primary  ntfs         boot
 3      105GB   400GB  295GB  primary  ntfs


Model: ATA WDC WD800JB-00JJ (scsi)
Disk /dev/sdb: 80,0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  80,0GB  80,0GB  primary  ntfs         boot


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk! 
```Can be the problem that both drives have boot flag?

---

### Post by darkod on 2012-10-24
No, the boot flag is not an issue, windows puts it there. Right now sdb is a single 80GB ntfs partition, there is no unallocated space. Or after deleting ubuntu you expanded the ntfs partition to take the whole disk? If not, how did you try to install on sdb?

With a mix of sata and ide disks the BIOS can give problems with booting sometimes, because it might try to boot from one disk or the other regardless what you select as first option. But from what you said, it seems this is not an issue with your machine.

I would use win7 Disk Management to shrink the partition on sdb and leave unallocated space for ubuntu how much you plan to use.

Then start the installation again, use the manual method, create the partitions and put the bootloader on /dev/sdb, not /dev/sda. Lets try that. When you reboot after the install go into BIOS and change it to boot sdb first.

Let us know how it goes. If it doesn't work, don't delete anything, we can try some fixes.

---

### Post by Janchi on 2012-10-24
Yes, I expanded the partition. And I can't use Windows. Only one thing that I can use is Live CD.  And in BIOS I don't have the second drive as opinion to boot from. What I need is firstly to get back Windows and then properly install Ubuntu.

---

### Post by darkod on 2012-10-24
I forgot. :)

You can boot win7 from the grub rescue. Assuming sda1 is where win7 boot files are, execute these commands one by one at the rescue prompt:
```
insmod part_msdos
insmod ntfs
set root=(hd0,1)
chainloader +1
boot
```

That should boot win7, hopefully.

Another alternative is installing generic MBR on sda from ubuntu live mode, this acts like windows bootloader. Open terminal and do:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

After the first command there will be some warnings about the lilo configuration, ignore them and continue. That's normal.

With the generic MBR and with sda as first option to boot, windows should boot directly.

---

### Post by Janchi on 2012-10-24
Thanks a lot. Now I won't install Ubuntu, because I realized that I will have new drives and i will completely reinstall my PC. Then I will write for correct booting settings.

---

