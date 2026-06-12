---
title: "Installing MS Office 2007"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by donaldkm on 2009-11-22
I would like to start out by saying that I really enjoy Ubuntu 9.1. My main reason for wanting to install MS Office 2007 is that, I really do not have the time to learn another programming language. The other reason is that all my projects are either done in Excel VBA or in Visual Studio and the code doesn't migrate without a lot of effort or not at all. I have tried all of the helpful links on this subject, but I guess I have a mental block, because nothing seems to work. I am using Wine 1.1.33 and have tried installing the items one at a time with the following problems:
1. DotNet11 aborts at the end or near the end after the download and execution of the installation file.
2. MSXML3, MSXML4, MSXML6 abort with error code 103 and the Windows Installer 2.0 will not load (I suspect DotNet11 affects this)
I have removed, reloaded and deleted directories more than I can remember, and to tell you the truth it may have been quicker to learn OpenOffice.org Basic. If anyone can help I would appriciate it.

---

### Post by darco on 2009-11-22
I havent played much w/Wine but an easy solution is to download Virtualbox and install Windows in a virtual environment. I personally use VMWare Workstation which is expensive but VB is free. Its great to just boot up Windows while I am still in my Linux box and go from there. I use Outlook for work.



darco

---

### Post by Mark Phelps on 2009-11-23
Installing .net and Office 2007 are especially difficult to do successfully in Wine.  Suggest you go to the Wine subforum here and do searches on these topics.  You will find some threads that contain some details on how to get this working.  But, be advised, .Net versions newer than 3x will simply NOT work in Wine.

---

### Post by donaldkm on 2009-11-24
> **donaldkm said:**
> I would like to start out by saying that I really enjoy Ubuntu 9.1. My main reason for wanting to install MS Office 2007 is that, I really do not have the time to learn another programming language. The other reason is that all my projects are either done in Excel VBA or in Visual Studio and the code doesn't migrate without a lot of effort or not at all. I have tried all of the helpful links on this subject, but I guess I have a mental block, because nothing seems to work. I am using Wine 1.1.33 and have tried installing the items one at a time with the following problems:
1. DotNet11 aborts at the end or near the end after the download and execution of the installation file.
2. MSXML3, MSXML4, MSXML6 abort with error code 103 and the Windows Installer 2.0 will not load (I suspect DotNet11 affects this)
I have removed, reloaded and deleted directories more than I can remember, and to tell you the truth it may have been quicker to learn OpenOffice.org Basic. If anyone can help I would appriciate it.
I was finally able to load Office 2007 by selecting Windows Vista in Wine and removing all overrides. However, .net framework failed to install in winetricks. Tried to run Excel but failed to start, as did all of the Office applications. Changed configuration to Windows XP, Excel started by froze, restarted Ubuntu 9.1 and changed configuration to Windows 2000. Excel started but gave an error to opt to run in safe mode, selected safe mode, received the same indications. Still trying to work on the .net problem, but if anyone has any help as far as running the applications I would appreciate it.

---

### Post by itoffshore on 2010-12-15
This worked for me in the latest stable version of WINE:

[Install Office 2007 in WINE]("http://mediakey.dk/~cc/howto-office-2007-on-linux-with-wine/")

If you need to run VBA install Office XP or 2003 as currently in 2007 there is a problem with MS Active X Data Objects 2.5 not loading (msado15.dll) registering this dll with regsvr32 fails.

---

