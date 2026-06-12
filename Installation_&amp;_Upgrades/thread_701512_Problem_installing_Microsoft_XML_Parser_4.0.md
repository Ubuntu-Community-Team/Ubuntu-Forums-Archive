---
title: "Problem installing Microsoft XML Parser 4.0"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by sbaxter on 2008-02-19
I am running Feisty 7.04, and have installed IES4Linux w/o a problem. I  am trying to view a web site which requires that I install Microsoft XML Parser 4.0 or above in order to run properly.

Downloaded msxml.msi and msxml6.msi, tried to install as follows:

 msiexec /i msxml6.msi

The GUI in front seemed to install properly, but the background data in terminal does not look right:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
fixme:advapi:LookupAccountNameW (null) L"sbaxter" (nil) 0x34f7fc (nil) 0x34f800 0x34f7f4 - stub
fixme:advapi:LookupAccountNameW (null) L"sbaxter" 0x1608a8 0x34f7fc 0x15edb8 0x34f800 0x34f7f4 - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 3 ignored L"Upgrade" table values
fixme:msi:ControlEvent_HandleControlEvent unhandled control event L"Reinstall" arg(L"ALL")
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 3 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 3 ignored L"Upgrade" table values


After restarting IE4Linuix again, the XML 4.0 error message reoccurs.  What am I doing wrong,or is there an easier way to display the web site?

Thanks,
SB

---

