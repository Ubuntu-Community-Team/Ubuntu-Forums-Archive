---
title: "Windows 7 Denial Error"
date: 2011-11-30
forum: Installation &amp; Upgrades
---

### Post by alchemist330 on 2011-11-30
my laptop has a broke cd drive and the bios pass cant be reset without sending it back...i have no patience for that.

Each time i try to install ubuntu beside windows it gets denied by windows...wont let it access the directory i guess....any suggestions?

---

### Post by Rubi1200 on 2011-11-30
Is this a Wubi install? Have you tried running as Administrator?

Let us know exactly what you have done so we can rule out the various possibilities.

Thanks.

---

### Post by alchemist330 on 2011-11-30
i have my usb cd drive in.
im running off the cd an im installing inside windows or well beside.

It gets to extracting files from G:\
[ATTACH]208275[/ATTACH]
I believe the attachment works. but if not


An Error Occured:

Permission Denied

For More Information, please see the log file:
c:\users\admin-1\appdata\local\temp\wubi-11.04-rev211.log

---

### Post by Mark Phelps on 2011-11-30
Rubi1200 suggested running the install as Administrator.  If this is a permissions problem, that should get around it.

Also, you need to look at that log and tell us what's in the last few lines.  That way, we will know why it's failing.

---

### Post by alchemist330 on 2011-11-30
cant find the log

---

### Post by alchemist330 on 2011-11-30
11-30 17:59 DEBUG  TaskList: ## Finished copy_installation_files
11-30 17:59 DEBUG  TaskList: ## Running get_iso...
11-30 17:59 DEBUG  TaskList: New task copy_file
11-30 17:59 DEBUG  TaskList: ### Running copy_file...
11-30 18:00 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
11-30 18:00 DEBUG  TaskList: # Cancelling tasklist
11-30 18:00 DEBUG  TaskList: New task check_iso
11-30 18:00 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
11-30 18:00 DEBUG  CommonBackend: Searching for local ISO
11-30 18:00 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-30 18:00 DEBUG  TaskList: New task get_metalink
11-30 18:00 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-30 18:00 DEBUG  TaskList: # Cancelling tasklist
11-30 18:00 DEBUG  TaskList: # Finished tasklist

---

### Post by Mark Phelps on 2011-12-01
The Wubi Guide (linked below) has details on how to install without an internet connection (in the case where you have both the installer and ISO on a local drive):

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

