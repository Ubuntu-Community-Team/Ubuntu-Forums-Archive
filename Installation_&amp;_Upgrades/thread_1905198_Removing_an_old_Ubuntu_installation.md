---
title: "Removing an old Ubuntu installation"
date: 2012-01-06
forum: Installation &amp; Upgrades
---

### Post by cyrus_the_virus on 2012-01-06
Hi,

I have two versions of Ubuntu installed on my laptop (11.04 and 11.10). Since I'm happy with 11.10, I want to remove the old installation and allocate the free space to my new ubuntu installation partition.

This are my partitions:
```

... windows partitions ...
/dev/sda4   extended
/dev/sda7   ext4  Ubuntu 11.10
/dev/sda5   swap
/dev/sda6   ext4  Ubuntu 11.04

```
Note that the order of the partitions is correct, though the numbering of the partitions may suggests otherwise

My questions are:
- Is it safe to simply remove sda6 and allocate the space to sda7 using gparted? I mean, will it work? It seems a bit risky to me.
- How can I repair the bootloader after doing this operation? Is this necessary at all?
- On my desktop I have a similar situation. The difference is that on that machine I first have the 11.04 partition and then the 11.10 partition. Can I perform the same operation in this case? Of course, in this case the complete 11.10 partition will have to be moved in order to use the free space.

Thanks,
Martin

---

### Post by fantab on 2012-01-06
You can use DISK UTILITY tool to format /dev/sda6 (11.04) clean. Or use [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") to delete the partition and if possible merge into another partition.

If you had installed GRUB BOOTLOADER when you had installed 11.10 then I don't think you need to worry about it.

---

### Post by cottfcfan on 2012-01-06
As long as 11.10 controls grub2, you should be fine deleting sda6.
If not run:
```
sudo dpkg-reconfigure grub-pc
``` in a terminal from within your 11.10 installation & follow the prompts.

---

### Post by cyrus_the_virus on 2012-01-06
Thanks for your answers!

What about doing this on my desktop where the 11.04 and 11.10 partition are interchanged? So it looks like this:

```

... windows partitions ...
/dev/sda4   extended
/dev/sda5   swap
/dev/sda6   ext4  Ubuntu 11.04
/dev/sda7   ext4  Ubuntu 11.10

```

---

### Post by cyrus_the_virus on 2012-01-06
I have just successfully completed this on my laptop.

I took the following steps
[LIST]
[*] I first booted into a Ubuntu 11.10 Live CD. Gparted is installed by default in the Live CD.
[*] Using Gparted, I removed sda5 and sda6 and resized sda7. I left some space at the end so I could create a swap partition after sda7
[*] After applying the changes in Gparted I was unable to boot. I got a grub error.
[*] I used [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") within the live cd to fix this. I used the option "Recommended repair" 
[/LIST]

---

### Post by fantab on 2012-01-06
I hope your laptop is functional. The position of SWAP partition doesn't matter. 

Follow the same steps for Desktop as well.

---

