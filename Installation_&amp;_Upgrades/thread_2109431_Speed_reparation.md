---
title: "Speed reparation?"
date: 2013-01-27
forum: Installation &amp; Upgrades
---

### Post by jojomeuh on 2013-01-27
Hello,

I tried to create a bootable SDcard on gumstix (for the ones that know that). 

A part of this process was to download the rootfs.tar.bz2 here

[http://cumulus.gumstix.org/images/angstrom/misc/caspapx/](http://cumulus.gumstix.org/images/angstrom/misc/caspapx/)

I wanted to know what's in it and I when I decompressed it, it starts to install stuffs and change the libraries etc. In fact it's supposed to do that job on the micro SD card to have there and Angstrom distribution. 

The problem is that my ubuntu doesn't really work now.

Is there a way to recover ubuntu as it should be?

I've a back up of my important documents so I don't mind reinstall ubuntu or smth like that. Isn't there a way to simply upgrade ubuntu and then all will be changed to the next version with the correct libraries and so on ?

Thanks

---

### Post by TheFu on 2013-01-27
I'd like to help, but can't understand what happened.

Either Ubuntu works or it doesn't.  Can you elaborate on the specific, exact issue(s) please? *"Doesn't really work"* is a little vague.

> Is there a way to recover ubuntu as it should be?
Perhaps. Do you have a backup? If so, use that to recover.

If the current version of ubuntu on your machine is not in a known-good-state, it is likely that any update process (from 11.10 or 12.04 as an example) will fail.

In the future, if you are trying to de-tar stuff that uses absolute paths, it would be smart to **not**
a) run as root
b) have an important file system available that you **do not want** to be overwritten

Live and learn.  I was burned by doing something similar about 20 yrs ago. 
I never forgot that lesson. ;)

---

### Post by jojomeuh on 2013-01-28
I will be kind... I'll help you to help me :D

The tutorial I used is here:

