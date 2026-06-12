---
title: "error after finished upgrade"
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by kknoas on 2008-10-12
hello

i was updating to version 8.04 ... and when they were missing a few minutes to finish, the light is gone .. : (, I returned to turn on the computer and I do not load any option of ubuntu. What can I do?, I have another partition with windows on the computer ...

Is there any option to update the version without having to lose what i had before? Or go to the light, has been left half .. and no longer has meaning?

thanks

---

### Post by Partyboi2 on 2008-10-12
If you can get to a terminal (Ctrl+Alt+F2) or boot into recovery mode then try in this order
```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by kknoas on 2008-10-13
i can't get to a terminal and i can't boot into recovery mode. When i try to boot into recovery mode, it's stop in this message: "[]Kernel panic- not syncing: VFS: unable to mount root fs on unknown-block(0,0)".

after it, i only can reboot the computer... :(

thanks

one question: if i try with a live cd, i can try the orders??? or there is another option with the live cd?¿?

---

### Post by Partyboi2 on 2008-10-13
If you have a ubuntu live cd you could try chroot into your ubuntu installation and try those previous commands
Boot a ubuntu live cd and open a terminal and[FONT=monospace]
[/FONT]```
sudo mkdir /media/hardy 
```[FONT=monospace]
[/FONT]```
sudo mount /dev/sda1 /media/hardy
``` You will need to change sda1 for the correct one of your installation.[FONT=monospace]
[/FONT]```
sudo chroot /media/hardy
```Then

```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jantra on 2008-10-13
More info on error message...

---

### Post by kknoas on 2008-10-13
i used a live cd, and i try those commands, but an error appears after the "sudo dpkg --configure -a" command finished:

```

.....
dpkg: dependency problems prevent configuration of eog:
 eog depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 eog depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-monitor:
 gnome-system-monitor depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-system-monitor (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted
```

then i try: 
```

root@ubuntu:/# sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
root@ubuntu:/# 
```

what can i do?

thanks

---

### Post by kknoas on 2008-10-13
i tried again, but when i used this command: ```
dpkg --configure -a
```, appeared errors in "dbus" package,..and all the others packages can't be configured because an error appears in "dbus"

---

### Post by Partyboi2 on 2008-10-13
I have pretty much  ran out of ideas, maybe someone else might know where to go from here. One option you may need to look at is to use the live cd to backup any data you want to keep to another source and do a fresh install. Hopefully someone else might have other suggestions.

---

