---
title: "wubi and iso installation problem"
date: 2012-02-29
forum: Installation &amp; Upgrades
---

### Post by Paticio on 2012-02-29
Hi all,
I am new on this OS and would like to try it out. I downloaded the wubi.exe file and executed it. But it stopped with error. The log file ending as follow:

02-29 16:21 ERROR  TaskList: [Errno 13] Permission denied: 'G:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'G:\\wubildr'
02-29 16:21 DEBUG  TaskList: # Cancelling tasklist
02-29 16:21 DEBUG  TaskList: # Finished tasklist
02-29 16:21 ERROR  root: [Errno 13] Permission denied: 'G:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'G:\\wubildr'

G Drive is a removable disk, ie a card reader.

Then I downloaded the iso file and attempt to create a CD image for installation. The download appeared completed but the file cannot not be use to create iso disk image. The end result of the download with the file name as follow"

ubuntu-11.10-desktop-i386.iso.crdownload

I attempt to change the extension as iso but no success.

Anyone can advise on this?

Pat:confused:

---

### Post by cbob on 2012-03-01
Hi Pat,

Some suggestions, remove both wubi.exe and the iso file. The download them again, the crdownload extension is for files who is in progress of being downloaded. So just make sure the download is complete and the files should be renamed.

Though I suggest installing Ubuntu from USB, you still have the option of installing it along side another OS. Check out [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick).

/cbob

---

### Post by bcbc on 2012-03-01
The G:\wubildr error is bug [lpbug]862003[/lpbug]. If you read it you'll see that the install was actually successful.

The .crdownload extension on the ISO probably means it was interrupted and didn't complete. If you haven't run wubi.exe since the G:\wubildr problem, then rebooting will boot straight into Ubuntu.

---

### Post by Paticio on 2012-03-02
Hi all,
Thank you for your reply. I rebooted the PC and was unable to load the ubuntu, despite the error message on the wubi installation.

I am now able to explore the new OS.:P

Thank you very much

---

