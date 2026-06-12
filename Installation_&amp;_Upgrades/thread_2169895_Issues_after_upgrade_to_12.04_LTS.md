---
title: "Issues after upgrade to 12.04 LTS"
date: 2013-08-23
forum: Installation &amp; Upgrades
---

### Post by matthew-hardin on 2013-08-23
So I had a perfectly fine working 10.04 system that I recently upgraded to 12.04 LTS. This is a headless system that I use NoMachine NX to access. I prefer gnome over Unity so I made the appropriate changes after the upgrade to get a gnome interface. The issues I will describe below behave the same regardless of Unity or Gnome.

LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise


So I have two issues that I can't resolve.
1)  Bacula Admin Tool will not display anything. I've looked at the bacula logs and the actual backup engine seems to be doing as expected without issue. I.e. I'm confident that my backups are being performed. However when I launch the bacula admin tool (bat) all I get is a dialog window with absolutely nothing in it and no menu's or such to do anything with. It is just an empty dialog window that I can move, resize, minimize, close... but nothing in the window.

I have not tried to uninstall/reinstall bacula. I fear going through the pain of getting my backups working properly again. 

2) Pidgin will not run. When I start it up it will flash some windows up but they will immediately close. I cannot find anything logged in the .purple log files in the user directory. I can't seem to find any other log files for Pidgin.  I have tried uninstall/reinstall of Pidgin. Deleted my .purple directory and still it behaves the same.


Both of these issues seem to either be UI related or permission related but I haven't been able to resolve them and not even sure where to look to solve them. I say they may be UI related but keep in mind that they didn't work in Unity either. Now I have Gnome running properly for everything else (that I've tried so far) and they still do not work.


Any help I can get with this would be appreciated.

Thanks,
Matthew

---

### Post by matthew-hardin on 2013-08-23
[ATTACH=CONFIG]245655[/ATTACH]

This is what the bacula admin tool appears like for me.

---

### Post by SweetAurora on 2013-08-23
Looks llike the upgrade was botched, a common occurance. 

In a terminal:
```
 sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install --fix-policy 
```

That could be a start, if there are errors, report here please.

---

### Post by matthew-hardin on 2013-08-24
So I ran those commands. There were updates that were done. Rebooted. Reconnected via NX and still have the same issues.  I did not see any errors reported during the updates.

---

### Post by matthew-hardin on 2013-08-24
Any other suggestions of what I could look at to resolve this?

---

### Post by matthew-hardin on 2013-08-26
Is there another room on the forums, or another forum, someone could suggest to where I might be able to get some help with this?

---

### Post by mastablasta on 2013-08-27
it could be a NoMachine NX issue

---

### Post by matthew-hardin on 2013-08-27
> **mastablasta said:**
> it could be a NoMachine NX issue

That is a possibility. This is a headless unit that would require me moving it to test that theory which will require me to have the time to do so.
However, I'm doubtful that is the case as NX is just an X-Window medium. So it is just displaying things from a video perspective and doesn't care wether it's gnome, unity, kde or whatever. The fact that the windows show up (and disappear in the pidgin case, as if it just errors out) lends me to think that its not NX.

---

### Post by matthew-hardin on 2013-09-06
So the Bacula problem I'm having does appear to be an X issue possibly or an authorities + X issue. But I'm still having very little luck in resolving it. 
It was suggested to me to try running the program from the command line which gave me the following errors:

```

X Error: BadAccess (attempt to access private resource denied) 10
  Extension:    129 (MIT-SHM)
  Minor opcode: 1 (X_ShmAttach)
  Resource id:  0x2800001
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    129 (MIT-SHM)
  Minor opcode: 5 (X_ShmCreatePixmap)
  Resource id:  0x280008a
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x280008b

```

So I took a look at the .xsessions.errors file but there are no recent entries for this file.
I also looked at if there were any Xorg log files in /var/log.  There are no recent log files for it either.
I see no relevant entries in the /var/log/auth log file either.
I've also googled the above X Errors but haven't been able to find anything that suggested a help for me.

Any help would be appreciated.

---

