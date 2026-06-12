---
title: "install problem"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by jamsie11 on 2012-01-27
I have been trying to install ubuntu via wubi so that I can dual boot using latest edition that is provided here:[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer).

It starts to install, but at the very end I get an error telling me I don't have permission.  Here is the end of the log file:
01-27 08:58 ERROR  TaskList: [Errno 13] Permission denied: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'F:\\wubildr'
01-27 08:58 DEBUG  TaskList: # Cancelling tasklist
01-27 08:58 DEBUG  TaskList: # Finished tasklist
01-27 08:58 ERROR  root: [Errno 13] Permission denied: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'F:\\wubildr'

There is nothing in "F" - it's empty.  The only thing I have connect in a external hard drive which is "J".  

I am running Win 7 64 on a HP Pavilion HPE.  I have administrator rights. 

Can someone please give me a clue as to what I'm doing wrong? 

Thanks.

---

### Post by Paddy Landau on 2012-01-27
How have you formatted your F: drive?

A word of advice. WUBI is unstable. If you already have an empty F: drive -- actually, it is probably a partition and not a drive -- I would suggest you do a native installation to that partition.

If you wish to do this, as a first step uninstall WUBI and reboot. If you need any help with partitions and figuring out where to install Ubuntu (while keeping Windows), let us know.

---

### Post by jamsie11 on 2012-01-27
> **Paddy Landau said:**
> How have you formatted your F: drive?

A word of advice. WUBI is unstable. If you already have an empty F: drive -- actually, it is probably a partition and not a drive -- I would suggest you do a native installation to that partition.

If you wish to do this, as a first step uninstall WUBI and reboot. If you need any help with partitions and figuring out where to install Ubuntu (while keeping Windows), let us know.


Thanks for your reply Paddy.

I have uninstalled WUBI.

Drive "F" is just an empty slot for a smart media card or a SD, USB etc.  There is no partition "F".  On my HD I have "C",  and "D" (which is where my recovery data is).  I also have  and an external HD which is listed as "J".

Yes, if you could instruct me on how to partition my HD without damaging data already there, please point me in the right direction.  

Since you say WUBI is unstable and I'm a newbie to all this,  I'm not going to bother with it. 

I hope you or others can help me install ubuntu.  

Thanks again.

---

### Post by bcbc on 2012-01-27
Wubi is not unstable. It has its issues, but so does everything. 

Wubi is intended for people to try out Ubuntu and it's a very close approximation to the real thing. The main benefit is that you don't need to repartition your computer, and that means uninstalling is simple (you uninstall just like any program from the Windows control panel).

If you don't mind partitioning, then a normal dual boot is better (but more difficult to later remove). Why don't you review this guide and see if you have any questions: [http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

If you want to use Wubi, then note that your original problem was bug [lpbug]862003[/lpbug] which means that the installation was successful.

---

### Post by Paddy Landau on 2012-01-28
> **bcbc said:**
> Wubi is not unstable. It has its issues, but so does everything.
Fair enough. My wording could have been more accurate. WUBI has a higher rate of failure without the ability to recover, particularly with upgrades, than does Ubuntu.

Thanks for noting the bug.

Anyway, to get back to the OP's problem...

If your F: drive is a separate drive (an SSD card), that is ideal for you. You can install Ubuntu onto it natively, being sure that you do not damage your Windows in any way.

[SIZE=3]**Some background**[/SIZE]

In Windows, drives (or rather partitions within drives) are named by letters -- A:, B:, C:, D:, E:, F:, and so on.

But in Linux, they have entirely different names. Drives are named sda, sdb, sdc, and so on. (They can have different names such as hda, hdb, hdc and so forth, but that probably won't happen with you.)

A drive *must* be partitioned; even flash disks. Each partition is numbered; so, partitions in sda would be numbered sda1, sda2, and so forth. Partition nunmbers do not have to be in order; you might have sda3, sda4, sda2, sda7.

In Linux, the partitions are *mounted* (made accessible) in a folder called /dev; thus you have /dev/sda1, /dev/sda2, and so on.

Suppose you had /dev/sda1, /dev/sda2 and /dev/sdb1. Windows would call those C:, D: and E: respectively, where C: and D: are in fact the same drive but different partitions.

[SIZE=3]**How to install**[/SIZE]

Download the version of Ubuntu that you want. Choose 64-bit if you have a modern machine with 2Gb RAM or more, otherwise choose 32-bit.

Burn your download to a CD (called a Live CD) or for faster response to a Live USB. The instructions are on [the download page]("http://www.ubuntu.com/download/ubuntu/download").

Now boot from the Live CD or Live USB. When it comes to asking you where to install, choose *Something else* (examples are on the download page). When it asks to choose the drive, select your SSD card.

***Warnings:***

[LIST=1]
[*]Be sure to choose the SSD card, otherwise you will overwrite your Windows!
[*]Back up before you actually do this, in case you accidentally choose the wrong thing.
[*]Choose to overwrite the entire SSD card; this will completely erase it (so be sure you have nothing you need on the card), and it will reformat it suitable for Ubuntu. (Instead of NTFS, which is Windows's format, it will choose something called ext4.)
[/LIST]
Follow the instructions. Post back should you need any help.

---

