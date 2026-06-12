---
title: "Can't install Wubi - log file"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by Paul4763 on 2010-10-08
**Can't install Wubi - log file** 			
 			 			 		   		 		 		I can't install Wubi, I keep getting an error, here is where the log file starts saying "ERROR":

10-08 14:20 DEBUG  TaskList: ### Finished get_metalink
10-08 14:20 DEBUG  TaskList: New task download
10-08 14:20 DEBUG  TaskList: ### Running download...
10-08 14:20 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.04.1/u...64.iso.torrent]("http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.iso.torrent") > C:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.iso
10-08 14:46 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (10060, 'Operation timed out')>

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (10060, 'Operation timed out')>


10-08 14:46 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (10060, 'Operation timed out')>

 in task download
10-08 14:46 DEBUG  TaskList: ### Finished download
10-08 14:46 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04.1-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04.1-desktop-amd64.iso'
10-08 14:46 DEBUG  TaskList: # Cancelling tasklist
10-08 14:46 DEBUG  TaskList: # Finished tasklist
10-08 14:46 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04.1-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04.1-desktop-amd64.iso'

---

### Post by Frogs Hair on 2010-10-08
Is this happening after the Ubuntu download or is the Wubi installer failing to start ?

---

### Post by Paul4763 on 2010-10-09
After the Ubuntu download

---

### Post by Paul4763 on 2010-10-10
Bump

---

### Post by Mark Phelps on 2010-10-11
Read the Release Notes on 10.10.  They clearly indicate installation problems with Wubi.

You can find them by going to distrowatch.com, looking in the center section for the Ubuntu 10.10 announcement, and clicking on the Release Notes link.

---

### Post by btamxx on 2010-11-23
I tried 5 times to install Ubuntu 10.10 and 10.04 32 bit and 64 bit using wubi on the same drive, not C:, and they all failed. So finally I tried to install it on drive C: and it worked. Apparently, there are some drives/partitions wubi simply can't stand/tolerate.

Oops. I just examined the drive and it is screwed up. It is a 800 GB drive but windows reports that it is a 3+ terrabyte. Problem solved.

---

