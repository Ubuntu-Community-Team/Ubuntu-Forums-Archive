---
title: "Getting error while updating the ubundu software update."
date: 2014-08-05
forum: Installation &amp; Upgrades
---

### Post by Rajeevgandhi on 2014-08-05
Hi all,

 I am getting the following error while updating the software. Kindly help me to resolve this issue.
 

   W:Failed to fetch cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)/dists/precise/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
 , W:Failed to fetch cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)/dists/precise/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
 , W:Failed to fetch cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
 , W:Failed to fetch cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
 , W:Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-amd64/Packages](http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-amd64/Packages)  403  Forbidden [IP: 74.125.236.33 80] 
 , W:Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages](http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages)  403  Forbidden [IP: 74.125.236.33 80] 
 , E:Some index files failed to download. They have been ignored, or old ones used instead.



Regards,
Rajeev

---

### Post by Bashing-om on 2014-08-05
Rajeevgandhi; Hi ! Welcome to the forum.

The package manager is looking for the DVD for updates, you do not want this at this time .
In ubuntu Software Center -> software sources disable the check box for the CD/DVD.
Now see what the update manager advises for the updates.

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

