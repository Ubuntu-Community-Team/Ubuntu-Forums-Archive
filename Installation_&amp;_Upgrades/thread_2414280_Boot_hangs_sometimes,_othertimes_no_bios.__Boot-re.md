---
title: "Boot hangs sometimes, othertimes no bios.  Boot-reair report cryptic"
date: 2019-03-08
forum: Installation &amp; Upgrades
---

### Post by cppljevans on 2019-03-08
I used the boot-repair installed on my ubuntu 18.04. 
The last window showed: 
--{--cut here-- 
Please write on a paper the following URL: 
[http://paste.ubuntu.com/p/zTPFGWTrPQ/](http://paste.ubuntu.com/p/zTPFGWTrPQ/) 


If you are experiencing boot issues, indicate this URL to people who  help you. For example on forums or via email. 
--}--cut here-- 

The version is shown by: 

evansl@lje-DL:~$ boot-repair --version 
boot-repair version : 4ppa65 
boot-sav version : 4ppa65 
boot-sav-extra version : 4ppa65 
glade2script version : 3.2.3~ppa4 
evansl@lje-DL:~$ 

The symptoms I'm having is that sometimes the system doesn't boot. 
I have to turn off/on the computer and then maybe it works. 
Other times, it takes very long time to show the login screen. 
Sometimes, it doesn't show the bios screen so I can't even change 
the boot order. 

Please help. 

-regards, 
Larry

---

### Post by kc1di on 2019-03-08
Which Graphics card is in that machine?

---

### Post by oldfred on 2019-03-08
Turning power off, often corrupts file system. Then when rebooting it may run fsck (or if Windows chkdsk) before fully booting and that can take a very long time.

Boot-Repair still shows issues with sda1 & sdb5.
If sda1 is really NTFS, then you need to run chkdsk (perhaps more than once as chkdsk does not fix everything on one pass) from your Windows or Windows repair disk. You cannot run chkdsk from Linux.
Your sdb5 if ext4 then may need fsck.
       
To see all the ext4 partitions, you may need to run on all ext4 partitions.
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb5
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb5

---

### Post by cppljevans on 2019-03-08
> **kc1di said:**
> Which Graphics card is in that machine?

How do I get the graphics card info?

---

### Post by kc1di on 2019-03-08
In a terminal copy and paste this command ```
lspci | grep VGA
``` post the output here.

---

### Post by oldfred on 2019-03-08
One line:
       lspci | grep VGA 
    
Bit more detail, shows driver:
       sudo lshw -c display

---

### Post by cppljevans on 2019-03-08
Dave, here's the output:

evansl@lje-DL:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Oland [Radeon HD 8570 / R7 240/340 OEM]

---

### Post by cppljevans on 2019-03-08
The lspci more detailed report:

 *-display                 
       description: VGA compatible controller
       product: Oland [Radeon HD 8570 / R7 240/340 OEM]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:31 memory:e0000000-efffffff memory:f7e00000-f7e3ffff ioport:e000(size=256) memory:c0000-dffff

---

### Post by cppljevans on 2019-03-08
> **oldfred said:**
> Turning power off, often corrupts file system. Then when rebooting it may run fsck (or if Windows chkdsk) before fully booting and that can take a very long time.

Boot-Repair still shows issues with sda1 & sdb5.
If sda1 is really NTFS, then you need to run chkdsk (perhaps more than once as chkdsk does not fix everything on one pass) from your Windows or Windows repair disk. You cannot run chkdsk from Linux.
Your sdb5 if ext4 then may need fsck.
       
To see all the ext4 partitions, you may need to run on all ext4 partitions.
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb5
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb5

Oldfred, thanks for the detailed instructions.  I'll reboot with my liveusb ubuntu18.04.2 and see if I can do it all.
I'll see if I can save what I do to another usbstick so that I can report results back here.
Hope it works.

OK, here's the results:
```

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD10EZEX-08W (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  185GB  185GB   primary
 3      185GB   485GB  301GB   extended
 6      185GB   468GB  284GB   logical   ext4
 5      468GB   485GB  17.1GB  logical
 2      485GB   500GB  14.7GB  primary   ntfs         boot


Model: ATA ST3500630AS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  500GB   500GB   extended
 5      64.5kB  43.0GB  43.0GB  logical   ext3
 6      43.0GB  500GB   457GB   logical   ext4


Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel? 

```
I cancelled because I didn't know what to do.

Any further suggestions?

---