[http://www.gumstix.org/create-a-bootable-microsd-card.html](http://www.gumstix.org/create-a-bootable-microsd-card.html)

The point I did wrong that :

[INDENT]Expand the root file system archive on to the second partition: 
$ sudo tar xaf roofs.tar.bz2 -C /media/rootfs 
$ sync
[/INDENT]
I wanted to see what was inside. I tough that it was just
some compressed file or bunch of files. The point it installs
the rootfs it means it changes a lot of libraries and settings.

I mean I opened it at first not in an external device but my 
hard disk... (as you've probably understood yet) 
It's difficult to know what doesn't work properly but when you see all the details it
changes you say "oho.... there may be dangerous changes done here". The first problem
is the lack of the launch bar but I guess there a more problems I've encountered yet.

You can see what the extraction does on a free disk on key.

(I don't have a real backup, only a copy of important files)

Thanks for all

---

### Post by jojomeuh on 2013-01-28
a bit more informations:

(trying to recover launcher)


```
bash: /home/yaacov/bin/ls: cannot execute binary file
yaacov@yaacov-laptop:~$ sudo unity --reset-icons
[sudo] password for yaacov: 
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
unity-panel-service: no process found
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite

(process:2228): GLib-WARNING **: In call to g_spawn_sync(), exit status of a child process was requested but SIGCHLD action was set to SIG_IGN and ECHILD was received by waitpid(), so exit status can't be returned. This is a bug in the program calling g_spawn_sync(); either don't request the exit status, or don't set the SIGCHLD action.
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (expo) - Warn: failed to bind image to texture
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
WARN  2013-01-28 14:04:58 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2013-01-28 14:04:58 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2013-01-28 14:04:58 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
ERROR 2013-01-28 14:04:58 unity.launcher.trashlaunchericon TrashLauncherIcon.cpp:61 Could not create file monitor for trash uri: Operation not supported
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.drag.threshold
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.drag.timeout
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.pinch.threshold
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.pinch.timeout
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.tap.threshold
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.tap.timeout
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.rotate.threshold
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.rotate.timeout
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.drag.threshold
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.drag.timeout
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.pinch.threshold
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.pinch.timeout
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.tap.threshold
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.tap.timeout
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.rotate.threshold
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.rotate.timeout
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.drag.threshold
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.drag.timeout
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.pinch.threshold
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.pinch.timeout
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.tap.threshold
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.tap.timeout
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.rotate.threshold
ERROR 2013-01-28 14:05:01 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.rotate.timeout
WARN  2013-01-28 14:05:01 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x1db1040

WARN  2013-01-28 14:05:01 unity <unknown>:0 Failed to fetch path: No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0x1db1040
WARN  2013-01-28 14:05:01 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x1db1040

WARN  2013-01-28 14:05:01 unity <unknown>:0 Failed to fetch icon: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x1db1040
WARN  2013-01-28 14:05:01 unity <unknown>:0 Failed to fetch name: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x1db1040
WARN  2013-01-28 14:05:01 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x1db1040
WARN  2013-01-28 14:05:01 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x1db1040
WARN  2013-01-28 14:05:01 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x1db1040
WARN  2013-01-28 14:05:01 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x1db1040

WARN  2013-01-28 14:05:01 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x1db1040

WARN  2013-01-28 14:05:01 unity <unknown>:0 Failed to fetch path: No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0x1db1040
WARN  2013-01-28 14:05:01 unity <unknown>:0 Failed to fetch path: No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0x1db1040
WARN  2013-01-28 14:05:01 unity <unknown>:0 Failed to fetch path: No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0x1db1040
WARN  2013-01-28 14:05:01 unity <unknown>:0 Failed to fetch path: No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0x1db1040
WARN  2013-01-28 14:05:01 unity <unknown>:0 Failed to fetch path: No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0x1db1040
WARN  2013-01-28 14:05:01 unity <unknown>:0 Failed to fetch type: No such interface `org.ayatana.bamf.window' on object at path /org/ayatana/bamf/window46137634
WARN  2013-01-28 14:05:42 unity.glib.dbusproxy GLibDBusProxy.cpp:291 Calling method "InfoRequest" on object path: "/net/launchpad/lens/video" failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.Unity.Lens' on object at path /net/launchpad/lens/video
WARN  2013-01-28 14:05:42 unity.glib.dbusproxy GLibDBusProxy.cpp:291 Calling method "SetViewType" on object path: "/net/launchpad/lens/video" failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.Unity.Lens' on object at path /net/launchpad/lens/video
WARN  2013-01-28 14:05:42 unity.glib.dbusproxy GLibDBusProxy.cpp:291 Calling method "InfoRequest" on object path: "/net/launchpad/lens/photos" failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.Unity.Lens' on object at path /net/launchpad/lens/photos
WARN  2013-01-28 14:05:42 unity.glib.dbusproxy GLibDBusProxy.cpp:291 Calling method "SetViewType" on object path: "/net/launchpad/lens/photos" failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.Unity.Lens' on object at path /net/launchpad/lens/photos

```

---

### Post by steeldriver on 2013-01-28
> **jojomeuh said:**
> 
$ sudo tar xaf roofs.tar.bz2 -C /media/rootfs 

I don't see why that would have had any effect on your installed / running system - it should have put everything under the /media directory (which is presumably a mounted pluggable / external device) 

Unless you were already chrooted to /media for some reason?

Are you sure that's what you did?

---

### Post by jojomeuh on 2013-01-28
The point is I did not do that command at first. I begun checking this file. Which means open it but in the wrong file. And what it supposed to do on the external media it did in my hard disk.

I found that:

[http://askubuntu.com/questions/184280/bash-filename-cannot-execute-binary-file](http://askubuntu.com/questions/184280/bash-filename-cannot-execute-binary-file)

Which suggests that 32 compiled do not match with 64 systems (if I understood correctly)

I get that kind of message:
bash: /home/yaacov/bin/ls: cannot execute binary file
or
/home/yaacov/bin/rm: 1: /home/yaacov/bin/rm: Syntax error: word unexpected (expecting ")")
or 
bash: /home/yaacov/bin/grep: cannot execute binary file

Given that the files to be tared are for 32 bit board, I suspect that event my simple application such as 
rm 
or 
grep
have been replaced by the one supposed to be on the 32 bit board. 

Repairing point by point seems to be a long and fastidious job. Isn't there a way to simply download and overwrite all that stuff?

---

### Post by TheFu on 2013-01-28
If you were not root and didn't use **sudo**, then you didn't harm your OS install. You could only harm YOUR settings in $HOME. That means you can probably create a new account and login to that and be perfectly happy.

Let me read the next msg.

---

### Post by TheFu on 2013-01-28
32-bit programs can run on 64-bit OSes if the right libraries are installed and the LD_LIBRARY_PATH includes those locations (which it probably does).  Any 64-bit x86 CPU can run 32-bit x86 programs (it is physically possible) provided the other software necessary supports that. 64-bit CPUs run 32-bit OSes all the time. This does not necessarily apply to other CPU families - but it is very unlikely that you have those CPUs at home and are running Ubuntu on them.

> is there a simply way to download and overwrite all that stuff?
Yes, there is. It is called a backup.  There are lots of other ways too, but I suspect you don't have the information needed to accomplish those either.  Backups rock.

How long does a reinstall take?  20 minutes?  If you don't have a backup, reinstall is the best answer.
Hopefully, you have a list of all the programs that you installed AND want to keep. If not, check out the **dpkg --get-selections** command.

I really think you should just create  a new account on the box and delete the old one. The OS is probably just fine.

---

### Post by steeldriver on 2013-01-28
> **jojomeuh said:**
> 
I get that kind of message:
bash: [COLOR=Red]/home/yaacov/bin/ls[/COLOR]: cannot execute binary file
or
[COLOR=Red]/home/yaacov/bin/rm[/COLOR]: 1: /home/yaacov/bin/rm: Syntax error: word unexpected (expecting ")")
or 
bash: [COLOR=Red]/home/yaacov/bin/grep[/COLOR]: cannot execute binary file


Those are not the **system** binary directories though

At the very worst, I would guess it's created a parallel filesystem in your **home** directory /home/yaacov, and when you try to execute commands it's finding the binaries in /home/yaacov/bin first because your PATH variable has /home/yaacov/bin ahead of /bin:/usr/bin etc.

So an immediate fix would be to remove /home/yaacov/bin from your PATH - beyond that, rescue any *actual* personal executables you may have had in /home/yaacov/bin and then delete the rest

---

### Post by jojomeuh on 2013-01-28
pfiuuuuu........


thanks a lot steeldriver

(thanks theFu too for the efforts)




.... I just hope I haven't caused too much damages trying to repair...


thanks it seems to work well now

):P

---

