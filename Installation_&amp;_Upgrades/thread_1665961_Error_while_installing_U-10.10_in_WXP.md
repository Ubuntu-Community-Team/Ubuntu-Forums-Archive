---
title: "Error while installing U-10.10 in WXP"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by maiardm on 2011-01-13
Hi!

i'm trying to install U-10.10 in WXP (SP3)

after some running time got this error from wubi:

[B]01-12 07:42 INFO   root: === wubi 10.10 rev197 ===
01-12 07:42 DEBUG  root: Logfile is c:\docume~1\rdm\config~1\temp\wubi-10.10-rev197.log
01-12 07:42 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
01-12 07:42 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\RDM\CONFIG~1\Temp\pyl1A.tmp\data
01-12 07:42 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\RDM\CONFIG~1\Temp\pyl1A.tmp\bin\7z.exe
01-12 07:42 DEBUG  CommonBackend: Fetching basic info...
01-12 07:42 DEBUG  CommonBackend: original_exe=D:\wubi.exe
01-12 07:42 DEBUG  CommonBackend: platform=win32
01-12 07:42 DEBUG  CommonBackend: osname=nt
01-12 07:42 DEBUG  CommonBackend: language=pt_BR
01-12 07:42 DEBUG  CommonBackend: encoding=cp1252
01-12 07:42 DEBUG  WindowsBackend: arch=amd64
....
01-12 07:42 DEBUG  WindowsBackend: windows version=xp
01-12 07:42 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
01-12 07:42 DEBUG  WindowsBackend: windows_sp=Service Pack 3
01-12 07:42 DEBUG  WindowsBackend: windows_build=2600
01-12 07:42 DEBUG  WindowsBackend: gmt=-3
01-12 07:42 DEBUG  WindowsBackend: country=BR
....
01-12 07:42 DEBUG  TaskList: ## Finished copy_installation_files
01-12 07:42 DEBUG  TaskList: ## Running get_iso...
01-12 07:42 DEBUG  TaskList: New task copy_file
01-12 07:42 DEBUG  TaskList: ### Running copy_file...
01-12 07:53 DEBUG  TaskList: ### Finished copy_file
[COLOR="DarkRed"]
01-12 07:54 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
01-12 07:54 DEBUG  TaskList: # Cancelling tasklist
01-12 07:54 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
01-12 07:54 DEBUG  TaskList: New task check_iso
01-12 07:54 DEBUG  CommonBackend: Searching for local ISO
01-12 07:54 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
01-12 07:54 DEBUG  TaskList: New task get_metalink
01-12 07:54 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
01-12 07:54 DEBUG  TaskList: # Cancelling tasklist
01-12 07:54 DEBUG  TaskList: # Finished tasklist
[/COLOR][/B]

Is there anything i can do to get around this ?

---

### Post by bcbc on 2011-01-13
copy wubi.exe and the downloaded CD image (.iso) in the same folder and run wubi from there.

---

