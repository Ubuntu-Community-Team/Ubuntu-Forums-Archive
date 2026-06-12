---
title: "Dual boot Windows 8.1 and Ubuntu 14.04, Installation error"
date: 2014-05-20
forum: Installation &amp; Upgrades
---

### Post by kotarikirankumar on 2014-05-20
Hi, I'm using windows 8.1 

Now, I am trying to install ubuntu 14.04 inside windows 8.1, it is giving the following error.

05-20 22:57 ERROR  root: Cannot download the metalink and therefore the ISO

Error in detail.
[
05-20 22:57 DEBUG  TaskList: ## Finished copy_installation_files
05-20 22:57 DEBUG  TaskList: ## Running get_iso...
05-20 22:57 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-20 22:57 DEBUG  TaskList: New task get_metalink
05-20 22:57 DEBUG  TaskList: ### Running get_metalink...
05-20 22:57 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink](http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink) > D:\ubuntu\install
05-20 22:57 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink](http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
05-20 22:57 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.metalink) > D:\ubuntu\install
05-20 22:57 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
05-20 22:57 DEBUG  TaskList: ### Finished get_metalink
05-20 22:57 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 406, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-20 22:57 DEBUG  TaskList: # Cancelling tasklist
05-20 22:57 DEBUG  TaskList: # Finished tasklist
05-20 22:57 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 406, in download_iso
Exception: Cannot download the metalink and therefore the ISO
]

May I know about error, suggest me how to install ubuntu 14.04 inside windows 8.1

---

### Post by oldfred on 2014-05-20
Is this pre-installed Windows booting in UEFI mode from a gpt partitioned drive.

Wubi does not work on gpt partitioned drives.
[http://askubuntu.com/questions/360616/why-was-wubi-removed-from-13-04](http://askubuntu.com/questions/360616/why-was-wubi-removed-from-13-04)
Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)

And 12.04 is the last officially supported wubi. You can install it in MBR partitioned drives, but then are on your own which is the opposite of the purpose of wubi as a easy to install and uninstall Ubuntu just to use for  a test before upgrading to a full install.

If your system is UEFI, then use Windows to shrink the Windows system partition and reboot so it can run chkdsk and update to its new size. Do not create any partitions with Windows as it may convert to dynamic even with gpt which has an very large (128) number of default partitions.

Make sure fast boot is off, usually better to have secure boot off. 
And make full backups of Windows and efi partition before install. You should have those backups even if not installing another system.
Make a Windows 8 repair flash drive.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

    
More details in link in my signature.

---

