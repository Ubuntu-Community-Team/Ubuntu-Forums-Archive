---
title: "Ubuntu 9.04 Installation fails."
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by yoog on 2010-04-07
I am trying to install Ubunti 9.04 from a CD+RW media using "alongwith windows" option from within windows Vista 32 bit. but I kept getting error and installation fails. I have posted the log file below but I can not figure out the problem.

Spec:
ASUS P7Q Pro Turbo
E6300 @ 2.80GHz
8GB OCZ
500GB x 2 (RAID 0)
Vista 32 Bit.

Any help is highly appreciated.

Log file:
04-06 13:28 INFO root: === wubi 9.04 rev128 ===
04-06 13:28 DEBUG root: Logfile is c : \users\bharat~1\appdata\local\temp\wubi-9.04-rev128.log
04-06 13:28 DEBUG root: sys.argv = ['main.pyo', '--exefile="E : \\wubi.exe"', '--cdmenu']
04-06 13:28 DEBUG CommonBackend: data_dir=C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp\dat a
04-06 13:28 DEBUG WindowsBackend: 7z=C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp\bin \7z.exe
04-06 13:28 DEBUG CommonBackend: Fetching basic info...
04-06 13:28 DEBUG CommonBackend: original_exe=E : \wubi.exe
04-06 13:28 DEBUG CommonBackend: platform=win32
04-06 13:28 DEBUG CommonBackend: osname=nt
04-06 13:28 DEBUG CommonBackend: language=en_US
04-06 13:28 DEBUG CommonBackend: encoding=cp1252
04-06 13:28 DEBUG WindowsBackend: arch=amd64
04-06 13:28 DEBUG CommonBackend: Parsing isolist=C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp\dat a\isolist.ini
04-06 13:28 DEBUG CommonBackend: Adding distro Xubuntu-i386
04-06 13:28 DEBUG CommonBackend: Adding distro Xubuntu-amd64
04-06 13:28 DEBUG CommonBackend: Adding distro Kubuntu-amd64
04-06 13:28 DEBUG CommonBackend: Adding distro Mythbuntu-i386
04-06 13:28 DEBUG CommonBackend: Adding distro Ubuntu-amd64
04-06 13:28 DEBUG CommonBackend: Adding distro Ubuntu-i386
04-06 13:28 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
04-06 13:28 DEBUG CommonBackend: Adding distro Kubuntu-i386
04-06 13:28 DEBUG WindowsBackend: Fetching host info...
04-06 13:28 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi
04-06 13:28 DEBUG WindowsBackend: windows version=vista
04-06 13:28 DEBUG WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
04-06 13:28 DEBUG WindowsBackend: windows_sp=Service Pack 2
04-06 13:28 DEBUG WindowsBackend: windows_build=6002
04-06 13:28 DEBUG WindowsBackend: gmt=-5
04-06 13:28 DEBUG WindowsBackend: country=US
04-06 13:28 DEBUG WindowsBackend: timezone=America/New_York
04-06 13:28 DEBUG WindowsBackend: windows_username=bharatAdmin
04-06 13:28 DEBUG WindowsBackend: user_full_name=bharatAdmin
04-06 13:28 DEBUG WindowsBackend: user_directory=bharatAdmin
04-06 13:28 DEBUG WindowsBackend: windows_language_code=1033
04-06 13:28 DEBUG WindowsBackend: windows_language=English
04-06 13:28 DEBUG WindowsBackend: processor_name=Pentium(R) Dual-Core CPU E6300 @ 2.80GHz
04-06 13:28 DEBUG WindowsBackend: bootloader=vista
04-06 13:28 DEBUG WindowsBackend: system_drive=Drive(C: hd 457970.070313 mb free )
04-06 13:28 DEBUG WindowsBackend: drive=Drive(C: hd 457970.070313 mb free )
04-06 13:28 DEBUG WindowsBackend: drive=Drive([IMG]http://ubuntuforums.org/images/smilies/familiar/disgusted.png[/IMG] hd 38052.6445313 mb free ntfs)
04-06 13:28 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-06 13:28 DEBUG WindowsBackend: drive=Drive(F: hd 57703.046875 mb free fat32)
04-06 13:28 DEBUG WindowsBackend: drive=Drive(G: hd 207689.429688 mb free ntfs)
04-06 13:28 DEBUG WindowsBackend: drive=Drive(H: removable 1003.96875 mb free fat)
04-06 13:28 DEBUG WindowsBackend: drive=Drive(I: hd 32239.859375 mb free ntfs)
04-06 13:28 DEBUG WindowsBackend: uninstaller_path=None
04-06 13:28 DEBUG WindowsBackend: previous_target_dir=None
04-06 13:28 DEBUG WindowsBackend: previous_distro_name=None
04-06 13:28 DEBUG WindowsBackend: keyboard_id=67699721
04-06 13:28 DEBUG WindowsBackend: keyboard_layout=us
04-06 13:28 DEBUG WindowsBackend: keyboard_variant=
04-06 13:28 DEBUG CommonBackend: locale=en_US.UTF-8
04-06 13:28 DEBUG WindowsBackend: total_memory_mb=2047.99999905
04-06 13:28 DEBUG CommonBackend: Searching ISOs on USB devices
04-06 13:28 DEBUG CommonBackend: Searching for local CDs
04-06 13:28 DEBUG Distro: checking whether C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp is a valid Ubuntu CD
04-06 13:28 DEBUG Distro: does not contain C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp\cas per\filesystem.squashfs
04-06 13:28 DEBUG Distro: checking whether C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp is a valid Ubuntu CD
04-06 13:28 DEBUG Distro: does not contain C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp\cas per\filesystem.squashfs
04-06 13:28 DEBUG Distro: checking whether C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp is a valid Kubuntu CD
04-06 13:28 DEBUG Distro: does not contain C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp\cas per\filesystem.squashfs
04-06 13:28 DEBUG Distro: checking whether C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp is a valid Kubuntu CD
04-06 13:28 DEBUG Distro: does not contain C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp\cas per\filesystem.squashfs
04-06 13:28 DEBUG Distro: checking whether C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp is a valid Xubuntu CD
04-06 13:28 DEBUG Distro: does not contain C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp\cas per\filesystem.squashfs
04-06 13:28 DEBUG Distro: checking whether C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp is a valid Xubuntu CD
04-06 13:28 DEBUG Distro: does not contain C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp\cas per\filesystem.squashfs
04-06 13:28 DEBUG Distro: checking whether C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp is a valid Mythbuntu CD
04-06 13:28 DEBUG Distro: does not contain C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp\cas per\filesystem.squashfs
04-06 13:28 DEBUG Distro: checking whether C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp is a valid Mythbuntu CD
04-06 13:28 DEBUG Distro: does not contain C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp\cas per\filesystem.squashfs
04-06 13:28 DEBUG Distro: checking whether D : \ is a valid Ubuntu CD
04-06 13:28 DEBUG Distro: does not contain D : \casper\filesystem.squashfs
04-06 13:28 DEBUG Distro: checking whether D : \ is a valid Ubuntu CD
04-06 13:28 DEBUG Distro: does not contain D : \casper\filesystem.squashfs
04-06 13:28 DEBUG Distro: checking whether D : \ is a valid Kubuntu CD
04-06 13:28 DEBUG Distro: does not contain D : \casper\filesystem.squashfs
04-06 13:28 DEBUG Distro: checking whether D : \ is a valid Kubuntu CD
04-06 13:28 DEBUG Distro: does not contain D : \casper\filesystem.squashfs
04-06 13:28 DEBUG Distro: checking whether D : \ is a valid Xubuntu CD
04-06 13:28 DEBUG Distro: does not contain D : \casper\filesystem.squashfs
04-06 13:28 DEBUG Distro: checking whether D : \ is a valid Xubuntu CD
04-06 13:28 DEBUG Distro: does not contain D : \casper\filesystem.squashfs
04-06 13:28 DEBUG Distro: checking whether D : \ is a valid Mythbuntu CD
04-06 13:28 DEBUG Distro: does not contain D : \casper\filesystem.squashfs
04-06 13:28 DEBUG Distro: checking whether D : \ is a valid Mythbuntu CD
04-06 13:28 DEBUG Distro: does not contain D : \casper\filesystem.squashfs
04-06 13:28 DEBUG Distro: checking whether E : \ is a valid Ubuntu CD
04-06 13:28 DEBUG Distro: info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
04-06 13:28 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
04-06 13:28 INFO Distro: Found a valid CD for Ubuntu: E : \
04-06 13:28 INFO root: Running the CD menu...
04-06 13:28 DEBUG WindowsFrontend: __init__...
04-06 13:28 DEBUG WindowsFrontend: on_init...
04-06 13:28 INFO root: CD menu finished
04-06 13:28 INFO root: Running the installer...
04-06 13:28 DEBUG WinuiInstallationPage: target_drive=[IMG]http://ubuntuforums.org/images/smilies/familiar/disgusted.png[/IMG], installation_size=17000MB, distro_name=Ubuntu, language=English, username=bharatadmin
04-06 13:28 INFO root: Received settings
04-06 13:28 DEBUG TaskList: # Running tasklist...
04-06 13:28 DEBUG TaskList: ## Running select_target_dir...
04-06 13:28 INFO WindowsBackend: Installing into D : \ubuntu
04-06 13:28 DEBUG TaskList: ## Finished select_target_dir
04-06 13:28 DEBUG TaskList: ## Running create_dir_structure...
04-06 13:28 DEBUG CommonBackend: Creating dir D : \ubuntu
04-06 13:28 DEBUG CommonBackend: Creating dir D : \ubuntu\disks
04-06 13:28 DEBUG CommonBackend: Creating dir D : \ubuntu\install
04-06 13:28 DEBUG CommonBackend: Creating dir D : \ubuntu\install\boot
04-06 13:28 DEBUG CommonBackend: Creating dir D : \ubuntu\disks\boot
04-06 13:28 DEBUG CommonBackend: Creating dir D : \ubuntu\disks\boot\grub
04-06 13:28 DEBUG CommonBackend: Creating dir D : \ubuntu\install\boot\grub
04-06 13:28 DEBUG TaskList: ## Finished create_dir_structure
04-06 13:28 DEBUG TaskList: ## Running uncompress_target_dir...
04-06 13:28 DEBUG TaskList: ## Finished uncompress_target_dir
04-06 13:28 DEBUG TaskList: ## Running create_uninstaller...
04-06 13:28 DEBUG WindowsBackend: Copying uninstaller E : \wubi.exe -> D : \ubuntu\uninstall-wubi.exe
04-06 13:28 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi UninstallString D : \ubuntu\uninstall-wubi.exe
04-06 13:28 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi InstallationDir D : \ubuntu
04-06 13:28 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayName Ubuntu
04-06 13:28 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayIcon D : \ubuntu\Ubuntu.ico
04-06 13:28 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayVersion 9.04-rev128
04-06 13:28 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi Publisher Ubuntu
04-06 13:28 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi URLInfoAbout [[COLOR=#22229c]http://www.ubuntu.com[/COLOR]]("http://www.ubuntu.com")
04-06 13:28 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi HelpLink [[COLOR=#22229c]http://www.ubuntu.com/support[/COLOR]]("http://www.ubuntu.com/support")
04-06 13:28 DEBUG TaskList: ## Finished create_uninstaller
04-06 13:28 DEBUG TaskList: ## Running copy_installation_files...
04-06 13:28 DEBUG WindowsBackend: Copying C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp\dat a\custom-installation -> D : \ubuntu\install\custom-installation
04-06 13:28 DEBUG WindowsBackend: Copying C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp\win boot -> D : \ubuntu\winboot
04-06 13:28 DEBUG WindowsBackend: Copying C : \Users\BHARAT~1\AppData\Local\Temp\pyl1C85.tmp\dat a\images\Ubuntu.ico -> D : \ubuntu\Ubuntu.ico
04-06 13:28 DEBUG TaskList: ## Finished copy_installation_files
04-06 13:28 DEBUG TaskList: ## Running get_iso...
04-06 13:28 DEBUG TaskList: New task copy_file
04-06 13:28 DEBUG TaskList: ### Running copy_file...
04-06 13:31 DEBUG TaskList: ### Finished copy_file
04-06 13:31 ERROR TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
File "Z : \home\evan\bzr\wubi.trunk\build\wubi\files\lib\wub i\backends\common\tasklist.py", line 196, in __call__
File "Z : \home\evan\bzr\wubi.trunk\build\wubi\files\lib\wub i\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
04-06 13:31 DEBUG TaskList: # Cancelling tasklist
04-06 13:31 ERROR root: [Errno 13] Permission denied
Traceback (most recent call last):
File "Z : \home\evan\bzr\wubi.trunk\build\wubi\files\lib\wub i\application.py", line 55, in run
File "Z : \home\evan\bzr\wubi.trunk\build\wubi\files\lib\wub i\application.py", line 125, in select_task
File "Z : \home\evan\bzr\wubi.trunk\build\wubi\files\lib\wub i\application.py", line 193, in run_cd_menu
File "Z : \home\evan\bzr\wubi.trunk\build\wubi\files\lib\wub i\application.py", line 117, in select_task
File "Z : \home\evan\bzr\wubi.trunk\build\wubi\files\lib\wub i\application.py", line 155, in run_installer
File "Z : \home\evan\bzr\wubi.trunk\build\wubi\files\lib\wub i\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
04-06 13:31 DEBUG TaskList: New task check_iso
04-06 13:31 DEBUG CommonBackend: Searching for local ISO
04-06 13:31 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
04-06 13:31 DEBUG TaskList: New task get_metalink
04-06 13:31 ERROR TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
File "Z : \home\evan\bzr\wubi.trunk\build\wubi\files\lib\wub i\backends\common\tasklist.py", line 196, in __call__
File "Z : \home\evan\bzr\wubi.trunk\build\wubi\files\lib\wub i\backends\common\backend.py", line 482, in get_iso
File "Z : \home\evan\bzr\wubi.trunk\build\wubi\files\lib\wub i\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-06 13:31 DEBUG TaskList: # Cancelling tasklist
04-06 13:31 DEBUG TaskList: # Finished tasklist
Traceback (most recent call last):
File "Z : \ home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi \backends\common\tasklist.py", line 196, in __call__
File "Z : \ home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi \backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
04-06 13:31 DEBUG TaskList: # Cancelling tasklist
04-06 13:31 ERROR root: [Errno 13] Permission denied
Traceback (most recent call last):
File "Z : \ home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi \application.py", line 55, in run
File "Z : \ home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi \application.py", line 125, in select_task
File "Z : \ home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi \application.py", line 193, in run_cd_menu
File "Z : \ home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi \application.py", line 117, in select_task
File "Z : \ home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi \application.py", line 155, in run_installer
File "Z : \ home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi \frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
04-06 13:31 DEBUG TaskList: New task check_iso
04-06 13:31 DEBUG CommonBackend: Searching for local ISO
04-06 13:31 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
04-06 13:31 DEBUG TaskList: New task get_metalink
04-06 13:31 ERROR TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
File "Z : \ home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi \backends\common\tasklist.py", line 196, in __call__
File "Z : \ home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi \backends\common\backend.py", line 482, in get_iso
File "Z : \ home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi \backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-06 13:31 DEBUG TaskList: # Cancelling tasklist
04-06 13:31 DEBUG TaskList: # Finished tasklist

---

