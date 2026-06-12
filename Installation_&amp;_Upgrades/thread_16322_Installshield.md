---
title: "Installshield"
date: 2005-02-20
forum: Installation &amp; Upgrades
---

### Post by dado on 2005-02-20
I have installed wine its working good but then i want to install Macromedia Flash MX and i get error something like this:
Installshield Engine is missing Ikernel.exe cannot be found
Where can i download Installshield engine????

---

### Post by kassetra on 2005-02-20
Here is the whole installshield set you'll need: (2Mb)
 
 [InstallShield.zip]("http://www.linuxpeach.com/ubuntu/installshield.zip")

---

### Post by dado on 2005-02-20
BROKEN LINK

---

### Post by kassetra on 2005-02-20
no need to yell!
 
 I fixed the link.

---

### Post by dado on 2005-02-20
Thanks
and sorry

---

### Post by kassetra on 2005-02-20
Does your wine installation of flash mx work now?

---

### Post by dado on 2005-02-20
Where must i extract files from archive?(installshield.zip)

---

### Post by kassetra on 2005-02-20
to the fake c:\...\program files\common or program filesc:\...\common files directory.

---

### Post by dado on 2005-02-20
Its not working i still get this error:
The Installshield Engine (iKernel.exe) could not be launched.(0X80004005)

---

### Post by kassetra on 2005-02-20
ok, try dumping that archive into the fake:
  C:\Documents and Settings\username\Application Data

---

### Post by dado on 2005-02-20
C:\Documents and Settings\username\Application Data
This folder doesn't exist should i create one?
This is folders of C:
My Documents
Program Files
windows

---

### Post by kassetra on 2005-02-20
which windows version are you emulating with wine?

---

### Post by dado on 2005-02-20
This i dont know where can i look for that???

---

### Post by kassetra on 2005-02-20
[QUOTE=dado]This i dont know where can i look for that???[/QUOTE]
    
    Open /home/username/.wine/config in a text editor, and look for something like this:
     ```
[Version]
   ; Windows version to imitate (win95,win98,winme,nt351,nt40,win2k,winxp,win20,win30,win31)
  "Windows" = "win98"
```

---

### Post by dado on 2005-02-21
This file does not exist in this folder i have only this files:
dosdevices
drive_c
system.reg
userdef.reg
user.reg

---

### Post by Jad on 2005-02-21
I would go with CrossOver for such applications

---

### Post by poofyhairguy on 2005-02-21
[QUOTE=Jad]I would go with CrossOver for such applications[/QUOTE]

amen.

---

### Post by dado on 2005-02-22
Where can i download this?

---

