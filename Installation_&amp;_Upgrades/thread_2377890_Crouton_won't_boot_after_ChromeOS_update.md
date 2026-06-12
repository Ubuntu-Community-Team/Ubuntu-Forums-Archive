---
title: "Crouton won't boot after ChromeOS update"
date: 2017-11-17
forum: Installation &amp; Upgrades
---

### Post by sduverge on 2017-11-17
I have an HP Chromebook, I have been booting Xubuntu from Crouton for the past 3 months, occasional updates made no changes to Crouton.

Today, latest update left crouton out of service, I need to boot back in or at least take out certain files before doing a wipe out. I need access to the hidden partition Crouton makes to install Linux (at least).

I keep getting this message when I try to start xubuntu and it gets stuck at 24% and logs out.
crosh> shell
chronos@localhost / $ sudo enter-chroot startxfce4
Entering /mnt/stateful_partition/crouton/chroots/xenial...
A chroot setup script still exists inside the chroot.
The chroot may not be fully set 

```
crosh> shellchronos@localhost / $ sudo enter-chroot startxfce4
Entering /mnt/stateful_partition/crouton/chroots/xenial...
A chroot setup script still exists inside the chroot.
The chroot may not be fully set up.
Would you like to finish the setup? [Y/n/d]
``` 

and then this error
```
Error org.freedesktop.DBus.Error.UnknownMethod: Method "ReleaseDisplayOwnership" with signature "" on interface "org.chromium.LibCrosServiceInterface" doesn't exist

xf86EnableIOPorts: failed to set IOPL for I/O (Operation not permitted)
Error org.freedesktop.DBus.Error.UnknownMethod: Method "ReleaseDisplayOwnership" with signature "" on interface "org.chromium.LibCrosServiceInterface" doesn't exist


xf86EnableIOPorts: failed to set IOPL for I/O (Operation not permitted)
(EE) 
Fatal server error:
(EE) AddScreen/ScreenInit failed for driver 0
(EE) 
(EE) 
Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
(EE) Please also check the log file at "/tmp/Xorg.crouton.1.log" for additional information.
(EE) 
Error org.freedesktop.DBus.Error.UnknownMethod: Method "TakeDisplayOwnership" with signature "" on interface "org.chromium.LibCrosServiceInterface" doesn't exist


(EE) Server terminated with error (1). Closing log file.
/usr/bin/xinit: giving up
/usr/bin/xinit: unable to connect to X server: Connection refused
/usr/bin/xinit: server error
Unmounting /mnt/stateful_partition/crouton/chroots/xenial...
```

Please help!!! I have 2 files that I desperately need! Though I have backups, they are not updated.
chronos@localhost / $ sudo enter-chroot startxfce4
Entering /mnt/stateful_partition/crouton/chroots/xenial...
A chroot setup script still exists inside the chroot.
The chroot may not be fully set[/CODE]

---

### Post by TheFu on 2017-11-18
I haven't used crouton in a few years.

Back then, crouton backups were just tar-gz files.  You should be able to make a fresh backup (assuming you know the password). That will created the unencrypted tgz file.  Then just gunzip it and pull the files you want from the tar.  If the backups are over 4G in size, I read that crouton uses 'split' to break them up.  Use 'join' to put the files back together before gunzip and tar steps.

Weekly backups are a good idea, since we never know when google is going to push an unwanted update that breaks crouton.  Then there is usually a few day wait as a new version of the libraries are created so crouton will work again.  That is why I stopped using ChromeOS. 1 of the reasons., anyway.  I was in a poorly connected country and google pushed an update without asking, no way to stop it.  How rude.

---

