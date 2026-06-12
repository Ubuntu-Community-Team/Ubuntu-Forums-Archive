---
title: "Can't complete the Ubuntu uninstall."
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by haciendadad on 2010-11-09
Installed Ubuntu in Windows Vista but never really got it to work so I tried to uninstalling it.  I uninstalled it from Control Panel then tried to install LinuxMint but when I try to start the LinuxMint install the Ubuntu Uninstaller starts and displays this error that I pulled form the log file.

```
11-09 23:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-09 23:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-09 23:21 DEBUG  Distro:   parsing info from str=Linux Mint 9 "Isadora" - Release amd64 (20100427.1)

11-09 23:21 DEBUG  Distro:   parsed info={'name': 'Linux Mint', 'subversion': 'Release', 'version': '9', 'build': '20100427.1', 'codename': 'Isadora', 'arch': 'amd64'}
11-09 23:21 DEBUG  Distro: wrong name: Linux Mint != Ubuntu
11-09 23:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-09 23:21 DEBUG  Distro: wrong name: Linux Mint != Ubuntu
11-09 23:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-09 23:21 DEBUG  Distro: wrong name: Linux Mint != Ubuntu Netbook
11-09 23:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-09 23:21 DEBUG  Distro: wrong name: Linux Mint != Kubuntu
11-09 23:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-09 23:21 DEBUG  Distro: wrong name: Linux Mint != Kubuntu
11-09 23:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-09 23:21 DEBUG  Distro: wrong name: Linux Mint != Kubuntu Netbook
11-09 23:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-09 23:21 DEBUG  Distro: wrong name: Linux Mint != Xubuntu
11-09 23:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-09 23:21 DEBUG  Distro: wrong name: Linux Mint != Xubuntu
11-09 23:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-09 23:21 DEBUG  Distro: wrong name: Linux Mint != Mythbuntu
11-09 23:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-09 23:21 DEBUG  Distro: wrong name: Linux Mint != Mythbuntu
11-09 23:21 INFO   root: Running the uninstaller...
11-09 23:21 INFO   CommonBackend: This is the uninstaller running
11-09 23:21 DEBUG  WindowsFrontend: __init__...
11-09 23:21 DEBUG  WindowsFrontend: on_init...
11-09 23:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jace114\AppData\Local\Temp\pylEC42.tmp\translations, languages=['en_US', 'en']
11-09 23:22 INFO   root: Received settings
11-09 23:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jace114\AppData\Local\Temp\pylEC42.tmp\translations, languages=['en_US', 'en']
11-09 23:22 DEBUG  TaskList: # Running tasklist...
11-09 23:22 DEBUG  TaskList: ## Running Backup ISO...
11-09 23:22 DEBUG  TaskList: ## Finished Backup ISO
11-09 23:22 DEBUG  TaskList: ## Running Remove bootloader entry...
11-09 23:22 DEBUG  WindowsBackend: Removing bcd entry {686a18d1-ffb5-11dd-ba34-001fe1ddad3e}
11-09 23:22 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {686a18d1-ffb5-11dd-ba34-001fe1ddad3e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 501, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 684, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {686a18d1-ffb5-11dd-ba34-001fe1ddad3e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
11-09 23:22 DEBUG  TaskList: # Cancelling tasklist
11-09 23:22 DEBUG  TaskList: # Finished tasklist
11-09 23:22 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {686a18d1-ffb5-11dd-ba34-001fe1ddad3e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 501, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 684, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {686a18d1-ffb5-11dd-ba34-001fe1ddad3e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=

```

It looks like the specified entry is already missing, so how do I get past this to install LinuxMint?

Thanks for any help!

---

### Post by yunchiluo on 2010-11-10
This looks more like the python script can't find bcdedit.exe. Are you running this in administrator mode? Is bcdedit.exe where it's supposed to be?

---

### Post by Mark Phelps on 2010-11-10
Not a Wubi expert, but from the log, it looks like it's trying to deleted the Vista BCD entry that Wubi originally created -- and failing in the process.

To do this yourself, suggest you do the following:
1) Go to the NeoSmart Technology forums and download EasyBCD
2) Install that into your Vista setup
3) Launch it in Vista
4) Click the View Settings button to see if there is still an entry for Ubuntu
5) If there is, use the Edit Settings button, select the Ubuntu entry, and remove it.
6) Exit, saving the results
7) Reboot Vist
8) Launch EasyBCD and confirm that the Ubuntu entry is now gone.

You should now be able to install Mint without these problems repeating.

---

### Post by sjonesy on 2010-11-30
This is happening a lot by the looks, my original install of mint 10 went well, but when I screwed up the sound I decided to reinstall mint 10, got the same stupid wubi error. Since I have a free external usb drive the winblows partition was untouched. Seems to me that it could be made more simple to uninstall from the live cd of mint.

---

### Post by sjonesy on 2010-11-30
Well I deleted the boot menu entry and same problem still happens. Any other suggestions?

---

### Post by sjonesy on 2010-11-30
Ok I got it to unisntall, need to manually delete the reg entry in regedit

---

