---
title: "Crysis again"
date: 2008-09-26
forum: Installation &amp; Upgrades
---

### Post by aimrait on 2008-09-26
Hi according to [http://appdb.winehq.org/objectManager.php?sClass=application&iId=5880](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5880) there is no problem but when I tried to open I get an error like this ->

moss@moss:~$ cd '/home/moss/.wine/drive_c/Program Files/Electronic Arts/Crytek/Crysis/Bin32' 
[email]moss@moss:~/.wine[/email]/drive_c/Program Files/Electronic Arts/Crytek/Crysis/Bin32$ gksudo wine Crysis.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\moss\\.wine\\drive_c\\Program Files\\Electronic Arts\\Crytek\\Crysis\\Bin32\\Crysis.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\moss\\.wine\\drive_c\\Program Files\\Electronic Arts\\Crytek\\Crysis\\Bin32\\Crysis.exe" failed, status c0000135


I downloaded MSVCR80.dll and pasted into system32 folder too..nothing changed...

---

