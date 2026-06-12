---
title: "Problems appear after installation"
date: 2013-10-30
forum: Installation &amp; Upgrades
---

### Post by ville.jt.kauppinen on 2013-10-30
I have installed 12.04.3 on my mini-laptop (eMachines 350-21G16kk). Everything is fine after installion, but when I reboot the laptop couple of times, nothing works and system cannot mount drives. It won't start even in recovery mode. I haven't installed windows on the hard drive, just ubuntu. How can I fix the problem? I attached picture of error message in this forum post.

---

### Post by ville.jt.kauppinen on 2013-10-31
I have tried to fix problem with sudo fsck /dev/sda1/ command in live-usb mode. Same problems appears after few reboots.
What should I do next?

---

### Post by fantab on 2013-10-31
Try installing again. But before you do:

Post some details of your computer, RAM, Graphics, CPU etc.
And also Boot with Ubuntu DVD/USB and 'Try Without Installing'. Open Terminal [Ctrl+Alt+T], run the following command and post the output:

```
sudo parted -l
sudo fdisk -l
```

---

### Post by ville.jt.kauppinen on 2013-11-02
Here is some information about my computer:
[TABLE]
[TR]
[TD="class: product_specs_features product_specs"]Processor[/TD]
[TD="class: product_specs_descript product_specs"]         Intel® Atom™ processor N450 (512 KB L2 cache, 1.66 GHz, 667 MHz FSB)[/TD]
[/TR]
[TR="class: product_specs_row"]
[TD="class: product_specs_features product_specs"]Chipset[/TD]
[TD="class: product_specs_descript product_specs"]         Mobile Intel® NM10 Express Chipset[/TD]
[/TR]
[TR="class: product_specs_alternate_row"]
[TD="class: product_specs_features product_specs"]Memory[/TD]
[TD="class: product_specs_descript product_specs"]         Up to 1 GB of single-channel DDR2 memory, upgradable to 2 GB using one soDIMM module[/TD]
[/TR]
[TR="class: product_specs_row"]
[TD="class: product_specs_features product_specs"]Graphics[/TD]
[TD="class: product_specs_descript product_specs"]         Intel® Graphics Media Accelerator 3150 (Intel® GMA 3150), 64 MB of dedicated video memory, supporting Microsoft® DirectX® 9                  External resolution/refresh rate[SUP][3]("http://support.gateway.com/emachines/notebook/2010/emachines/em/em350/eM350sp2.shtml#sup_3")[/SUP]:         
         
[LIST]
[*]VGA port up to 1400 x 1050: 60 Hz 
[/LIST]
[/TD]
[/TR]
[/TABLE]
More: [http://support.gateway.com/emachines/notebook/2010/emachines/em/em350/eM350sp2.shtml](http://support.gateway.com/emachines/notebook/2010/emachines/em/em350/eM350sp2.shtml).


sudo parted -l gave following information:
> Model: ATA WDC WD1600BEVT-2 (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  159GB  159GB   primary   ext4            boot
 2      159GB   160GB  1061MB  extended
 5      159GB   160GB  1061MB  logical   linux-swap(v1)

sudo fdisk -l gave following information:
> Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000196c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   310505471   155251712   83  Linux
/dev/sdb2       310507518   312580095     1036289    5  Extended
/dev/sdb5       310507520   312580095     1036288   82  Linux swap / Solaris

---

### Post by fantab on 2013-11-02
Not sure what the problem is with your current install.
Re-installing might help.

A suggestion: Your e-machine specs are a bit low for Ubuntu, consider installing Xubuntu or Lubuntu.

---

### Post by ville.jt.kauppinen on 2013-11-02
First I tried to install Xubuntu and Lubuntu alongside with Win7 Starter, but same problems appeared (OS didn't started after couple of reboots). Maybe I'll try next clean Xubuntu install without Win7.

---

