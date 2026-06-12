---
title: "Ubunut didn`t recognized my RAID-0 Array. And I lost everything"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by Slashrk on 2008-05-17
Buenas,

A little history....
I`ve got 2x500GB seagate, and put them on a RAID-0 Array. Everything was perfect. I Have installed Windows Vista in a 100GB partition, got another one of 750Gb for files, and the rest i was planning to install any linux distro. Googling, I discovered that it`s not every distro which work with Sata-Raid. Actually, only openSuse and Fedora. But I prefer Debian-like distros, so i searach for a solution (google again! rolleyes.gif), and saw that if i boot from a live cd, and install a certain package i could install it in the RAID Array, and so i did... Boot with Ubuntu LiveCd, installed the package dmraid, and with the partition editor, i`ve saw the array...the windows, the file partition, and the destinated to the linux system. So i tried to format the linux one. apparently everything ok, no errors... But when the partition tables refreshed, i`ve yelled very bad words.... it`s erased all the partitions, and the format got the entire 1TB array!
I don`t think it did a full format, because it was very quick (not more than a few seconds...), and after this stupid action of mine... i just have stopped everything... hoping that it will be possible to recover my files, something about 300Gb ...or even if its possible to revert the formatting...since the partition manager just rewrote the partition table, and i didn`t write any data yet.
Maybe if i boot windows from another harddrive, there will be a way to access the files on the NTFS partition?

Well, thanx in advance... and i appreciate any suggestions...


=======

EDIT:
Just in case someone want to know what happens, i've managed to solve this problem (almost a nightmare for me :lolflag:).
Put a IDE hdd as master, and boot windows from it, with the raid array as slave got a program called R-Studio, which scanned the entire hdd, and recognized the lost partitions, and the data was intact! So i could recover everything i want.
Farewell

---

