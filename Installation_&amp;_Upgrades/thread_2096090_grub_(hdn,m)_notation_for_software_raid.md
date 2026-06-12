---
title: "grub (hdn,m) notation for software raid"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by Viglen on 2012-12-19
I'm trying to install grub on a seperate partition that doesn't overwrite the Windows boot manager. The catch is that I'm using software raid and don't understand how the grub notation carries over. 

Below is my partition layout from the debian installer. I used an LVM called AD. I want to put Grub2 on the 512 MB partition number 5. How do I tell grub2 that using the grub notation (hdn,m).


[HTML]
<pre>
debian Partition disks window	
	
	
	Configure Encrypted volumes

LVM VG AD, LV home - 5.2 GB Linux device-mapper (linear)

	> #1					5.2 GB				ext3
	
LVM VG AD, LV home - 10.0 GB Linux device-mapper (linear)

	> #1					10.0 GB				ext3
Serial ATA RAID isw_diidgiggif_Volume0(stripe) - 256.1 GB Linux device-mapper (striped)

	> #5	logical			511.7 MB			ext3
	> #6	logical			17.2  GB		K   lvm
	> #1	primary			104.9 MB   B		ntfs
	> #2	primary			120.9 GB 	  		ntfs
	> 	primary			117.3 GB 	  		FREE SPACE

Serial ATA RAID isw_diidgiggif_Volume0p1(partition #p1) - 104.9 MB Linux device-mapper (linear)

	> #1					104.9 MB			ntfs

Serial ATA RAID isw_diidgiggif_Volume0p2(partition #p2) - 120.9 GB Linux device-mapper (linear)

	> #1					104.9 MB			ntfs

Serial ATA RAID isw_diidgiggif_Volume0p3(partition #p3) - 17.7 GB Linux device-mapper (linear)

	> #1	primary			511.7 MB   			ext3
	> #5	logical			17.2 GB   		K	lvm

Serial ATA RAID isw_diidgiggif_Volume0p5(partition #p5) - 511.7 MB Linux device-mapper (linear)

	> #1					511.7 MB			ext3
Serial ATA RAID isw_diidgiggif_Volumep6(partition #p6) - 17.2 GB Linux device-mapper (linear)

	Undo changes to partitions
	Finish partitioning and write changes to disk

	</pre>[/HTML]

Thanks a lot for any help, I've been stuck on this for days.

---

