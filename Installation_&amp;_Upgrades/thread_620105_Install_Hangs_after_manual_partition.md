---
title: "Install Hangs after manual partition"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by libregeek on 2007-11-22
Hello all,
  Today I received the latest ubuntu-7.10 CDROM and started installing (fresh) on my desktop. ( It has already FreeBSD and Fedora 8 installed). Booting the live cd doesn't caused any problem. But when I try to install it on hard disk the installation program simply hangs at step 4. I chose manual partition, and I created new partition for Ubuntu. The newly created partition is listed, but the mouse pointer is simply busy all the time and the "Forward" button is disabled. I waited for about 10 minutes, but nothing happened. On looking to the logs I got the following:

ubuntu@ubuntu:~$ tail -f /var/log/messages 
Nov 22 12:08:47 ubuntu kernel: [ 3640.078425] EXT3 FS on sda7, internal journal
Nov 22 12:08:47 ubuntu kernel: [ 3640.078435] EXT3-fs: mounted filesystem with ordered data mode.
Nov 22 12:08:47 ubuntu migration-assistant: error: /dev/disk/by-label//home1 does not exist.
Nov 22 12:08:47 ubuntu ubiquity: mount: can't find /mnt/migrationassistant/home in /etc/fstab or /etc/mtab
Nov 22 12:08:47 ubuntu ubiquity: 
Nov 22 12:08:47 ubuntu ubiquity: umount: /mnt/migrationassistant: device is busy
Nov 22 12:09:02 ubuntu last message repeated 3 times
Nov 22 12:09:02 ubuntu ubiquity: return: 204: 
Nov 22 12:09:02 ubuntu ubiquity: Illegal number: LABEL=/data
Nov 22 12:09:02 ubuntu ubiquity:

ubuntu@ubuntu:~$ tail -f /var/log/installer/debug 
    return callback(source, debconf_condition)
  File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 179, in process_input
    if not self.process_line():
  File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 112, in process_line
    return self.dbfilter.process_line()
  File "/usr/lib/ubiquity/ubiquity/debconffilter.py", line 363, in process_line
    self.reply(0, data)
  File "/usr/lib/ubiquity/ubiquity/debconffilter.py", line 139, in reply
    self.subin.write('%s\n' % ret)
IOError: [Errno 32] Broken pipe

ubuntu@ubuntu:~$ tail -f /var/log/partman 
parted_server: OUT: -1  27472435200-80023749119 52551313920     pri/log free    /dev/sdb-1


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 440
parted_server: Opening infifo

I am using a Pentium 4 machine(Intel Desktop Board) with 2 SATA hard disks. Please somebosy help me.

regards
libregeek.

---

### Post by Sef on 2007-11-22
Instead of going into the live cd, scroll down the list and highlight check disk.   Check the disk to make sure it is good.

---

### Post by libregeek on 2007-11-22
Sef,
I have tested the CD and no errors are reported.

libregeek.

---

