---
title: "Screen freezes on USB load at syslinux copyright message"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by mwake on 2011-01-13
I have used Universal USB Installer to extract the xubuntu 10.10 iso and install onto a flash drive. I would like to try a live version of xubuntu that boots from a flash drive.

When attempting to boot from the flash drive, the screen effectively freezes after displaying the syslinux / ebios copyright message, with a flashing cursor.

Does anyone know a possible cause or solution?

Information that may be useful:

I am using a 4GB flash drive, formatted as FAT32. I formatted once using the Universal USB Installer, but some files were left on the drive, so I have reformatted it using the option provided by the Windows interface, (and reinstalled xubuntu.)

When I opt to install onto USB with a 2GB persistence file using Universal USB Installer, the installation processes hangs with a dialogue saying there are 0 seconds left to copy, until the dialogue is forcefully shut (and installation appears to be successful). When I select no persistence file, the process does not hang. (I am faced with the same aforementioned problem at boot time, regardless.)

I have not checked the md5sum (though I have no reason to suspect it will fail.) I have downloaded a simple programme which checks a single md5sum against a single file, although I am unsure which file I should check against in the case of xubuntu, and if the md5sum.txt file represents a single md5sum.

I am using Windows Vista on an old Toshiba Satellite.

I am new to using linux, and am very unfamiliar with the the setup and installation procedure.

---

### Post by samirsshah on 2011-01-13
I have a similar problem, after going to SYSLINUX it says "configuration files not found for UI .. "
I also have reformatted my USB drive with FAT32. I have a 2GB USB drive and I have Vista 64. I want to try out 10.10 64 bit.

---

### Post by oldfred on 2011-01-13
Welcome to the forum.

There were some bugs with some versions.

syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)

---

### Post by C.S.Cameron on 2011-01-13
10.10 MD5SUMs [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

or try Unetbootin to install.

---

### Post by mwake on 2011-01-14
Thanks for the replies. They were most helpful.

I tried UNetbootin and was able to start the OS successfully. The md5sum ultimately checked out. (I was also able to crash the system on the first test-run apparently by simply viewing some folder properties. I must be talented..)

I didn't see any persistence option with UNetbootin, however - does one not exist?

I also wonder whether one can install packages on such a live version, or if a full install is required to do this?

I must say my first impressions of xubuntu were marred a little due to my touchpad behaving somewhat unresponsively when clicking (even after toying with the settings), however that's another issue altogether.

---

### Post by C.S.Cameron on 2011-01-14
This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1GB FAT32 partition, (on the left side of the bar).
Created a 2GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext2 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Windows, started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, booted thumbdrive.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

---

### Post by samirsshah on 2011-01-14
I tried "Unetbootin" and also tried "help" workaround as suggested in the link to no avail.

I have Vista 64 with AMD Athlon X2 and 8GB of memory. primary hard drive is IDE 80 GB, archive hard drive is USB 2.0 1 TB.

I wanted to try out Ubuntu 10.10 64 bit on my 2 GB USB drive and then install it.

---

### Post by samirsshah on 2011-01-14
I tried "Unetbootin" and also tried "help" workaround as suggested in the link to no avail.

I have Vista 64 with AMD Athlon X2 and 8GB of memory. primary hard drive is IDE 80 GB, archive hard drive is USB 2.0 1 TB.

I wanted to try out Ubuntu 10.10 64 bit on my 2 GB USB drive and then install it.

---

### Post by samirsshah on 2011-01-14
I tried "Unetbootin" and also tried "help" workaround as suggested in the link to no avail.

I have Vista 64 with AMD Athlon X2 and 8GB of memory. primary hard drive is IDE 80 GB, archive hard drive is USB 2.0 1 TB.

I wanted to try out Ubuntu 10.10 64 bit on my 2 GB USB drive and then install it.

---

### Post by samirsshah on 2011-01-14
I tried "Unetbootin" and also tried "help" workaround as suggested in the link to no avail.

I have Vista 64 with AMD Athlon X2 and 8GB of memory. primary hard drive is IDE 80 GB, archive hard drive is USB 2.0 1 TB.

I wanted to try out Ubuntu 10.10 64 bit on my 2 GB USB drive and then install it.

---

### Post by samirsshah on 2011-01-14
I tried "Unetbootin" and also tried "help" workaround as suggested in the link to no avail.

I have Vista 64 with AMD Athlon X2 and 8GB of memory. primary hard drive is IDE 80 GB, archive hard drive is USB 2.0 1 TB.

I wanted to try out Ubuntu 10.10 64 bit on my 2 GB USB drive and then install it.

---

### Post by samirsshah on 2011-01-15
very sorry for so many posts my Internet was acting up.

---

### Post by C.S.Cameron on 2011-01-15
Try Startup Disk Creator from the Live CD.
I think the Multiple posts are a problem with the site. I see dozens.

---

### Post by samirsshah on 2011-01-16
I do not have Linux to run Startup Disk Creator. I have Windows Vista 64.

---

### Post by C.S.Cameron on 2011-01-16
Extract, (or unrar), usb-creator.exe from the iso.
It will work in Windows.

---

### Post by samirsshah on 2011-01-17
I tried to use it but it does not read an iso file. As it says here...

[http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator](http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator)

The tool is available for Ubuntu (GNOME) or Kubuntu (KDE) and also for Windows starting in Ubuntu 10.10 "Maverick Meeerkat" but only accessible by inserting the Live CD into a CD-ROM drive with Windows running.[1]

It needs a CD drive which I do not have.

---

### Post by C.S.Cameron on 2011-01-17
In windows I use Winiso to open iso's

---

### Post by samirsshah on 2011-01-18
I got USB Creator out of the ISO. But USB Creator requires a CD drive.

---

### Post by danerben on 2011-06-19
[http://ubuntuforums.org/showthread.php?p=10957093#post10957093](http://ubuntuforums.org/showthread.php?p=10957093#post10957093)

---

