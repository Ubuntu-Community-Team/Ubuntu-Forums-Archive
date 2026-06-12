---
title: "Register DLL files in ubuntu 9.10 (upgraded)??"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by dilshannet on 2010-01-13
I need to register some dll files in ubuntu. I used following command n it gives an error,

[HTML]Z:\home\tharaka>regsvr32  "C:\Program Files\Union Assurance HRM\Alerts.dll" 
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\Program Files\\Union Assurance HRM\\Alerts.dll") not found
Failed to load DLL C:\Program Files\Union Assurance HRM\Alerts.dll
[/HTML]

---

### Post by sliketymo on 2010-01-13
A DLL file is a windows file my friend.It will not work natively in Linux,it will need a little help,like maybe Wine.

---

### Post by dilshannet on 2010-01-19
> **sliketymo said:**
> A DLL file is a windows file my friend.It will not work natively in Linux,it will need a little help,like maybe Wine.

I have inatalled WINE. The command regsvr32 is there but it gives an error when i try to register dlls.

---

### Post by sliketymo on 2010-01-19
> **dilshannet said:**
> I need to register some dll files in ubuntu. I used following command n it gives an error,

[HTML]Z:\home\tharaka>regsvr32  "C:\Program Files\Union Assurance HRM\Alerts.dll" 
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\Program Files\\Union Assurance HRM\\Alerts.dll") not found
Failed to load DLL C:\Program Files\Union Assurance HRM\Alerts.dll
[/HTML]

Looks like your missing some pieces to your puzzle.

---

