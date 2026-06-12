---
title: "Ubuntu W&#304;ndows Installer problem"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by yozden on 2011-01-10
Hi i want to install ubuntu 10.04 via windows installer.
 
My os is windows7 64 bit edition.
 
I got than warning that installation has an error, for detail you can see the log file.
 
Here is the log file.
 
 
01-10 02:41 DEBUG TaskList: ### Finished download
01-10 02:41 ERROR TaskList: [Errno 13] Permission denied: u'E:\\ubuntu\\install\\ubuntu-10.04.1-desktop-amd64.iso'
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'E:\\ubuntu\\install\\ubuntu-10.04.1-desktop-amd64.iso'
01-10 02:41 DEBUG TaskList: # Cancelling tasklist
01-10 02:41 DEBUG TaskList: # Finished tasklist
01-10 02:41 ERROR root: [Errno 13] Permission denied: u'E:\\ubuntu\\install\\ubuntu-10.04.1-desktop-amd64.iso'
Traceback (most recent call last):
File "\lib\wubi\application.py", line 56, in run
File "\lib\wubi\application.py", line 130, in select_task
File "\lib\wubi\application.py", line 156, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'E:\\ubuntu\\install\\ubuntu-10.04.1-desktop-amd64.iso'
 
How can i achieve this problem.
 
thank you

---

### Post by Bucky Ball on 2011-01-10
> **yozden said:**
> Hi i want to install ubuntu 10.04 via windows installer.
 
My os is windows7 64 bit edition.
 
I got than warning that installation has an error, for detail you can see the log file.
 
Here is the log file.
 
 
01-10 02:41 DEBUG TaskList: ### Finished download
01-10 02:41 ERROR TaskList: [Errno 13] Permission denied: u'E:\\ubuntu\\install\\ubuntu-10.04.1-desktop-amd64.iso'
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'E:\\ubuntu\\install\\ubuntu-10.04.1-desktop-amd64.iso'
01-10 02:41 DEBUG TaskList: # Cancelling tasklist
01-10 02:41 DEBUG TaskList: # Finished tasklist
01-10 02:41 ERROR root: [Errno 13] Permission denied: u'E:\\ubuntu\\install\\ubuntu-10.04.1-desktop-amd64.iso'
Traceback (most recent call last):
File "\lib\wubi\application.py", line 56, in run
File "\lib\wubi\application.py", line 130, in select_task
File "\lib\wubi\application.py", line 156, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'E:\\ubuntu\\install\\ubuntu-10.04.1-desktop-amd64.iso'
 
How can i achieve this problem.
 
thank you

If you're putting a command in a terminal you need to put 'sudo' in front of it.

```
sudo apt-get install package_name_goes_here
```If you have free space I would just remove Wubi from Windows and do a proper dual-boot install from a Ubuntu installation CD. Easier and less problematic. You can even boot from the installation CD, run Ubuntu from the disk, and on the desktop there should be an icon; 'Install Ubuntu' or something to that effect. ;)

Use manual partitioning when you get to that part of the install and just don't touch the Windows partition (clearly visible as an NTFS partition). Create these three partitions, they are default partition names in the installer:

/ = Ubuntu, 20Gb more than enough;
/home = your personal data and settings, big as you like;
/swap = 2Gb or 4Gb if you intend to hibernate the machine.

All EXT4 except /swap which takes care of itself. On reboot you should be looking at a list with your Ubuntu install and your Windows install at the bottom of the list.

Before attempting a dual-boot ***back-up anything important*** (personal data)!!!

It's pretty easy to set up a dual-boot but we all have a brain melt now and then! 

Your Wubi install was running fine I take it?

---

