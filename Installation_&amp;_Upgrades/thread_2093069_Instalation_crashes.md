---
title: "Instalation crashes"
date: 2012-12-09
forum: Installation &amp; Upgrades
---

### Post by jpaulb on 2012-12-09
I had this happen also today with wubi 12.10 rev273
The installation crashes. The error seems to be The boot configuration  data store could not be opened.

```
12-09 15:48 DEBUG  TaskList: ### Running modify_bcd...
12-09 15:48 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 871950.609375 mb free ntfs)
12-09 15:49 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 694, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
12-09 15:49 DEBUG  TaskList: # Cancelling tasklist
12-09 15:49 DEBUG  TaskList: New task modify_bcd
12-09 15:49 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 694, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
12-09 15:49 DEBUG  TaskList: New task modify_bcd
12-09 15:49 DEBUG  TaskList: New task modify_bcd
12-09 15:49 DEBUG  TaskList: New task modify_bcd
12-09 15:49 DEBUG  TaskList: New task modify_bcd
12-09 15:49 DEBUG  TaskList: New task modify_bcd
12-09 15:49 DEBUG  TaskList: ## Finished modify_bootloader
12-09 15:49 DEBUG  TaskList: # Finished tasklist

```there is about 800GB free on the HDD there shouldn't be any  problem with fragmentation. The error seems to be The boot configuration  data store could not be opened.

---

### Post by bcbc on 2012-12-09
The problem is that something has turned your boot partition (that contains the BCD store) offline. You can find directions how to turn it back online at the following link:
[http://askubuntu.com/questions/73585/wubi-installer-error-the-boot-configuration-data-store-could-not-be-opened]("http://askubuntu.com/q/73585/14916")

---

### Post by jpaulb on 2012-12-23
> **bcbc said:**
> The problem is that something has turned your boot partition (that contains the BCD store) offline. You can find directions how to turn it back online at the following link:
[http://askubuntu.com/questions/73585/wubi-installer-error-the-boot-configuration-data-store-could-not-be-opened]("http://askubuntu.com/q/73585/14916")

Thanks I tried that no luck.

---

### Post by bcbc on 2012-12-23
The other approach is to assign a drive letter to the boot partition. You can do this from the Windows Disk Management (Create and format partitions).

---

### Post by jpaulb on 2012-12-23
Windows 7 is on its' own HDD as it came from Dell,  Ubuntu on another HDD.
Windows HDD has only 2 partitions, the installation and the recovery partition, a far as I know that HDD does not have a separate boot partition.

---

### Post by Bucky Ball on 2012-12-23
*Thread Moved to **Installation & Upgrades***

Your thread is tagged with 'Wubi' yet you are now saying you have Windows and Ubuntu on separate partitions. 

A Wubi install is Ubuntu inside Windows ... which is it?

---

### Post by jpaulb on 2012-12-23
> **Bucky Ball said:**
> *Thread Moved to **Installation & Upgrades***

Your thread is tagged with 'Wubi' yet you are now saying you have Windows and Ubuntu on separate partitions. 

A Wubi install is Ubuntu inside Windows ... which is it?

Yes I know
The problem is after I installed wubi once the windows is messed up. Read the first entry here.

I use wubi with windows to preview the next Ubuntu installation before I up grade my linux installation. I have been running Xubuntu since Ubuntu started with that Unity which I personally think sucks. I used wubi to install the latest ubuntu distro  and then removed it to try out  Kubuntu. that is when something screwed up and I can not use wubi because of the warning I get which is stated at the beginning of this thread.

---

### Post by Bucky Ball on 2012-12-23
Point is ... which do you want help with? The Wubi install or the Ubuntu install on the separate partition? If the latter, please remove the 'Wubi' tag from the thread title. Cheers. ;)

---

### Post by jpaulb on 2012-12-23
> **Bucky Ball said:**
> Point is ... which do you want help with? The Wubi install or the Ubuntu install on the separate partition? If the latter, please remove the 'Wubi' tag from the thread title. Cheers. ;)

Wubi instal as I asked for with my initial question.  Go back to beginning. why do I get this warning at the start of this thread ???
> 12-09 15:48 DEBUG  TaskList: ### Running modify_bcd...
12-09 15:48 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 871950.609375 mb free ntfs)
12-09 15:49 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 694, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
12-09 15:49 DEBUG  TaskList: # Cancelling tasklist
12-09 15:49 DEBUG  TaskList: New task modify_bcd
12-09 15:49 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 694, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
12-09 15:49 DEBUG  TaskList: New task modify_bcd
12-09 15:49 DEBUG  TaskList: New task modify_bcd
12-09 15:49 DEBUG  TaskList: New task modify_bcd
12-09 15:49 DEBUG  TaskList: New task modify_bcd
12-09 15:49 DEBUG  TaskList: New task modify_bcd
12-09 15:49 DEBUG  TaskList: ## Finished modify_bootloader
12-09 15:49 DEBUG  TaskList: # Finished tasklist

---

### Post by arpanaut on 2012-12-23
If your windows is not working or its filesystem is corrupt,
then I have doubts that the wubi installer will work or even be able to write to the windows system. 
Please clarify if your windows is working correctly.

---

### Post by bcbc on 2012-12-23
Dell's come with a boot partition. I have a recent Win 7 Dell (more than one actually). You can see all the partitions through the disk management console.

You're not the first to get this problem. If you go to an CMD.EXE prompt that you "Run as Adminstrator" and run "bcdedit" it will give you the same error. The fix(es) I have provided seem to work for other people. I'm not aware of any other fixes. (And this is unrelated to Ubuntu or Wubi).

---

