---
title: "wubi installation fails after download complete."
date: 2012-01-24
forum: Installation &amp; Upgrades
---

### Post by moosiecakes on 2012-01-24
Greetings, 

I apologize in advance if this is the wrong forum or has already been covered. 

I've been trying to install the latest 64bit from the ubuntu website along side of my win7 x64 installation with wubi.

Every time i start the installer, It downloads the iso And then quits at the end spitting out an error message about "could not retrieve the required installation files" please refer to log file. I have the log file, but am unsure what i should be looking for.

Here is a snippet of the Log file, Noticeable errors at the end of the log. 

I have deleted the ISO file, Tried re-installing on a different drive and still get the same error. 



01-24 18:20 ERROR  CommonBackend: The md5 of the metalink does match
01-24 18:20 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 367, in get_metalink
  File "\lib\wubi\backends\common\downloader.py", line 79, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1182, in _make_request
URLGrabError: [Errno 14] HTTP Error 404: Not Found
01-24 18:20 DEBUG  TaskList: ### Finished get_metalink
01-24 18:20 DEBUG  TaskList: New task download
01-24 18:20 DEBUG  TaskList: ### Running download...
01-24 18:20 DEBUG  btdownloader: downloading [http://cdimage.ubuntu.com/lucid/daily-live/20120124.1/lucid-desktop-amd64.iso.torrent](http://cdimage.ubuntu.com/lucid/daily-live/20120124.1/lucid-desktop-amd64.iso.torrent) > E:\ubuntu\install\lucid-desktop-amd64.iso
01-24 18:20 ERROR  TaskList: problem getting response info - HTTP Error 404: Not Found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 129, in download
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: problem getting response info - HTTP Error 404: Not Found
01-24 18:20 ERROR  TaskList: Non fatal error problem getting response info - HTTP Error 404: Not Found in task download
01-24 18:20 DEBUG  TaskList: ### Finished download
01-24 18:20 DEBUG  TaskList: New task download
01-24 18:20 DEBUG  TaskList: ### Running download...
01-24 18:20 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lucid/daily-live/20120124.1/lucid-desktop-amd64.iso](http://cdimage.ubuntu.com/lucid/daily-live/20120124.1/lucid-desktop-amd64.iso) > E:\ubuntu\install\lucid-desktop-amd64.iso
01-24 18:20 DEBUG  downloader: Download start filename=E:\ubuntu\install\lucid-desktop-amd64.iso, url=http://cdimage.ubuntu.com/lucid/daily-live/20120124.1/lucid-desktop-amd64.iso, basename=lucid-desktop-amd64.iso, length=722808832, text=None
01-24 18:42 DEBUG  TaskList: ### Finished download
01-24 18:42 DEBUG  downloader: download finished (read 722808832 bytes)
01-24 18:42 DEBUG  TaskList: New task check_iso
01-24 18:42 DEBUG  TaskList: ### Running check_iso...
01-24 18:42 DEBUG  CommonBackend: Checking E:\ubuntu\install\lucid-desktop-amd64.iso
01-24 18:42 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu\install\lucid-desktop-amd64.iso
01-24 18:42 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu\install\lucid-desktop-amd64.iso
01-24 18:42 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20120124.1)
01-24 18:42 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20120124.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
01-24 18:42 DEBUG  Distro: wrong version: 10.04.3 != 10.04.1
01-24 18:42 DEBUG  TaskList: ### Finished check_iso
01-24 18:42 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files
01-24 18:42 DEBUG  TaskList: # Cancelling tasklist
01-24 18:42 DEBUG  TaskList: # Finished tasklist
01-24 18:42 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files




-Moosie

---

### Post by Rubi1200 on 2012-01-24
Hi and welcome to the forums :-)

Try downloading the Desktop ISO and wubi.exe and placing them in the same folder before running the executable file.

Versions here:


[LIST]
[*]For 10.04 use [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)
[*]For 10.10 use [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)
[*]For 11.04 use [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)
[*]For 11.10 use [http://releases.ubuntu.com/oneiri]("http://releases.ubuntu.com/oneiric/")
[/LIST]
The wubi.exe is at the bottom of the pages linked to.

---

### Post by moosiecakes on 2012-01-24
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Try downloading the Desktop ISO and wubi.exe and placing them in the same folder before running the executable file.

Versions here:


[LIST]
[*]For 10.04 use [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)
[*]For 10.10 use [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)
[*]For 11.04 use [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)
[*]For 11.10 use [http://releases.ubuntu.com/oneiri]("http://releases.ubuntu.com/oneiric/")
[/LIST]
The wubi.exe is at the bottom of the pages linked to.


Thanks! Being pretty new to ubuntu, is there a version i should be trying or are they all similar?

---

