---
title: "Built a custom computer and can't get ubuntu to install"
date: 2014-08-28
forum: Installation &amp; Upgrades
---

### Post by boss86741 on 2014-08-28
Hey,

I built a computer from and I can't get ubuntu to install. I have tried unetbootin (on my MacBook Pro) for installing it onto my custom computer but when I try to install it, it gives the following error:
No root file system is defined. Please correct this from the partitioning menu.

I have a 64GB SSD and I am installing off of an 8GB USB Flash Drive.

Thanks,

---

### Post by mikewhatever on 2014-08-29
Usually, that means you've selected the manual partitioning option (aka something else), and not assigned anything to the root partition. 
-->[This]("http://askubuntu.com/questions/80455/no-root-file-system-defined-error-while-installing-ubuntu")<-- should help to explain it further.

---

### Post by boss86741 on 2014-08-29
I don't think there actually is a root partition. The drive is completely clean and nothing shows up when I get to the Installation Type screen. And when I hit the +, -, or Change... buttons, it freezes and the installer crashes.

---

### Post by yancek on 2014-08-29
You should see at least /dev/sda on the Installation type screen and be able to highlight it and then click the + and create a partition.  If you can't do that, it might be a bad download.

---

### Post by boss86741 on 2014-08-29
I see a menu under "Device for boot loader installation" that says /dev/sda, which is the only option. There is nothing in the list about the +, -, and Change... buttons and if I hit any of those three buttons, it crashes. I have tried multiple downloads (all of them being 14.04.1).

There could be something up with the drive too. I don't know.

---

### Post by yancek on 2014-08-29
You mention your Macbook Pro in the initial post.  I am right that you used that computer simply to create the bootable flash drive with Ubuntu to use for the installation?  Did you download the unetbootin version for Mac to create the bootable flash?

Your last post seems to indicate that you do not have any partitions formatted or otherwise on the computer, is that correct?
When you boot the computer and enter the BIOS setup, is this hard drive recognized?
Try booting the Ubuntu flash and selecting Try Ubuntu and when you get to a Desktop, open a terminal and run:  sudo fdisk -l(Lower Case Letter L in the command) and post the output and if that doesn't do anything try:  sudo gparted and post the image.

---

### Post by boss86741 on 2014-08-29
> **yancek said:**
> [SIZE=5]1.[/SIZE]You mention your Macbook Pro in the initial post.  I am right that you used that computer simply to create the bootable flash drive with Ubuntu to use for the installation?  Did you download the unetbootin version for Mac to create the bootable flash?

[SIZE=5]2.[/SIZE]Your last post seems to indicate that you do not have any partitions formatted or otherwise on the computer, is that correct?
[SIZE=5]3.[/SIZE]When you boot the computer and enter the BIOS setup, is this hard drive recognized?
[SIZE=5]4.[/SIZE]Try booting the Ubuntu flash and selecting Try Ubuntu and when you get to a Desktop, open a terminal and run:  sudo fdisk -l(Lower Case Letter L in the command) and post the output and if that doesn't do anything try:  sudo gparted and post the image.

1. Yes, I used unetbootin.

2. Yes, that's correct.

3. Yes, it's recognized, but if I try to boot into it, it says "Non-system disk. Press any key to reboot"

4. The output:
> Disk /dev/sda: 8004 MB, 8004304896 bytes
255 heads, 63 sectors/track, 973 cylinders, total 1533408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes/ 512 bytes
Disk identifier: 0x00000000

     Device      Boot  Start    End            Blocks     Id   System
/dev/sda1    *    2         15633407   7816703   b   W95 FAT32

---

### Post by boss86741 on 2014-08-29
> **yancek said:**
> [SIZE=5]1.[/SIZE]You mention your Macbook Pro in the initial post.  I am right that you used that computer simply to create the bootable flash drive with Ubuntu to use for the installation?  Did you download the unetbootin version for Mac to create the bootable flash?

[SIZE=5]2.[/SIZE]Your last post seems to indicate that you do not have any partitions formatted or otherwise on the computer, is that correct?
[SIZE=5]3.[/SIZE]When you boot the computer and enter the BIOS setup, is this hard drive recognized?
[SIZE=5]4.[/SIZE]Try booting the Ubuntu flash and selecting Try Ubuntu and when you get to a Desktop, open a terminal and run:  sudo fdisk -l(Lower Case Letter L in the command) and post the output and if that doesn't do anything try:  sudo gparted and post the image.

1. Yes, I used unetbootin.

2. Yes, that's correct.

3. Yes, it's recognized, but if I try to boot into it, it says "Non-system disk. Press any key to reboot"

4. The output:
```
Disk /dev/sda: 8004 MB, 8004304896 bytes
255 heads, 63 sectors/track, 973 cylinders, total 1533408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes/ 512 bytes
Disk identifier: 0x00000000

     Device Boot           Start          End           Blocks   Id   System
/dev/sda1     *            2          15633407       7816703     b  W95 FAT32
```

---

### Post by fantab on 2014-08-29
The output only shows the 8gb USB drive. It does not show your HDD.
Boot with Live Ubuntu and post the output of:
```
sudo parted -l
```

Open Gparted and post the screenshot of your HDD.
Look for your HDD/SSD in the drop-down device list at the top right corner.

---

