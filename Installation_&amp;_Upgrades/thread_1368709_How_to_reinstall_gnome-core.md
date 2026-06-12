---
title: "How to reinstall gnome-core?"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by Putnam11 on 2009-12-31
So a few days ago I tried to resize my partitions to give windoes more space using gparted, but I thought it failed... Yesterday it couldn't mount the filesystem so I ran ubuntu in maintenence mode and ran fsck. I can use ubuntu 9.10 now, but can't access any directories, such as computer, home, pictures, network, etc.  Every other program runs fine.  I tried typing nautilus into terminal and wow! Segfault! So I want to uninstall and reinstall gnome-core. I tried to remove via Ubuntu Software Center, but it says 'Waiting for other software managers to quit.' Nothing else is running afaik.
here's the nautilus error
```
bridger@laptop:~$ nautilus

(nautilus:2331): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:2331): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2331): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2331): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Segmentation fault
bridger@laptop:~$ 

```

so yea, halp!

---

### Post by Jekshadow on 2009-12-31
Why remove gnome-core, instead of nautilus itself?

[SIZE="5"]This is just the generic reinstall command I use, so be warned that removing nautilus may remove your entire GUI, leaving you with a command line only system. To reinstall the desktop, just type 'sudo apt-get install ubuntu-desktop' into the command line.
[/SIZE]

Short version:
```
sudo su -c 'apt-get remove nautilus -y && apt-get install nautilus -y'
```

Long version:
```

sudo apt-get remove nautilus
sudo apt-get install nautilus

```

---

### Post by Jekshadow on 2010-01-01
Now I'm getting the same exact error, down to the character.

Here is what is left in my dmesg:
```
[  539.551623] nautilus[3097]: segfault at 7f40d416dff8 ip 00007f40dbe6c6bd sp 00007f40d416dff0 error 6 in libc-2.10.1.so[7f40dbd9b000+166000]

```

I purged nautilus and installed it, and the same problem occured.

What happened immediately before the problem started is I had accidentally caused an infinite loop in a threaded python program, causing both of my cores to 100%, resulting in a frozen system. When I hard restarted my computer, everything worked except nautilus, which began giving me the error.

---

### Post by Putnam11 on 2010-01-01
well good-luck, Im ditching this laptop tomorrow, installing winblows fully then giving it to my dad, I bought a $1200 computer :DDD:P

---

