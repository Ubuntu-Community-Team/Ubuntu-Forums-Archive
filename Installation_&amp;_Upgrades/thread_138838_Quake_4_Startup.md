---
title: "Quake 4 Startup"
date: 2006-03-02
forum: Installation &amp; Upgrades
---

### Post by R3linquish3r on 2006-03-02
Im getting the following error when I try to run Quake 4.... Not really sure what it means but igured someone here would. :)

```
found DLL in pak file: /usr/local/games/quake4/q4base/game100.pk4/gamex86.so
copy gamex86.so to /home/ed/.quake4/q4base/gamex86.so
WARNING: idFileSystemLocal::OpenFileRead: fs_caseSensitiveOS 1 could not open /home/ed/.quake4/q4base/gamex86.so
Regenerated world, staticAllocCount = 0.
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

Shutting down sound hardware
------ OSS Sound Shutdown ------
close sound device
--------------------------------
idRenderSystem::Shutdown()
Sys_Error: could not create destination file /home/ed/.quake4/q4base/gamex86.so
```

---

### Post by R3linquish3r on 2006-03-02
Never mind. Turns out I have to launch it with sudo. Kinda gay but thats how it goes :/

---

### Post by Ptero-4 on 2006-03-02
Is "ed" your user account? b/c if it is then you would not need to use sudo since AFAICS that path in the error msg indicates a folder in the "ed" home directory.

---

### Post by R3linquish3r on 2006-03-02
yeah ed is the user account. but when i open consol nd just type "quake4" i get that error. When I type "sudo quake4" the game runs fine.....

---

### Post by Ptero-4 on 2006-03-03
You should check file/directory permissions b/c quake should be able to write to your home folder from your user account.

---

### Post by Simian on 2006-03-13
[QUOTE=Ptero-4]"Some people says that if you play a Windows XP install CD backwards you will hear demon voices commanding you to worship Satan". But that's nothing. If you play it forward it will install Windows XP.[/QUOTE]
 LOL I love your sig Ptero-4

---

