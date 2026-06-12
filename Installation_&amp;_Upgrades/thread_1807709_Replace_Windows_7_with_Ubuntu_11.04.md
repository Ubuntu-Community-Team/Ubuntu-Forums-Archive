---
title: "Replace Windows 7 with Ubuntu 11.04"
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by hellburst on 2011-07-19
I currently got Windows 7 installed on C: drive and I also got a backup partition which is D: and I want to switch to Ubuntu. Ubuntu's installation gives me an option which is "Replace Windows 7 with Ubuntu". Will this option also erase my backup D: drive?

---

### Post by Mark Phelps on 2011-07-19
When you say Backup, do you mean that "D" is a Recovery partition?

Installers have been known (especially recently) to do wierd things, sometimes because the options presented are confusing.

If you EVER want to restore Win7 to your PC, you should do the following:
1) Download and install the FREE version of Macrium Reflect
2) Once installed, make an image backup of the "C" drive to an external drive.
3) Also, use the option to create a Linux Boot CD in MR
4) When done, restart -- with the Ubuntu CD in the drive.
5) Use the Partition Editor (you may have to install this) to remove the "C" partition (it won't be called that as Linux does not use drive letters).
6) Since you now have an image backup of "C", if you need the space, you can also remove the "D" partition.
7) You can then install Ubuntu and use the entire drive.

---

### Post by 2F4U on 2011-07-19
May I ask why you don't want to keep Windows, at least until you are comfortable with Ubuntu? It would be less work to return just in case you encounter that there is some compelling reason to keep Windows, e.g. the famous application you can't live without and for which there is no replacement on Linux.

---

