---
title: "Install 19.04 Server on Intel NUC"
date: 2019-10-23
forum: Installation &amp; Upgrades
---

### Post by david_j on 2019-10-23
I'm trying to install 19.04 server on an Intel NUC8i5BEH with a Samsung 500GB NVME SSD in the M.2 slot but installation fails when trying to install on this drive.

The BIOS recognises the drive and the installer also recognises this drive. The installer log shows the drive under "merged config" as 'wwn':'eui.0025385791b3bdf4' with path '/dev/nvme0n1'. 

At the stage in the install process where the installer recognises available drives I am offered "eui.0025385791b3bdf4 local disk 465.761G" which is the Samsung SSD. The installation progresses through asking for login ID etc, but when pressing "Done" to begin the install, it fails.

The log shows that the install process failed because "curtin" cannot find the drive:
start: cmd-install/stage-partitioning/builtin/cmd-block-meta: curtin command block-meta
get_path_to_storage_volume for volume disk-nvme0n1
devsync for /dev/disk/by-id/wwn-eui.0025385791b3bdf4 
Running command ['partprobe', 'wwn-eui.0025385791b3bdf4'] with allowed return code [0,1] (capture=false)
Error: Could not stat device /dev/disk/by-id/wwn-eui.0025385791b3bdf4 - No such file or directory

An ls on /dev/disk/by-id shows
nvme-eui.0025385791b3bdf4 and nvme-samsung_SSD_970 .......

So the installer recognises the drive as eui.0025385791b3bdf4 early in the process, knows it is an nvme drive, yet goes looking for it under /dev/disk/by-id as WWN-eui.0025385791b3bdf4.

Why is this and how can I get the installer to look for the drive using the correct name under /dev/disk/by-id? 

The installer seems to incorrectly add WWN to the ID of the drive rather than NVME which the system uses to identify the drive.

All assistance greatly appreciated.

---

### Post by TheFu on 2019-10-23
Sorry, I have nothing helpful, except ... 

Support for 19.04 ends in about 3 months. Do you really want to install that release at this point? 
19.10 support will end in June/July 2020, so if you really want to setup a server, then 18.04 is the last LTS with support until 2023 around June.  If you've already tried 18.04 and ran into HW issues, then 19.10 would be the next stop, not 19.04, at least not on this date.

Ubuntu isn't like other Linux distros. Support periods for every release are pretty well known.  LTS is even years, April.

Where does /dev/disk/by-id/wwn-eui.0025385791b3bdf4, a symbolic link, point?

---

### Post by david_j on 2019-10-23
Thanks TheFu but I originally tried 18.04 LTS (my preference for LTS) but it also failed at the same install point with the same errors. I had hoped that the installer for 19.04 would have been better. It wasn't. 
I've since had success installing Debian, so this is an issue with Ubuntu and not my hardware (I think).

---

### Post by TheFu on 2019-10-24
> **david_j said:**
> Thanks TheFu but I originally tried 18.04 LTS (my preference for LTS) but it also failed at the same install point with the same errors. I had hoped that the installer for 19.04 would have been better. It wasn't. 
I've since had success installing Debian, so this is an issue with Ubuntu and not my hardware (I think).

Debian stable or testing or bleeding?
Regardless, today, if you don't want the 18.04 LTS, then 19.10 is the release that should be installed.

Where does that symlink point, as previously asked?

---

### Post by david_j on 2019-10-24
Using Debian 10 stable and the symlink [COLOR=#000000]/dev/disk/by-id/wwn-eui.0025385791b3bdf4[/COLOR] doesn't exist, that is the problem. The installer should be looking for [COLOR=#000000]/dev/disk/by-id/eui.0025385791b3bdf4[/COLOR]

---

### Post by TheFu on 2019-10-24
In every Ubuntu installer I've seen, UUIDs are used, unless LVM is being deployed.
I've not seen WWN links used, ever, but I've never deployed SAN with Linux.

Debian isn't Ubuntu, however.

---

### Post by ubfan1 on 2019-10-24
Have you checked that the firmware on you NUC is the latest?  Do that before anything else.

---

### Post by ubushredder on 2019-11-01
Had the same problem as david_j on a NUC8i5BEK. Also a non-existing /dev/disk/by-id/wwn-eui.*, but /dev/disk/by-id/nvme-eui.* did exist. Managed to properly install by creating the missing symlink manually just prior to hitting continue on the screen to setup LVM. I got it to work on 19.10 this way. Did not verify it with 18.04.

---

