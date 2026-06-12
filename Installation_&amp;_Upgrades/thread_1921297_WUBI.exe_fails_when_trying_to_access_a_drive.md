---
title: "WUBI.exe: fails when trying to access a drive"
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by vieridipaola on 2012-02-06
My computer has 3 disk drives (c:, d:, z: ) and 4 "removable disks" (f:, g:, h:, i: - Windows 7). Actually, the 4 removable disks are empty and ejected (they correspond to the 4 slots on my integrated card reader which I cannot simply disconnect).

When I run WUBI from drive C: to install Ubuntu on Windows, I tell it to install to drive D:.

It fails after unpacking the downloaded image because it tries to access drive F:... Why in the world is it trying to do that? (see log snippet below)

Also, if I run WUBI again and choose the same install parameters, it download the whole image again... Shouldn't it be "smart enough" not to re-download it if it already has a valid local copy?

log:
```

02-06 19:07 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
02-06 19:07 DEBUG  TaskList: ## Finished choose_disk_sizes
02-06 19:07 DEBUG  TaskList: ## Running expand_diskimage...
02-06 19:12 DEBUG  TaskList: ## Finished expand_diskimage
02-06 19:12 DEBUG  TaskList: ## Running create_swap_diskimage...
02-06 19:12 DEBUG  TaskList: ## Finished create_swap_diskimage
02-06 19:12 DEBUG  TaskList: ## Running modify_bootloader...
02-06 19:12 DEBUG  TaskList: New task modify_bcd
02-06 19:12 DEBUG  TaskList: ### Running modify_bcd...
02-06 19:12 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 364951.003906 mb free ntfs)
02-06 19:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {2a688e26-c170-11e0-a98a-c52aba0c14de}
02-06 19:12 DEBUG  TaskList: ### Finished modify_bcd
02-06 19:12 DEBUG  TaskList: New task modify_bcd
02-06 19:12 DEBUG  TaskList: ### Running modify_bcd...
02-06 19:12 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 111385.738281 mb free ntfs)
02-06 19:12 DEBUG  WindowsBackend: BCD has already been modified
02-06 19:12 DEBUG  TaskList: ### Finished modify_bcd
02-06 19:12 DEBUG  TaskList: New task modify_bcd
02-06 19:12 DEBUG  TaskList: ### Running modify_bcd...
02-06 19:12 DEBUG  WindowsBackend: modify_bcd Drive(F: removable 0.0 mb free )
02-06 19:12 DEBUG  WindowsBackend: BCD has already been modified
02-06 19:12 DEBUG  TaskList: ### Finished modify_bcd
02-06 19:12 DEBUG  TaskList: New task modify_bcd
02-06 19:12 DEBUG  TaskList: ### Running modify_bcd...
02-06 19:12 DEBUG  WindowsBackend: modify_bcd Drive(G: removable 0.0 mb free )
02-06 19:12 DEBUG  WindowsBackend: BCD has already been modified
02-06 19:12 DEBUG  TaskList: ### Finished modify_bcd
02-06 19:12 DEBUG  TaskList: New task modify_bcd
02-06 19:12 DEBUG  TaskList: ### Running modify_bcd...
02-06 19:12 DEBUG  WindowsBackend: modify_bcd Drive(H: removable 0.0 mb free )
02-06 19:12 DEBUG  WindowsBackend: BCD has already been modified
02-06 19:12 DEBUG  TaskList: ### Finished modify_bcd
02-06 19:12 DEBUG  TaskList: New task modify_bcd
02-06 19:12 DEBUG  TaskList: ### Running modify_bcd...
02-06 19:12 DEBUG  WindowsBackend: modify_bcd Drive(I: removable 0.0 mb free )
02-06 19:12 DEBUG  WindowsBackend: BCD has already been modified
02-06 19:12 DEBUG  TaskList: ### Finished modify_bcd
02-06 19:12 DEBUG  TaskList: New task modify_bcd
02-06 19:12 DEBUG  TaskList: ### Running modify_bcd...
02-06 19:12 DEBUG  WindowsBackend: modify_bcd Drive(Z: hd 81560.5898438 mb free ntfs)
02-06 19:12 DEBUG  WindowsBackend: BCD has already been modified
02-06 19:12 DEBUG  TaskList: ### Finished modify_bcd
02-06 19:12 DEBUG  TaskList: ## Finished modify_bootloader
02-06 19:12 DEBUG  TaskList: ## Running diskimage_bootloader...
02-06 19:12 DEBUG  WindowsBackend: Copying C:\Users\Vieri\AppData\Local\Temp\pyl9F1C.tmp\winboot -> D:\ubuntu\winboot
02-06 19:12 ERROR  TaskList: [Errno 13] Permission denied: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'F:\\wubildr'
02-06 19:12 DEBUG  TaskList: # Cancelling tasklist
02-06 19:12 ERROR  root: [Errno 13] Permission denied: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'F:\\wubildr'
02-06 19:12 DEBUG  TaskList: # Finished tasklist

```Thanks

Vieri

---

### Post by darkod on 2012-02-06
I don't use wubi but if I understand this right, the wubildr goes where your boot partition is. Is that F: ?

The wubi.exe will try to download every time except if you have the ISO of the exact same version together with the wubi.exe in the same folder. In that case it will detect and use the ISO.

But only if they are in the same folder and same version.

One thing you could do to make sure the version is the same, don't download wubi.exe but instead download the ISO you want, and extract the wubi.exe from it (it's inside). Then put them in the same folder and run the exe with right-click, Run As Administrator.

In Vista and 7 the exe needs to be run with elevated permissions, maybe that's what is bothering it right now.

My personal opinion is to install a proper dual boot, but your choice if you wanna go with wubi. Just note that it was never meant as long term install and it can break during updates/upgrades. Don't think that it will also happen in the proper install.

---

### Post by bcbc on 2012-02-06
This is bug [lpbug]862003[/lpbug]. The install is successful.

---

