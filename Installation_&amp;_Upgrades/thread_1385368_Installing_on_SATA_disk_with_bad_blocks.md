---
title: "Installing on SATA disk with bad blocks"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by Orlando84 on 2010-01-19
Hi all! My harddrive seems to be with bads. When I was installing Ubuntu on the last stage (98%) when some ttf files were removing occured bug - installation hang up, then I pressed CTRL-ALT-F1 and saw messages like "ata.1 ... media error" a lot of them. How to boot Ubuntu in rescue mode and format HDD partition in a such way, that bad blocks would be surrounded with flags? How then to install Ubuntu so there's no need to format that partitions again. Have I to install in expert mode like in Debian?

---

### Post by recluce on 2010-01-19
> **Orlando84 said:**
> Hi all! My harddrive seems to be with bads. When I was installing Ubuntu on the last stage (98%) when some ttf files were removing occured bug - installation hang up, then I pressed CTRL-ALT-F1 and saw messages like "ata.1 ... media error" a lot of them. How to boot Ubuntu in rescue mode and format HDD partition in a such way, that bad blocks would be surrounded with flags? How then to install Ubuntu so there's no need to format that partitions again. Have I to install in expert mode like in Debian?

Get your disk manufacturer's diagnostic tool, usually a self-booting CD image. Use the diagnostics, if the disk is indeed bad - REPLACE IT, do not install anything to it and do not trust your data to this disk. Alternatively, the manufacturer's diagnostic disk may have a low-level format tool that will mask/replace the bad sectors.

---

### Post by Orlando84 on 2010-01-20
Thank you for your post. I tried to solve the problem with badblocks (linux util), but it hang up on 5%, the disk is really needs to be replaced. And is there an utility to recover data from hdd with erased partition table? Maybe, under Windows? Strange, but windows loads great despite bad blocks

---

### Post by earthpigg on 2010-01-20
> Thank you for your post. I tried to solve the problem with badblocks (linux util), but it hang up on 5%, the disk is really needs to be replaced. And is there an utility to recover data from hdd with erased partition table?  Maybe, under Windows? 

testdisk and photorec. pick your OS. the wiki is very nice.

[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

> 
Strange, but windows loads great despite bad blocks

windows likely mapped them as they went bad.

---

