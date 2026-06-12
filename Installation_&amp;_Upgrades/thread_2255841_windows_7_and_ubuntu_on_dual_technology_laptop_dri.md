---
title: "windows 7 and ubuntu on dual technology laptop drive"
date: 2014-12-08
forum: Installation &amp; Upgrades
---

### Post by Jeremy_Fowler on 2014-12-08
Greetings all...
Been away from Ubuntu for a bit  and wanted to get up to speed with it ...
my laptop needs a new hard drive and I figgered why not dual boot.
looking at new drives online tonight and I came across the WD Black model
which has 120GB SSD combined with 1TB regular ...
I thought ... what a brilliant thing to use !
dual boot win7 and Ubu on the SSD, 1/2 for each for speedy booting,  and use the 1 TB for data ...
Q1 - am I crazy to think this is a beautiful idea ?
Q2 - how to accomplish ?
I know I would have to install win7 first and partition the SSD in half for the operating systems
to get the win boot loader happy,
but how to direct the OS's to deposit/read data to/from the 1TB drive ?
would I have to partition the 1TB , 1/2 for NTFS ,  1/2 for Linux file system ??
or am i over thinking this ?

Thanks in advance for any and all help.

J

---

### Post by ajgreeny on 2014-12-08
I don't know anything about using a 50:50 split of the SSD for windows and Ubuntu, but I am sure others will help out with that, but for the other 1TB disk I suggest you format to NTFS and share that between the two OSs as the data drive.  Both OSs can read and write to ntfs without a problem, so that should work fine.

After installing Ubuntu, after Windows, as you said, for ease of dealing with grub, you will need to edit /etc/fstab to make the data drive mount at boot time, and then I would suggest you make soft links from folders in the data drive to the appropriately named folders in your Ubuntu /home folder. Working this way /home can be left within the / (root) partition, as all data will actually sit in the data disk, not in Ubuntu at all, though that is where the data will appear to be.

If you want more info on this partition setup, come back again for details, but as I said, wait for more info on the SSD arrangement.

---

### Post by Darth Riker on 2014-12-08
I don't think that drive is suitable at all actually (happy to be proven wrong though).

Based on what I read here: [http://www.wdc.com/en/products/products.aspx?id=1190#tabs-301](http://www.wdc.com/en/products/products.aspx?id=1190#tabs-301)

> 
Can I dual boot?

    Dual boot is not supported.

And here: [http://www.wdc.com/en/products/products.aspx?id=1190#tabs-304](http://www.wdc.com/en/products/products.aspx?id=1190#tabs-304)

> 
Once the HDD is enabled, will I have two disk volumes?

    Yes. The SSD will be the boot volume, which is typically the C: volume, but the WD Black2install software is required to enable the second volume. The letter for the HDD portion of the drive will depend on how your system is configured. For example, if your DVD/CD drive is configured to show as D: then the WD Black2may appear as drive E:


---

