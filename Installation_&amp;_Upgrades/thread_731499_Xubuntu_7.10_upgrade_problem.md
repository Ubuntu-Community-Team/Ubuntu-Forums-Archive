---
title: "Xubuntu 7.10 upgrade problem"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by dan22644 on 2008-03-21
I tried this in the Absolute beginner forum, but I think this might be a better place.

I have upgraded from Xubuntu 7.04 to Xubuntu 7.10 by the Update Manager, and I am having several problems that I think may all be related.

Here's the list of things I have noticed so far:

-when I click on Applications -> System -> Add/Remove... or Applications -> System -> Update Manager or Applications -> Settings -> Printing nothing happens, like I don't have permission or something

-I cannot open .pdf or .doc files. When I double click or right click a .pdf and select open with document viewer, nothing happens. When I try to open a .doc file, the Open Office splash screen starts and the progress bar moves to the end, but the splash screen never closes and the document never opens.

-I cannot restart or shutdown. When I click the exit icon in the top right, I have my choice of switch user, log out, restart, or shutdown. If I click restart or shutdown, it asks for my password, which I enter and it then says that the system administrator disallows shutting down with my account. After that the buttons will be grayed out.

-I cannot see my second hard drive /dev/sdb1 in /media where it used to be

daniel@jenni:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    77433299    38716618+  83  Linux
/dev/sda2        77433300    78156224      361462+   5  Extended
/dev/sda5        77433363    78156224      361431   82  Linux swap / Solaris

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01f458c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   160826714    80413326    c  W95 FAT32 (LBA)



Please be explicit with any suggestions as I am a total newb! Thanks!

---

### Post by dan22644 on 2008-03-21
> -I cannot see my second hard drive /dev/sdb1 in /media where it used to be

daniel@jenni:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xea1aa9c7

Device Boot Start End Blocks Id System
/dev/sda1 * 63 77433299 38716618+ 83 Linux
/dev/sda2 77433300 78156224 361462+ 5 Extended
/dev/sda5 77433363 78156224 361431 82 Linux swap / Solaris

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01f458c0

Device Boot Start End Blocks Id System
/dev/sdb1 63 160826714 80413326 c W95 FAT32 (LBA)

I think I fixed my own problem here after searching for a while. It was a simple fix...

    sudo mkdir /media/disc

created the directory I was missing and then...

    sudo mount /dev/sdb1 /media/disc

mounted the disk to the directory:)

Still have the other problems though:mad:

---

### Post by dan22644 on 2008-03-22
OK, so that didn't fix the HD problem. I have to remount after each restart.

Anybody have any ideas here?

---

