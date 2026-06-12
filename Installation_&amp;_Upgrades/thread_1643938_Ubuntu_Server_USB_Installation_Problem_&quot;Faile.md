---
title: "Ubuntu Server USB Installation Problem &quot;Failed to determine codename for release&quot;"
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by alexpolt on 2010-12-12
Hi people
Tried to install Ubuntu Server amd64 10.10 
Downloaded ubuntu-10.10-server-amd64.iso
Made a usb with the help of usb-installer

Ran into problem "Failed to determine codename for release"
on the package installation phase

Was fighting for long hours and found out that
the thing wasn't installing properly because of a script problem in
/var/lib/dpkg/cdrom-detect.postinstall

Steps:
0. make sure you are in installation main menu stuck on step "mount cdrom ..."
1. go to console by ctrl-alt-f2
2. mkdir /usb
3. mount -t vfat /dev/sd? /usb
4. okay, here you can mount either the usb stick itself or the original ISO image ( you should copy it beforehand )
i found out that its best to mount original ISO: mount /usb/....iso /cdrom
5. edit /var/lib/dpkg/cdrom-detect.postinstall :
   comment line with "mount | grep ...."
   comment "exit 0" at the end of the next if block
   change "fi" after "exit 0" to "else"
   go to "done" string corresponding to "while" block and
   append on a new line "fi" ( so that we have good if...else..fi block)
6. go back to installation menu by pressing ctrl-alt-f1


so the problem was in the script that exited prematurely and
didnt update important "cdrom/codename" variable in debconf database

---

### Post by justin.cherniak on 2011-03-12
I ran into this issue with the 10.10 alternate installer.  Note, at least on that disk, the file to edit is /var/lib/dpkg/**info/**cdrom-detect.postinstall.

Thanks for the help!

---

### Post by tomryantx on 2011-11-16
> **justin.cherniak said:**
> I ran into this issue with the 10.10 alternate installer.  Note, at least on that disk, the file to edit is /var/lib/dpkg/**info/**cdrom-detect.postinstall.

Thanks for the help!


I have run into the same problem ("Failed to determine codename of the release" in trying to install Ubuntu Studio 11.10. I believe the first appearance of the difficulty is at "Retrieving dmraid-udeb" where I am told there is "a problem reading data from the CD-ROM. Please make sure it is in the drive . . . ." The installation continues through the partitioning sequence, but then gives me the "Failed to determine . . . cde name" message. I have found the work-around here, but I need more help to make the change in the script (if that's what I should do).

Any help or advice would be much appreciated.

Thanks,

Tom

---

