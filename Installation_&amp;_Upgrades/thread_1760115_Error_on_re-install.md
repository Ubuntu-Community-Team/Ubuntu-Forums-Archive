---
title: "Error on re-install"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by mooseman123 on 2011-05-16
I am attempting to re-install Ubuntu on my system. I originally used the wubi installer. I lost the files when I removed the used partition. I am using windows 7, and had ubuntu in the boot menu. Now, when I attempt to use the wubi installer again, it says that there it is already present, and must be un-installed first. When I do this, I receive an error. (The first attached image). How can I resolve this?

Thanks!

---

### Post by Dreigo42 on 2011-05-16
You could try Revo Uninstaller. I have found that it helps deal with stubborn un-installation attempts.
try uninstalling it with Revo, you will probably still get the same error but then Revo will scan the registry and hard drive for anything left over. It sounds like the files needed to complete the uninstall process were lost but the registry entries remain. Delete those using Revo and try wubi again. I would bet that would do the trick.

---

### Post by mooseman123 on 2011-05-17
What is Revo?

---

### Post by Rubi1200 on 2011-05-17
Hi and welcome to the forums mooseman123 :)

First, try using the instructions to manually uninstall Wubi from here:
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

If that still fails when you try and reinstall, post the log mentioned in the error message.

Please wrap with code tags when posting the log as it makes for easier reading (highlight all text and click on the # icon on the toolbar).

Thanks.

---

### Post by mooseman123 on 2011-05-17
Thanks! I completed the uninstall successfully now. I added the ubuntu OS as an OS with bcdedit in Windows 7. I am now attempting to re-install from the original wubi installer. I now receive an "permission denied" error. I am running the installer as admin. :confused:

The log file shows this at the end:
```
05-17 08:42 DEBUG  TaskList: ### Finished get_metalink
05-17 08:42 DEBUG  TaskList: New task download
05-17 08:42 DEBUG  TaskList: ### Running download...
05-17 08:42 DEBUG  btdownloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent > U:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-17 08:42 ERROR  TaskList: Traceback (most recent call last):
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


05-17 08:42 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (10060, 'Operation timed out')>

 in task download
05-17 08:42 DEBUG  TaskList: ### Finished download
05-17 08:42 ERROR  TaskList: [Errno 13] Permission denied: u'U:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'U:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
05-17 08:42 DEBUG  TaskList: # Cancelling tasklist
05-17 08:42 DEBUG  TaskList: # Finished tasklist
05-17 08:42 ERROR  root: [Errno 13] Permission denied: u'U:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'U:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
```

Thanks!

(U: is a 30gb partition) (I have no working CD/DVD disk drive at the moment)

---

### Post by Rubi1200 on 2011-05-17
Thanks for the log file and additional information.

The error mentions the U drive which would normally be associated with a dynamic disk in Windows.

Normally, it is not possible to install Ubuntu, whether with Wubi or otherwise, to a dynamic disk.

Please confirm for us whether the disks are dynamic by going to the Disk Management tool in Windows and looking whether the disks are labeled as Basic or Dynamic.

Meantime, I will send a message to forum member bcbc, an expert on Wubi installs, asking for confirmation about this.

Please hang in there until one of us responds (be aware of time-zone differences).

Thanks.

---

### Post by bcbc on 2011-05-17
This particular problem appears to be the bittorrent downloader Wubi uses. It requires access to the windows firewall (for the python runtime pyrun.exe) and also make sure there are no other firewalls blocking it e.g. corporate. For alternatives on installing see the [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide#Installation")

As Rubi1200 stated, if you have dynamic drives then you should not install Wubi.

---

### Post by mooseman123 on 2011-05-17
I don't see a label for dynamic or basic disks. I saw somebody else saying they're only in ultimate and enterprise versions of Windows; if that's correct, I can't have them.

I disabled the firewalls, and still no luck. Wubi creates a directory for Ubuntu on the U drive, but the iso file is 0kb. Can I manually download it and restart wubi?

In my previous post I meant no CD/DVD drive; I edited that just now.

Thanks again for your help!
-Mooseman

---

### Post by bcbc on 2011-05-17
From the wubi guide:
> ...download both Wubi.exe and the required Desktop ISO from the same location (the release has to match):

For 10.04 use [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)
For 10.10 use [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)
For 11.04 use [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)
Copy both files into the same folder on the machine with no Internet access and run the Wubi executable.

Hopefully that does the trick

---

### Post by mooseman123 on 2011-05-17
Thanks! I'll try this first thing tomorrow morning.

---

### Post by mooseman123 on 2011-05-18
Just completed install! Thanks for all your help: bcbc and rubi1200! I just needed to download the iso first as bcbc stated. :)

---

### Post by Rubi1200 on 2011-05-18
> **mooseman123 said:**
> Just completed install! Thanks for all your help: bcbc and rubi1200! I just needed to download the iso first as bcbc stated. :)
Excellent! Glad you got thing sorted out and can enjoy Ubuntu on your computer :-)

If you need more help with anything, feel free to ask.

Please also mark this thread Solved using the Thread Tools near the top of the page.

---

