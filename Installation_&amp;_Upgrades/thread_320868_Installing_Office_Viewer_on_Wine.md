---
title: "Installing Office Viewer on Wine"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by textguru on 2006-12-18
I have installed Xubuntu 6.06 and wanting to install Office 2003 viewer. Is it possible? Hope you can guide me on how to do this.

---

### Post by textguru on 2006-12-18
I already install wine but cannot install office viewer especially powerpoint viewer 2003 here is the prompt:

> 
helpdesk@mypc:~$ wine /home/softwares/ppviewer.exe
fixme:advapi:LookupAccountNameW (null) L"helpdesk" (nil) 0x34f808 (nil) 0x34f804 0x34f810 - stub
fixme:advapi:LookupAccountNameW (null) L"helpdesk" 0x16e0f0 0x34f808 0x16e108 0x34f804 0x34f810 - stub
fixme:msi:ACTION_AppSearchComponents AppSearch CompLocator (L"{FC780C4C-F066-40E0-B720-DA0F779B81A9}") unimplemented
fixme:msi:ACTION_AppSearchComponents AppSearch CompLocator (L"{C86C0B92-63C0-4E35-8605-281275C21F97}") unimplemented
fixme:msi:ACTION_AppSearchComponents AppSearch CompLocator (L"{CC29E94B-7BC2-11D1-A921-00A0C91E2AA2}") unimplemented
fixme:msi:ACTION_AppSearchComponents AppSearch CompLocator (L"{FC780C4C-F066-40E0-B720-DA0F779B81A9}") unimplemented
fixme:msi:ACTION_AppSearchComponents AppSearch CompLocator (L"{C86C0B92-63C0-4E35-8605-281275C21F97}") unimplemented
fixme:msi:ACTION_AppSearchComponents AppSearch CompLocator (L"{CC29E94B-7BC2-11D1-A921-00A0C91E2AA2}") unimplemented
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveODBC"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnpublishComponents"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterTypeLibraries"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveRegistryValues"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterClassInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterExtensionInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterProgIdInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterMIMEInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveShortcuts"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveDuplicateFiles"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveFolders"fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
helpdesk@mypc:~$


What does it mean?

---

### Post by WakkiTabakki on 2006-12-18
It probably means its not compatible with wine, not all windows apps are.
But, why not install OpenOffice, it's free, open source and can open and edit powerpoint files. Left the MSOffice-world years ago and haven't looked back once =)

/N

---

### Post by textguru on 2006-12-18
the problem is this:

1. I only have Slow PCs
2. Most presentation files were created on MS Office
3. I use viewer cause it was intended for presentation PC only (no editing)

Hope you got my point.

---

### Post by WakkiTabakki on 2006-12-18
> **textguru said:**
> the problem is this:

1. I only have Slow PCs
2. Most presentation files were created on MS Office
3. I use viewer cause it was intended for presentation PC only (no editing)

Hope you got my point.

Ahh, ok. Got it. Still Openoffice can open ppt:s and save any file as a pdf, thus even with a slow comp you can convert ppt to pdf and just use acrobat when presenting...

But, yeah, it get your problem. Have you tried this one? [http://tonicsystems.com/products/viewer/]("http://tonicsystems.com/products/viewer/")

/N

---

### Post by Biker on 2006-12-18
> **WakkiTabakki said:**
> It probably means its not compatible with wine, not all windows apps are.
But, why not install OpenOffice, it's free, open source and can open and edit powerpoint files. Left the MSOffice-world years ago and haven't looked back once =)
/N

Alle MS Office 2003 viewers runs fine here with CrossOver 5.0.3 so I think it must be compatible with Wine.

---

### Post by WakkiTabakki on 2006-12-18
I triedinstalling the ppviewer (should really be working, but what the hell, its morning, its monday...) and got the same message as you. But the thing is, it does install, and it does seem to work!

Check under 
```
~/.wine/drive_c/Program Files/Microsoft Office/Powerpoint Viewer
```
and you'll find a working installation!

/N

---

### Post by textguru on 2006-12-18
Yes I have seen the folder but I run it with an error. Probably you might help me by giving me the right way on running the program.

---

### Post by textguru on 2006-12-18
You are right, PowerPoint Viewer 2003 is working by the following command:
 
$wine "c:\Program Files\Microsoft Office\PowerPoint Viewer\PPTVIEW.EXE"
 
It works fine but I see difference on the presentation:
 
Text are all in one character (if you have a text of Hello, characters are all pilled up in one position, where letter "H" is located.
 
Also, is there a way where I can execute the viewer on a batch file? I dont want users to type in the command that I have indicated above.

---

### Post by textguru on 2006-12-19
just resolve the problem. It has something to do with fonts that I have. I have tried downloading arial font and install it and found the presentation working:

> sudo wget [http://switch.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/arial32.exe)
wine arial32.exe /Q


But it seems that this will only work if the presentation is using Arial font. Is there a way that I can download windows fonts so there will be no font related problem?

---

