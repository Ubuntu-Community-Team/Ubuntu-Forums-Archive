---
title: "Win 7 / Windows Installer Error"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by Brettjb76 on 2010-05-13
Hi all,

I currently have Windows 7 installed on an Acer Aspire One 532h netbook.  On seeing the new Ubuntu release, I downloaded the Windows Installer to have a dual boot system.   Unfortunately, I have had no luck, with either the downloader hanging after 12%, or when it does complete it gives an error.

I have chosen a fresh partition to install Ubuntu, and have created this through Windows 7 Disk Manager.  

- 126 Gb
- exFAT file system (only option other than NTFS) - currently empty partition

On one attempt, the install completed but Ubuntu would not boot.

Each other attempt has resulted in a hang or errors as per below.  If someone could advise how to rectify this issue, I would appreciate it a great deal.

----------------------------------------------------------------------------------------------------
[SIZE=1]
05-13 09:11 DEBUG  TaskList: ### Finished get_metalink
05-13 09:11 DEBUG  TaskList: New task download
05-13 09:11 DEBUG  TaskList: ### Running download...
05-13 09:11 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent) > D:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
05-13 10:41 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

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
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request


05-13 10:41 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
05-13 10:41 DEBUG  TaskList: ### Finished download
05-13 10:41 ERROR  TaskList: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
05-13 10:41 DEBUG  TaskList: # Cancelling tasklist
05-13 10:41 DEBUG  TaskList: # Finished tasklist
05-13 10:41 ERROR  root: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
[/SIZE]

---

### Post by lemming465 on 2010-05-14
I usually get the best dual-boot results if I install from booting a live desktop CD directly, rather than WUBI.  Also, if the partition was created from windows, the partition type and filesystem are going to be unfortunate.  If you are comfortable using ubuntu fdisk, I'd change the partition type ("t" command) to "83" (linux ext2/3/4) before doing the install, and I'd be sure to reformat the partition as ext3 or ext4.

It's OK to let grub2 take over the MBR, unless you are using bitlocker with a TPM chip.

---

### Post by darkod on 2010-05-14
With wubi you will NOT have a dual boot. Wubi resides inside windows and is sort of virtual ubuntu, like a virtual machine that you can install with an OS, but it sits in a file on your hdd.
If windows breaks, you can't boot wubi neither.

The point of dual boot is two independent systems on their separate partitions.

Having said that, if you want to try wubi again, try right-clicking the wubi.exe and select Run as Administrator. Sometimes in vista/win7 you need to install with admin privilegies.

And the partition you prepared for wubi, it needs to be ntfs. Maybe you were confused expecting a dual boot and selected the only available choice besides ntfs, but on the contrary, it needs to be ntfs. Wubi is inside windows.

---

### Post by lemming465 on 2010-05-14
While agreeing with darkod's advice, I'll just clarify that a WUBI install uses really big NTFS files to hold the Linux file systems (these are loopback mounted).  The boot process starts with windows, but switches to grub, and you end up running a native linux system.  This is different from running a virtual guest inside windows using a hypervisor such as vmware or virtualbox; with WUBI, you either boot windows, or you boot Linux.  

However, in this case Brettjb76 indicated he wanted to put Linux on its own, separate partition, so WUBI is the not the best kind of install.

---

### Post by Siddharth Yadav on 2010-05-15
I am trying to install 'ubuntu-8.04.4-desktop-i386' I downloaded the iso, and it had the wubi. The version however was '4.57.0.0' and the description says 7z Setup SFX. I tried to keep this and the iso in the same folder and install. But it goes on the start downloading it. I tried to download the proper version of wubi for the iso, I used Wubi-8.04.1-rev506 and others. But it still goes on and starts downloading. I am pretty sure that the iso is not corrupt. What's the issue? how to fix this?

---

### Post by RichStephens on 2010-05-26
Darkod is WRONG about wubi not giving you dual boot.  That is exactly what WUBI does.  It just makes the installation and removal of the dual boot easier.  WUBI doesn't set up a "virtual machine" situation.

I know because I had a wubi installation on my Windows XP machine, and wubi automatically set it up as a dual-boot situation.

---

### Post by wilee-nilee on 2010-05-26
> **RichStephens said:**
> Darkod is WRONG about wubi not giving you dual boot.  That is exactly what WUBI does.  It just makes the installation and removal of the dual boot easier.  WUBI doesn't set up a "virtual machine" situation.

I know because I had a wubi installation on my Windows XP machine, and wubi automatically set it up as a dual-boot situation.

Yeh right, you have no idea what your talking about.

---

