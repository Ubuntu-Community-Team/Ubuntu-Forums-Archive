---
title: "How to dual boot ubuntu on windows 7"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by Anand208 on 2010-02-24
[CENTER][FONT=Times New Roman][SIZE=2][COLOR=black]Hi guys i am newbie to linux os.I want to dual boot ubuntu 9.04 with windows 7 which is already running on my pc.When i tried to do it with live cd i am getting an error message "Permission denied" while extracting files from cd drive.The log file shows the information given below.[/COLOR][/SIZE][/FONT][/CENTER]
[SIZE=2][FONT=Times New Roman][COLOR=black]My system specifications are:[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman][COLOR=black]intel core 2 duo e7500[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman][COLOR=black]Windows 7 ultimate[/COLOR][/FONT][/SIZE]

LOG file:
 
02-24 13:19 DEBUG TaskList: ## Finished copy_installation_files
02-24 13:19 DEBUG TaskList: ## Running get_iso...
02-24 13:19 DEBUG TaskList: New task copy_file
02-24 13:19 DEBUG TaskList: ### Running copy_file...
02-24 13:21 ERROR TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
02-24 13:21 DEBUG TaskList: # Cancelling tasklist
02-24 13:21 ERROR root: [Errno 13] Permission denied
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
02-24 13:21 DEBUG TaskList: New task check_iso
02-24 13:21 DEBUG CommonBackend: Searching for local ISO
02-24 13:21 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
02-24 13:21 DEBUG TaskList: New task get_metalink
02-24 13:21 ERROR TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
02-24 13:21 DEBUG TaskList: # Cancelling tasklist
02-24 13:21 DEBUG TaskList: # Finished tasklist
 
How to do proceed with it?Any body know about the error in the log file?

---

### Post by darkod on 2010-02-24
This log is mentioning wubi. Are you trying to install wubi or ubuntu?
Wubi is working inside windows and is designed to be just a quick way to try ubuntu, not a long term install.
For proper dual boot on its own partition, just boot from the ubuntu cd and select Try Ubuntu if you want to try it running from the cd first, or Install Ubuntu if you want to install right away. Not from within windows. Boot with the cd.

---

### Post by Anand208 on 2010-02-25
Hi friend thanx for ur replyt.But I have tried in all possible ways to install it.It is showing the same error.How to fix it?

---

### Post by NefariousNobo on 2010-02-25
If you are using WUBI, it's probably an issue of you not running it as administrator or without the necessary privilege. 

If you're installing it from the LiveCD, then there may be an error with the way your partition was mounted. If you could possibly include a thorough description of when in the install the error occurred, I may be able to help further.

Hope this helps...

---

### Post by Anand208 on 2010-02-25
Actually I was not able to login as administrator.It was disabled.Then i searched google how to enable it and then made.Then i entered as administrator and tried to install using live cd.I am having four disk partitions in my computer with windows 7 in C:.I tried to install it with the option install with in windows and it shown the above error message.Even i tried other options also it is showing the same error.
Do you know how much free space it requires for installing it in the drive?I am having 6.8GB in my C:.Is that sufficient for installing ubuntu 9.04.I am really trying hard to install it.

Waiting for the reply eagerly

---

### Post by Mark Phelps on 2010-02-25
> **Anand208 said:**
> Actually I was not able to login as administrator.It was disabled.Then i searched google how to enable it and then made.
You don't need to login as Administrator.  You only need to right-click the .exe file and select Run as Administrator.  That will invoke the Trusted Installer to run the app.

[QUOTEI am having four disk partitions in my computer with windows 7 in C:[/QUOTE]
That's all the primary partitions you can have on a drive. Unloess you want to tackle a difficult process of backing off partitions, reformatting partitions, and restoring date, you're not going to be able to create any more partitions.

> I tried to install it with the option install with in windows and it shown the above error message.Even i tried other options also it is showing the same error.
Do you know how much free space it requires for installing it in the drive?I am having 6.8GB in my C:.Is that sufficient for installing ubuntu 9.04.I am really trying hard to install it.

That's enough space for a minimal install -- but if you use up ALL the available space, Win7 won't run anymore.  IT need space for working files.

---

