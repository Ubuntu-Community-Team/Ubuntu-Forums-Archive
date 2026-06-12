---
title: "Long format"
date: 2016-09-02
forum: Installation &amp; Upgrades
---

### Post by cerasus on 2016-09-02
I tried to fully format my HD from an Ubuntu Live CD (as there were some kernel problems) before installing the latest Ubuntu version from scratch but i got some errors. So I have deleted the partition that contained all my data in gparted, so  the disk is formatted, but the process only took a few seconds so I  assume it was just a quick format. Is there any reason to get worried because of this? Is installing on a quick-formatted HD somehow different from installing on a long-formatted one? Hypothetically speaking do I have any chance of performing a long format (without any errors to kill the process as they did when I did the Live CD thing) from a version that's installed on the HD? Why did I get those errors?

---

### Post by Dennis N on 2016-09-02
"Quick format", "long format", "full format" are not terms I have seen used with Linux tools like gparted - just "format". Where did you see these options in Linux tools?

When you create a partition yourself and select the file system to use, the partition is formatted in that action.

To set up a disk for use with Ubuntu, you need to 1) create a partition table (either GPT or MSDOS) on the disk; 2) Create needed partitions with the correct file systems (formats) for the installation; these tasks can be accomplished pre-installation with the gparted tool on the live CD, or let the installer create the needed partitions.

---

### Post by cerasus on 2016-09-04
> **Dennis N said:**
> "Quick format", "long format", "full format" are not terms I have seen used with Linux tools like gparted - just "format". Where did you see these options in Linux tools?

When you create a partition yourself and select the file system to use, the partition is formatted in that action.

To set up a disk for use with Ubuntu, you need to 1) create a partition table (either GPT or MSDOS) on the disk; 2) Create needed partitions with the correct file systems (formats) for the installation; these tasks can be accomplished pre-installation with the gparted tool on the live CD, or let the installer create the needed partitions.

I can't remember. I guess it was somewhere in a dropdown menu where you could select the erase and format type. Just above that "ext2/ext3/ext4/fat32" thing. Or in the side bar when you right clicked 318 GB Volume. But it was there only when I booted from the Live CD. It's not there anymore. Anyway. I reinstalled and this is how my partitions look like at this moment: 

[[IMG]http://imagizer.imageshack.us/v2/640x480q90/921/I4wxdw.png[/IMG]]("https://imageshack.com/i/plI4wxdwp")

What's the difference between a short and a long format? By "long format" one understands replacing the information with zeroes. At least that's how the option was explained.

I think I did something wrong. Why has the 3rd partition appeared? It wasn't there before I formated. And my HD was 320 or 318 GB and it got smaller now.

---

### Post by Impavidus on 2016-09-04
By filling the drive with zeros you make sure that the files on the drive cannot be recovered by file recovery software. Useful if you want to give the harddrive to someone else. It can also prevent confusion during partitioning and filesystem recovery and similar scenarios. But usually it shouldn't matter.

The extra partition that you got is an extended partition. It's a container for the swap partition. Extended partitions are a workaround for the 4 primary partition limit on MBR partitioned hard drives. It was created automatically when the swap partition was created as a logical partition.

Your hard drive is 320.07 GB, which is the same as 298.09 GiB. 1 GiB = 1.0737 GB. Choosing your prefixes as a power of 2 often gives rounded numbers in computer stuff, but the downside is that, contrary to all other units we use in daily life (with a few exceptions), the prefixes are not a power of the base of our numeral system, leading to inconvenient unit conversions.

I don't think you did anything wrong.

---

### Post by cerasus on 2016-09-05
> **Impavidus said:**
> By filling the drive with zeros you make sure that the files on the drive cannot be recovered by file recovery software. Useful if you want to give the harddrive to someone else. It can also prevent confusion during partitioning and filesystem recovery and similar scenarios. But usually it shouldn't matter.

The extra partition that you got is an extended partition. It's a container for the swap partition. Extended partitions are a workaround for the 4 primary partition limit on MBR partitioned hard drives. It was created automatically when the swap partition was created as a logical partition.

Your hard drive is 320.07 GB, which is the same as 298.09 GiB. 1 GiB = 1.0737 GB. Choosing your prefixes as a power of 2 often gives rounded numbers in computer stuff, but the downside is that, contrary to all other units we use in daily life (with a few exceptions), the prefixes are not a power of the base of our numeral system, leading to inconvenient unit conversions.

I don't think you did anything wrong.

Yeah....I partly understand what do you mean. But what do you mean by prefix? GB over GiB? The big picture is about how much subdivisions a single unit contains. I think....I got it....

---

### Post by Impavidus on 2016-09-05
By prefix I mean G- or giga-, standing for 1,000,000,000 times the base unit, versus Gi- or gibi-, standing for 1,073,741,824 times the base unit. The base unit is in this case byte.

---

### Post by autocrat on 2016-09-05
[https://en.wikipedia.org/wiki/Gibibyte](https://en.wikipedia.org/wiki/Gibibyte)
HD vendors often label in decimal, whereas Linux reads in Binary.

---

