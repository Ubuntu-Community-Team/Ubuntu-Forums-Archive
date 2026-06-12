---
title: "Help with installing? (Tells me I have no space)"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by TerryJGJ on 2012-04-26
Alright, so I'm trying to install with Wubi on a USB. I have an SSD with 10GB left, and a Regular hard drive with plenty of space (Including 10GB of Unallocated space). Now, when I finally get to the screen where I can install, it tells me I don't have 4.4GB of space available. This is where I'm stuck...any and all help appreciated!

---

### Post by Karlchen on 2012-04-26
Hello, TerryJGJ.

> Wubi on a USB USB sticks, SD cards and quite a few USB harddisks come preformatted with a FAT32 filesystem.
FAT32 limits the maximum size of a single file to 4 GB.

Installing Ubuntu with the help of WUBI means that the installer will create a large root.disk file on the selected disk. This root.disk file will hold the Ubuntu filesystem.

Obviously the minimum space needed for a Ubuntu installation is 4.4 GB. As a consequence the root.disk file would be 4.4 GB plus a bit of overhead maybe, but definitely larger than 4 GB.

As a consequence, Wubi cannot perform a Wubi installation on a FAT32 formatted medium, be it a USB stick, an SD card, or a USB harddisk drive. As Wubi always creates the root.disk file on an existing partition, unallocated disk space is of no direct use to Wubi.

--

It is unclear why you want to use Wubi to install Ubuntu on an external USB device. So maybe the bottom of all problem is that you misunderstand what Wubi is all about. So perhaps the first thing to do is reading this article: [**WubiGuide**]("https://wiki.ubuntu.com/WubiGuide")

Kind regards,
Karl

---

### Post by TerryJGJ on 2012-04-26
Well, what I thought I was doing was using my USB (with Wubi) to install Ubuntu onto my SSD. So now I'm all confused. I tried doing it with a CD with the same result (not enough memory)

---

### Post by jadtech on 2012-04-26
wubi is set by default to require 18gb of disk space , that can be changeed how ever it wil need a min of I believe 5 gig to install , windows window though window will allow you to fill your drive full once it gets to nder 10% windows will no longer boot till you clean up and free space on your hard drive .. 

though ubuntu will run with out swap space it normally looks for a swap partition most sgest size should be double your ram ..

ubuntu can run on the USB fairly happy  just like a second hd though it will be temporary  if you  down load a lot of  stuff :)

---

### Post by Karlchen on 2012-04-26
Hello, TerryJGJ.

[Your reply](http://ubuntuforums.org/showpost.php?p=11875097&postcount=3) suggests that I have misinterpreted your initial post or that I have not read it carefully enough, :oops:  'cause I thought you wished to create a Wubi installation on the USB device.

Chances of performing a successful installation as a rule will be best provided:

[LIST]
[*]you make sure that wubi.exe and the downloaded ISO image belong to the same Ubuntu version. - You can do so e.g. by extracting wubi.exe from the ISO file with the help of 7Zip.
[*]you put wubi.exe and the downloaded ISO image next to each other in the same folder on a harddisk. - In this case Wubi will see and use the ISO file in the same folder
[*]you launch wubi.exe by right-clicking it and selecting "run as administrator", i.e. in elevated mode.
[*]you instruct Wubi to install on the "normal" harddisk. I am not sure whether Wubi can perform an installation on an SSD disk.
Maybe it can. If so someone will sure come up and state that (s)he has done so successfully.
Yet with just 10 GB of free space left on the SSD, using the SSD will not be the best choice anyway, as already stated by jadtech.
[/LIST]
In case you keep on experiencing problems, you may wish to post the Wubi installation logfile. It should be created in your %temp% folder. It might hold relevant details on what makes Wubi fail.

Kind regards,
Karl

---

