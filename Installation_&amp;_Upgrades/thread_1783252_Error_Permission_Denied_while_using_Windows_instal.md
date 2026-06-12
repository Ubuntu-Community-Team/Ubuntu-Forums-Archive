---
title: "Error Permission Denied while using Windows installer"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by drewg123 on 2011-06-15
I am using the windows installer and I receive a Permission Denied. 
 
Here is the error in the log.
 
 
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
DownloadError: Problem connecting to tracker - (10060, 'Operation timed out')
 
06-15 11:13 ERROR TaskList: Non fatal error Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
File "\lib\bittorrent\Rerequester.py", line 96, in fail
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - (10060, 'Operation timed out')
in task download
06-15 11:13 DEBUG TaskList: ### Finished download
06-15 11:13 ERROR TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-i386.iso'
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-i386.iso'
06-15 11:13 DEBUG TaskList: # Cancelling tasklist
06-15 11:13 DEBUG TaskList: # Finished tasklist
06-15 11:13 ERROR root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-i386.iso'
Traceback (most recent call last):
File "\lib\wubi\application.py", line 57, in run
File "\lib\wubi\application.py", line 131, in select_task
File "\lib\wubi\application.py", line 157, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-i386.iso'

---

### Post by bcbc on 2011-06-15
Wubi is using a bittorrent downloader that is being blocked by a firewall somewhere.

You can download the desktop CD ISO yourself to get around this. Just make sure it's a desktop CD ISO not an alternate or dvd and make sure the version matches the same release of wubi.exe (11.04) and then place it in the same folder as wubi.exe before running.

---

