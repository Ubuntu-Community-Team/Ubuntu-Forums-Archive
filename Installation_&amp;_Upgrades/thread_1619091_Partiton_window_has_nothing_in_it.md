---
title: "Partiton window has nothing in it"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by xnols on 2010-11-11
When i go to install ubuntu 32bit i get to the partition screen and no drives show up. Not sure what to do.

Im using a usb drive with the image loaded to it. i have a Gigabyte GA-P55A-UD3 motherboard. A ATI Radeon HD 5830 graphics card and a  i7 875K Processor.

Thanks for the help.

---

### Post by Quackers on 2010-11-11
Welcome to UF.
Is there any free space on the hard drive to install in?

---

### Post by dino99 on 2010-11-11
Little help about installation:

[http://ubuntuforums.org/showpost.php?p=10098299&postcount=2](http://ubuntuforums.org/showpost.php?p=10098299&postcount=2)

---

### Post by sikander3786 on 2010-11-11
Hi. Welcome to the forums :popcorn:

> i get to the partition screen and no drives show up.

From that I understand that Ubuntu installer is unable to detect your HDD at all. If thats the case, go to Appications > Accessories > Terminal and post the output of this command.

```
sudo fdisk -l
```

If it doesn't list any drives, try plugging your Sata HDD to the other Sata controller on your Motherboard. They would look like 2 different sets of ports. Try the other coloured port and retry to see if it is detected now.

---

### Post by xnols on 2010-11-11
I did the fdisk. And there is enough room, i have 1tb 

```
Disk /dev/sdf: 8021 MB, 8021606400 bytes
255 heads, 63 sectors/track, 975 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2341b5aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1         974     7823623+   b  W95 FAT32
```

---

### Post by sikander3786 on 2010-11-11
Ok. It does see your HDD at least.

From the Ubuntu installer, if you select "Specify partitions manually (advanced), can you see your existing partition i.e, sdf and some unallocated space?

---

### Post by xnols on 2010-11-11
> **sikander3786 said:**
> Ok. It does see your HDD at least.

From the Ubuntu installer, if you select "Specify partitions manually (advanced), can you see your existing partition i.e, sdf and some unallocated space?

I didnt see any of those options on the screens. Here is a screen shot. That drop down menu doesnt drop.

<screenshot is now a thumbnail>

---

### Post by sikander3786 on 2010-11-11
Sorry I mis-posted in my last post. It doesn't see your HDD at all.

Did you try switching to the other Sata controller?

Ubuntu is not good at Marvell sata controllers till now.

---

### Post by xnols on 2010-11-11
I just moved the sata into 3 different ports still nothing.

---

### Post by sikander3786 on 2010-11-11
I have seen your motherboard here.

[http://www.gigabyte.com/products/product-page.aspx?pid=3439#sp](http://www.gigabyte.com/products/product-page.aspx?pid=3439#sp)

It has got 6Gb/s Marvell controller and also the standard 3Gb/s X 6 sata ports. Your HDD should work with any of the Sata1, Sata2, Sata3 or Sata4 ports atleast.

There should be some settings for Raid and ahci in the Bios menu. Try turning them off and try again.

---

### Post by xnols on 2010-11-11
The setting was PCH SATA control mode and it is set to IDE, but it is still not working

---

### Post by xnols on 2010-11-11
I just switched all my setting to ahci and it is working now. Thanks for the help.

---

### Post by sikander3786 on 2010-11-12
> **xnols said:**
> I just switched all my setting to ahci and it is working now. Thanks for the help.
Thats what I was talking about :-)

Glad to hear it's sorted.

Please mark your thread solved using Thread Tools near the top of the page.

Happy Ubuntu-ing!

---

### Post by srs5694 on 2010-11-12
Please post the output of "sudo fdisk -lu". Note the extra "u" compared to the command you posted earlier. This extra option changes the output from the imprecise cylinder values to the much more precise sector values. It doesn't look like there's a problem with mis-sized partitions based on your earlier output, but getting sector-precise values will make that certain.

---

