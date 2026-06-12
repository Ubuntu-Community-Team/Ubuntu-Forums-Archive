---
title: "Wine: Issues with updating."
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by Equiflux on 2008-01-25
Hey Ubuntu Forums forum goers,

I tried to update my Wine installation from 0.9.3x to 0.9.53 using WineHQ's APT repository; Then I ran into some trouble:
[INDENT]-I can't run anything using the "Run application with Wine..." from the right-click menu.[/INDENT]
[INDENT]-When I try to run any exe with Wine in Terminal, I get something like this message:[/INDENT]

> Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/media/disk/AppDirectory/Application.exe', starting in the Windows directory.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\Application.exe": Module not found

[INDENT]-When I try to install Wine in Terminal, I get this error after typing "sudo apt-get install wine":[/INDENT]
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

[INDENT]-I tried this: "sudo dpkg -r wine" but I got another error:[/INDENT]
> dpkg: status database area is locked by another process

---
I'm using Gutsy.

---

### Post by FuturePilot on 2008-01-25
Make sure you don't have Synaptic or any other package manager open when running that command.

---

### Post by Equiflux on 2008-01-26
Thanks, but now I just have this problem:
> Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/media/disk/AppDirectory/Application.exe', starting in the Windows directory.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\Application.exe": Module not found

---

### Post by FuturePilot on 2008-01-26
Does the application you're trying to run happen to be on a USB driver or something?

---

### Post by Equiflux on 2008-01-26
No, and it's not just one application though; this happens with every application I try to run with Wine. When I look in my wine directory, there are no drive_c and WINDOWS directories.

---

### Post by FuturePilot on 2008-01-26
Run
```
winecfg
```
and then see if those directories show up.

---

### Post by Equiflux on 2008-01-27
Winecfg starts; after a while that is. Before it starts I still get the errors about not finding a c drive and windows directory.

When I try to add a new drive and browse for a path for it, I get this error in terminal:
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\user\\Desktop".

---

### Post by Equiflux on 2008-01-27
I found a solution to my problem here:
[http://ubuntuforums.org/showthread.php?p=4215903](http://ubuntuforums.org/showthread.php?p=4215903)

I think my problem was that "wineprefixcreate" wasn't run during installation.

---

