---
title: "Can't recover data from Windows 10 Backup"
date: 2020-03-23
forum: Installation &amp; Upgrades
---

### Post by tsidia on 2020-03-23
I am  transitioning from Windows 10 to Ubuntu. Before installing the new OS, I  made a full backup of my windows 10, expecting to extract individual  files from the backup on my Ubuntu. Now I'm stuck with a bunch of .xml  and .vhdx files How do I proceed?


 I have already tried [https://stackoverflow.com/questions/36819474/how-can-i-attach-a-vhdx-or-vhd-file-in-linux/37790474](https://stackoverflow.com/questions/36819474/how-can-i-attach-a-vhdx-or-vhd-file-in-linux/37790474) and failed with the following error message:
 tsidia@tsidia-System-Product-Name:/media/tsidia/SP PHD U3/WindowsImageBackup/DESKTOP-HG1003T/Backup 2020-03-22 140135$ guestmount -a c3c7f9c3-0000-0000-0000-501f00000000.vhdx -i -r /home/tsidia/Desktop/Backup
libguestfs: trace: set_verbose true
libguestfs: trace: set_verbose = 0
libguestfs: create: flags = 0, handle = 0x555f823973b0, program = guestmount
libguestfs: trace: set_recovery_proc false
libguestfs: trace: set_recovery_proc = 0
libguestfs: trace: add_drive "c3c7f9c3-0000-0000-0000-501f00000000.vhdx" "readonly:true"
libguestfs: creating COW overlay to protect original drive content
libguestfs: trace: get_tmpdir
libguestfs: trace: get_tmpdir = "/tmp"
libguestfs: trace: disk_create "/tmp/libguestfsHmRYJu/overlay1.qcow2" "qcow2" -1 "backingfile:/media/tsidia/SP PHD U3/WindowsImageBackup/DESKTOP-HG1003T/Backup 2020-03-22 140135/c3c7f9c3-0000-0000-0000-501f00000000.vhdx"
libguestfs: command: run: qemu-img
libguestfs: command: run: \ create
libguestfs: command: run: \ -f qcow2
libguestfs: command: run: \ -o backing_file=/media/tsidia/SP PHD U3/WindowsImageBackup/DESKTOP-HG1003T/Backup 2020-03-22 140135/c3c7f9c3-0000-0000-0000-501f00000000.vhdx
libguestfs: command: run: \ /tmp/libguestfsHmRYJu/overlay1.qcow2
qemu-img: /tmp/libguestfsHmRYJu/overlay1.qcow2: VHDX image file '/media/tsidia/SP PHD U3/WindowsImageBackup/DESKTOP-HG1003T/Backup 2020-03-22 140135/c3c7f9c3-0000-0000-0000-501f00000000.vhdx' opened read-only, but contains a log that needs to be replayed
To replay the log, run:
qemu-img check -r all '/media/tsidia/SP PHD U3/WindowsImageBackup/DESKTOP-HG1003T/Backup 2020-03-22 140135/c3c7f9c3-0000-0000-0000-501f00000000.vhdx'
Could not open backing image to determine size.
libguestfs: error: qemu-img: /tmp/libguestfsHmRYJu/overlay1.qcow2: qemu-img exited with error status 1, see debug messages above
libguestfs: trace: disk_create = -1 (error)
libguestfs: trace: add_drive = -1 (error)
libguestfs: trace: close
libguestfs: closing guestfs handle 0x555f823973b0 (state 0)
libguestfs: command: run: rm
libguestfs: command: run: \ -rf /tmp/libguestfsHmRYJu

---

### Post by Mark Phelps on 2020-03-23
This is a Linux forum, not a Windows forum.

For help with Win10 stuff, you should post to the right forum:  [https://www.tenforums.com/]("https://www.tenforums.com/")

---

### Post by ipv on 2020-03-23
> **Mark Phelps said:**
> This is a Linux forum, not a Windows forum.

op's question is regarding ubuntu & windows & not just windows.

---

### Post by TheFu on 2020-03-23
> **ipv said:**
> op's question is regarding ubuntu & windows & not just windows.

Proprietary MSFT file formats are hard for Linux to crack.  Expecting Linux or Ubuntu to have some magic method to handle every file created by another OS is asking for disappointment.  Best to never ass-u-me something will work magically. It might, but it probably will not.

When I think of vdhx files, I think of hyper-v virtual machines.

Looks like *guestmount* is extremely buggy.  I'd not heard of it prior to reading this post, but I'm fairly Linux-centric and actively avoid using Windows. I'd look for the guestmount project team, see if they have a bug tracker, check to see if a later version fixes the issue and only submit a bug report if it hasn't already been submitted and/or fixed in the latest version of that software.  Sometimes the team can fix the issue in a few days, but usually months are needed, if a fix ever comes.  These guys are probably all volunteers working on the software as a hobby nights, weekends, rather than going on holiday or spending time with their kids.

But it would probably be more productive to restore the Windows backup, use a different cross-platform backup method, and move to Linux.

---

### Post by ipv on 2020-03-24
> **TheFu said:**
> Expecting Linux or Ubuntu to have some magic method to handle every file created by another OS is asking for disappointment.

i am in complete compliance with you.

i knew it was a bummer when i read this :

> **tsidia said:**
> Before installing the new OS, I  made a full backup of my windows 10, expecting to extract individual  files from the backup on my Ubuntu.

---

