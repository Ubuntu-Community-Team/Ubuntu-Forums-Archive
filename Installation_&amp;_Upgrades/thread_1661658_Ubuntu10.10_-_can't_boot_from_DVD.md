---
title: "Ubuntu10.10 - can't boot from DVD"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by kjbox on 2011-01-07
Hi,

I am attempting to try and hopefully install XUbuntu.

I loaded the dvd (one that came with Linux Format Magazine No. 139), changed BIOS to boot from dvd, and then:

I get the welcome screen with the options to boot Ubuntu, KUbuntu, XUbuntu or Boot from First Hard Disk. As I have an older laptop I was going to try XUbuntu. However, the arrow keys did not change the boot option. In fact nothing worked, Tab did not bring up a menu and Enter did not initiate boot.

I tried reloading the dvd, switching off the laptop (no way to shutdown) and restarting but always come up with the same problem.

My DVD drive works fine and the dvd appears not to be faulty since all the info is readable when it is loaded with windows running.

My system details are:

HP compaqnx9000
Mobile Intel Pentium(R) 4-m CPU 2.20 GHz 219GHz 704MB RAM
Optiarc DVD RW AD-7580A
Radeon 1GP 340M

Hope somebody can suggest a solution.

Thanks in advance

---

### Post by wilee-nilee on 2011-01-07
I would try the dvd on another computer to start with to compare if it is the dvd.

I wouldn't equate a menu on the cd with no keyboard use as a good dvd until I tried it on another computer.

If so the download for any of those is free from the web.

---

### Post by kjbox on 2011-01-07
I have now tried that and the dvd works perfectly.

---

### Post by wilee-nilee on 2011-01-07
> **kjbox said:**
> I have now tried that and the dvd works perfectly.

If it was me since Xubuntu can be downloaded for free, is download it and try that. I don't think there is any easy answer here. I am assuming that the computer runs, and that it is not a hardware issue.

---

### Post by kjbox on 2011-01-07
Hi, thank you again.

Yes, the laptop works fine, in fact I am using it to send this. I tried to boot from the dvd again and the same thing happened. I pressed caps lock and no light came on so the dvd is crashing my computer for some reason.

I have started to download XUbuntu already but I live in Borneo and here the internet is barely out of the stone age, download will take approx 5 hours!

I will update here when it eventually finishes.

---

### Post by kjbox on 2011-01-07
OK this is getting weirder by the minute!!

I successfully downloaded XUbuntu and burnt the iso to disk.

Booting from the disk started ok and I got the language screen. However, as soon as I pressed Enter the laptop froze. I thought of changing the mode, as I have read about this being a possible fix, so I rebooted. Got the language screen again but pressing any key froze the computer. Then I tried rebooting and doing nothing ie letting the timer run down. The language screen disappeared but all I got was a blank screen with a blinking cursor and a frozen laptop!

Next I booted into windows (xp with sp3) and put the disk in to see if it would open and I could see and problems, I got a message as follows: 'Exception Processing Message c0000013 Parameters 75b6bd7c 4 75b6bd7c 75b6bd7c'

I clicked 'continue' got the same message, clicked 'continue' again and got the wubi installer. I tried a within windows install and this started off fine but then failed because of 'Permission Denied'. I tried again after logging in as Administrator to see if that helped but same result.

Viewing the log showed all to be going well until:

01-07 23:01 DEBUG TaskList: ## Finished create_dir_structure
01-07 23:01 DEBUG TaskList: ## Running uncompress_target_dir...
01-07 23:01 DEBUG TaskList: ## Finished uncompress_target_dir
01-07 23:01 DEBUG TaskList: ## Running create_uninstaller...
01-07 23:01 DEBUG WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-07 23:01 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-07 23:01 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-07 23:01 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Xubuntu
01-07 23:01 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Xubuntu.ico
01-07 23:01 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
01-07 23:01 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Xubuntu
01-07 23:01 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.xubuntu.org](http://www.xubuntu.org)
01-07 23:01 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-07 23:01 DEBUG TaskList: ## Finished create_uninstaller
01-07 23:01 DEBUG TaskList: ## Running copy_installation_files...
01-07 23:01 DEBUG WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
01-07 23:01 DEBUG WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\winboot -> C:\ubuntu\winboot
01-07 23:01 DEBUG WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\data\images\Xubuntu.ico -> C:\ubuntu\Xubuntu.ico
01-07 23:01 DEBUG TaskList: ## Finished copy_installation_files
01-07 23:01 DEBUG TaskList: ## Running get_iso...
01-07 23:01 DEBUG TaskList: New task copy_file
01-07 23:01 DEBUG TaskList: ### Running copy_file...
01-07 23:06 ERROR TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
01-07 23:06 DEBUG TaskList: # Cancelling tasklist
01-07 23:06 ERROR root: [Errno 13] Permission denied
Traceback (most recent call last):
File "\lib\wubi\application.py", line 56, in run
File "\lib\wubi\application.py", line 128, in select_task
File "\lib\wubi\application.py", line 194, in run_cd_menu
File "\lib\wubi\application.py", line 118, in select_task
File "\lib\wubi\application.py", line 156, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
01-07 23:06 DEBUG TaskList: New task check_iso
01-07 23:06 DEBUG CommonBackend: Searching for local ISO
01-07 23:06 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
01-07 23:06 DEBUG TaskList: New task get_metalink
01-07 23:06 ERROR TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
01-07 23:06 DEBUG TaskList: # Cancelling tasklist
01-07 23:06 DEBUG TaskList: # Finished tasklist

In case it was a cd drive problem I retried the whole process with a USB Stick download. This laptop does not have an option to boot from USB device so I could not try that, but trying to install via wubi produced the same result as above.

If it is a graphic card conflict then I can see no option other than to change the card since trying to change boot settings causes a freeze. Unless, o f course, somebody has another suggestion/solution.

Thanks for your help.

---

