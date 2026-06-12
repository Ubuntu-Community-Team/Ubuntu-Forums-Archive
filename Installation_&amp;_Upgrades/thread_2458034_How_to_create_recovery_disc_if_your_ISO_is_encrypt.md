---
title: "How to create recovery disc if your ISO is encrypted and hidden"
date: 2021-02-14
forum: Installation &amp; Upgrades
---

### Post by voxpopili on 2021-02-14
During installation of 20.04 I chose the option of encrypting my drive image.

I just tried to create a recovery image for backup redundancy however the backup tool cannot see my ISO because of course it is encrypted.

The app i tried to use first is from the "Show applications menu  > Startup Disc Creator > Make Startup Disc" 


[B]
ps , i tried the Utilities >> make backups app but it crashed the first two times with error "cannot access network" however once i changed destination from google drive to USB drive it appears to be working ... this works and answers the question[/B]

---

### Post by TheFu on 2021-02-16
Using image-based stuff for backups raises all sorts of issues, requires downtime to create the image, and doesn't allow the same flexibility that using file-based backups all do.  Encryption makes it even more complex.

Using file-based backups, we don't need to backup the OS, since reinstalling from any ISO media is 10-15 minutes on most current hardware, let's us change the networking, storage, and prevents proprietary hardware issues (RAID cards, GPUs) getting into the way.  Plus, with file-based backups, we don't need to backup anything in /usr/ or most of the rest of the OS stuff.  Getting everything from /home/, /etc/ and a list of installed packages (apt-mark showmanual) is almost always sufficient for desktop Ubuntu installs to be recreated in 30 minutes onto 100% new hardware.  

It is also a way add or remove encryption from the new system, if we like, while it cleans up the unneeded applications that may have been left after we learned they didn't do what we needed.

**Recovery Steps:**
[LIST=1]
[*]Perform a fresh install of whatever OS you like
[*]Restore /home/ to storage that can hold everything in the backups
[*]Restore any OS settings from /etc/ in the old system that were manually modified - DO NOT BLINDLY COPY EVERYTHING BACK! I put tags in all the manually modified files, so they are easy to find later, like
```
# :THEFU:
```
[*]Begin restoring any outside data - usually in external disks. It might be possible to just mount those partition to the new machine.  Again, you'll glad you made a copy of /etc/ ... since the old fstab has the mount information. Selectively copy the old fstab lines into the new install /etc/fstab
[*]Feed the list of manually installed applications from the old machine into the new machine:
```
sudo apt-mark manual $(cat pkgs_manual.lst)
sudo apt-get -u dselect-upgrade
```
[*]May want to ensure your backups makes that list of manually installed applications, snap packages, and flatpaks.
[/LIST]
For systems with less than 100G of backup stuff, the restore should be 45 min or less.

File-based backups support versioning, efficient use of storage, no downtime, automation.  I keep 90-180 days of versioned backups for my systems.  YMMV, but for all those versions, typically only 30% extra storage is needed for desktops. For example:
```
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Feb 14 01:15:03 2021         6.77 GB           6.77 GB   (current mirror)
Sat Feb 13 01:15:04 2021         3.33 MB           6.78 GB
Fri Feb 12 01:15:03 2021         1.86 MB           6.78 GB
...
Thu Nov 19 01:15:04 2020         10.7 MB           7.16 GB
Wed Nov 18 01:15:05 2020         78.5 MB           7.23 GB
Tue Nov 17 01:15:04 2020          109 MB           7.34 GB
```
I only run weekly reports about backup sizes, hence why the report is from last Sunday (a few days ago). I get daily backup-completion reports for each system.  Last night for that system:
```
=== Time for Backups to regulus === 
StartTime 1613456104.00 (Tue Feb 16 01:15:04 2021)
EndTime 1613456109.54 (Tue Feb 16 01:15:09 2021)
ElapsedTime 5.54 (5.54 seconds)
TotalDestinationSizeChange 3314920 (3.16 MB)
```
Less than 6 seconds for a backup? Well, yesterday was a holiday here, so I wasn't doing anything on that machine.  Most days, the changes are under 100MB.

The total mounted storage for that system is:
```
$ dft
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-root ext4   17G   14G  2.4G  85% /
/dev/mapper/vgubuntu--mate-home ext4   12G  7.4G  3.8G  67% /home
/dev/vda1                       vfat  511M  7.1M  504M   2% /boot/efi
```
About 30GB of total storage, but only 7.5G needs to be backed up to provide 90 days of daily, versioned, backups.  Why would anyone NOT do that?  Last July, I had to restore that system from backups. Worked, no problem. In early June 2020, I moved from 16.04 --> 20.04 on that box. How does an image-based backup help with that process?
[https://ubuntuforums.org/~#post13928432](https://ubuntuforums.org/~#post13928432) has a simple script.

---

