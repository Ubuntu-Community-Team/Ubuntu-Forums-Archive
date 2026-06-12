---
title: "Unable to install NetBook Edition"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by hrblackith on 2010-05-18
Have just tried to use Wubi to install 10.04 on a Samsung N150.

Installation stopped with a "Permission Denied" error. Log file contains following:

[COLOR="Blue"]05-19 23:19 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (10060, 'Operation timed out')>

 in task download
05-19 23:19 DEBUG  TaskList: ### Finished download
05-19 23:19 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-netbook-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-netbook-i386.iso'
05-19 23:19 DEBUG  TaskList: # Cancelling tasklist
05-19 23:19 DEBUG  TaskList: # Finished tasklist
05-19 23:19 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-netbook-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-netbook-i386.iso'[/COLOR]



Very grateful for any help.

---

### Post by darkod on 2010-05-18
You are aware that wubi is not the same as full install on its own partition right?

As for this error, I can't be sure if it will help but you can try running the wubi.exe as administrator. Instead of double-clicking the file, right-click and select Run as Administrator. Sometimes it helps with some windows permissions issues.

---

### Post by hrblackith on 2010-05-20
Thanks for the reply. Have tried the suggestion, but no luck. Will probably try to create a bootable USB.

---

