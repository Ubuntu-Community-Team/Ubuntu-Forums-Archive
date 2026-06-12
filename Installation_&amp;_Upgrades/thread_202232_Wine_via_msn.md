---
title: "Wine via msn"
date: 2006-06-23
forum: Installation &amp; Upgrades
---

### Post by bekok on 2006-06-23
hey, 

I want to use msn messenger via wine, so i tried doing this in my commandline:
"wine msnmsgr.exe", but it didn't quite work.
I got an error namely:

```
err:module:import_dll Library MSVCR80.dll (which is needed by L"E:\\Program Files\\MSN Messenger\\msnmsgr.exe") not found
err:module:import_dll Library gdiplus.dll (which is needed by L"E:\\Program Files\\MSN Messenger\\msnmsgr.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"E:\\Program Files\\MSN Messenger\\MSNCore.dll") not found
err:module:import_dll Library gdiplus.dll (which is needed by L"E:\\Program Files\\MSN Messenger\\MSNCore.dll") not found
err:module:import_dll Library MSNCore.dll (which is needed by L"E:\\Program Files\\MSN Messenger\\msnmsgr.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"E:\\Program Files\\MSN Messenger\\ContactsUX.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"E:\\Program Files\\MSN Messenger\\MSNCore.dll") not found
err:module:import_dll Library gdiplus.dll (which is needed by L"E:\\Program Files\\MSN Messenger\\MSNCore.dll") not found
err:module:import_dll Library MSNCore.dll (which is needed by L"E:\\Program Files\\MSN Messenger\\ContactsUX.dll") not found
err:module:import_dll Library gdiplus.dll (which is needed by L"E:\\Program Files\\MSN Messenger\\ContactsUX.dll") not found
err:module:import_dll Library ContactsUX.dll (which is needed by L"E:\\Program Files\\MSN Messenger\\msnmsgr.exe") not found
err:module:import_dll Library CRYPTNET.dll (which is needed by L"E:\\Program Files\\MSN Messenger\\msnmsgr.exe") not found
err:module:import_dll Library WINHTTP.dll (which is needed by L"E:\\Program Files\\MSN Messenger\\msnmsgr.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"E:\\Program Files\\MSN Messenger\\msnmsgr.exe" failed, status c0000135

```

I dont know how to get it working and i hope you guys do... 
THanks in advance

---

### Post by aysiu on 2006-06-23
Is this because aMSN and GAIM are missing some critical feature?

---

### Post by bekok on 2006-06-23
I don't like aMsn, doesnt look fancy enough :P nah joking, i just have some extra function on msn via msn+ and other stuff... And I don't really like Gaim

---

### Post by aysiu on 2006-06-23
Just wanted to double-check.

Is it possible that MSN messenger simply doesn't work with Wine?

**Edit**: I guess it does...
[http://wiki.winehq.org/MSN_Messenger_webcam_support](http://wiki.winehq.org/MSN_Messenger_webcam_support)

---

### Post by bekok on 2006-06-23
I dunno really... I'm pretty new with Ubuntu firstly, let alone wine..

---

### Post by aysiu on 2006-06-23
I'm pretty new to Wine myself.

What I've generally found (obviously there are exceptions) is that Wine works really well for most Windows programs that can be run on Windows 98. But if the Windows program needs Windows 2000 or XP, Wine doesn't suffice.

---

### Post by bekok on 2006-06-23
Ke danx, i'll try it with an older version of msn which works on 98..

---

