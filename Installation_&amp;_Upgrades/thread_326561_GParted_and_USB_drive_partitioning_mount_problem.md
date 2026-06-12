---
title: "GParted and USB drive partitioning mount problem"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by louieb on 2006-12-27
I got a 160 gig Western Digital USB drive for Christmas. It has a single fat32 partition.[LIST]
[*]I am trying to make 2 80 gig partitions one ext3 one Risnerfs.
[*]On a P2 400 running Dapper I plugged the drive in and it shows up as an icon on my desktop and Nautilus opens showing the content of the drive.
[*]I close Nautilus and right clicked on it and select the eject option. The drive get unmounted.
[*]I fired up GParted and delete the fat partition, add the two partitions and click apply.
[*]GParted starts working on the disk, then it stops with an error. Ubuntu must think that I have plugged in the drive again because an icon for the drive   shows up as an icon on my desktop and Nautilus opens showing the content of the drive.[/LIST]I used the GParted live CD and finish up but I wonder if anyone has had this problem and how they got around it.

---

### Post by webfootedchicken on 2006-12-30
> **louieb said:**
> I got a 160 gig Western Digital USB drive for Christmas. It has a single fat32 partition.[LIST]
[*]I am trying to make 2 80 gig partitions one ext3 one Risnerfs.
[*]On a P2 400 running Dapper I plugged the drive in and it shows up as an icon on my desktop and Nautilus opens showing the content of the drive.
[*]I close Nautilus and right clicked on it and select the eject option. The drive get unmounted.
[*]I fired up GParted and delete the fat partition, add the two partitions and click apply.
[*]GParted starts working on the disk, then it stops with an error. Ubuntu must think that I have plugged in the drive again because an icon for the drive   shows up as an icon on my desktop and Nautilus opens showing the content of the drive.[/LIST]
I am going to used the GParted live CD and finish up but I wonder if anyone has had this problem and how they got around it.
Your answer is most likely here: [http://ubuntuforums.org/showthread.php?t=327085](http://ubuntuforums.org/showthread.php?t=327085)

HTH

WFC

---

### Post by louieb on 2006-12-31
> **webfootedchicken said:**
> Your answer is most likely here: [http://ubuntuforums.org/showthread.php?t=327085](http://ubuntuforums.org/showthread.php?t=327085)

Thanks that worked for me too. Louie.

---

