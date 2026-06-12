---
title: "Unable to complete 10.04 install"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by PoppaK on 2010-05-30
You've probably heard this one before, but I could not turn up anything with searching.  I'm trying to install Ubuntu on an Aspire laptop with Windows XP.  I downloaded 10.04 and burned an ISO image.  I boot Windows and open the ISO disk.  I open the first choice which is to try Ubuntu prior to a complete installation. The installation starts and proceeds for a few minutes.  Then it stops and displays a message 'Permission Denied' and a suggestion to check the installation log.  The last few lines are:

05-21 13:45 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARLHE~1\LOCALS~1\Temp\pyl6.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-21 13:45 DEBUG  TaskList: ## Finished copy_installation_files
05-21 13:45 DEBUG  TaskList: ## Running get_iso...
05-21 13:45 DEBUG  TaskList: New task copy_file
05-21 13:45 DEBUG  TaskList: ### Running copy_file...
05-21 14:00 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
05-21 14:00 DEBUG  TaskList: # Cancelling tasklist
05-21 14:00 ERROR  root: [Errno 13] Permission denied

There are a few more lines showing the installation trying futilely to recover.  I would like some help in completing this installation.

TIA,
Karl

---

### Post by ronparent on 2010-05-30
The boot of the CD proceeds directly to an install if you don't hit any key right after the splash screen first appears. You may need to hit that key so the menu appears giving you an option to 'try without installing'. Often you have to hit f6 when that menu appears to select one or more of the offerred boot parameters until the conditions are found to permit ubuntu to boot on your computer. Once the desktop is up, you should know what special boot parameter are required to run the install on your computer. And you will have the option to run that install on the desktop.

---

