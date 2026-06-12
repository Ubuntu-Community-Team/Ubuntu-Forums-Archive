---
title: "Running EasyC with WINE(general WINE question)"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by xelapond on 2007-03-29
I am not having much luck with linux, but more then i have had with wondoze:lolflag: 

Anyway, i installed WINE using a wonderful utility called simple64, but when i try and run anything, in this case the EasyC program for the vex robotics system, i get the following output:

alex@alex-desktop:~$ wine easyc.exe
err:module:import_dll Library MFC71.DLL (which is needed by L"C:\\windows\\easyc.exe") not found
err:module:import_dll Library MSVCR71.dll (which is needed by L"C:\\windows\\easyc.exe") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\windows\\easyc.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\easyc.exe" failed, status c0000135
alex@alex-desktop:~$ 

It also will not install visual studio express.

Any ideas?

BTW, i am running Edgy on an AMD64 system.

---

### Post by spin2cool on 2007-03-30
You need to check in with the WINE DB to see if your applications are supported and/or functional under WINE.  I'm willing to bet that Visual Studio is not.  [http://appdb.winehq.org/](http://appdb.winehq.org/)

You'll probably be better off using natively linux code editors.  Personally, I just use emacs and GCC, but there are development programs like Vis Studio for linux - search the forums and google and you should find some good alternatives.

---

