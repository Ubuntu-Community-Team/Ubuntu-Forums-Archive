---
title: "Previous install /home headache!"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by Splork on 2010-08-10
OMG MY HEAD

The wife loaded windows partition up, then told windows to shutdown but unplugged the pc from the wall before windows did it's thing, so... the bootloader dissapeared, someone advised me to reinstall Lucid Lynx again so that I would get the bootloader back without too much trouble, did that, windows is still dead, don't care anymore, my Ubuntu old /home is in limbo, the space is used up but I can't access any of the files from the previous install. Thought that just having the same user account 'dave' wouldn't force the install to make a new one, I'm a fool.

I'm assuming this is the whole of the contents, but cannot see it:

```
dave@dave-desktop:/media/c4db98fa-0925-4511-972c-7e03e2777399/dave$ ls -al
total 12
drwxrwxrwx  3 dave dave 4096 2010-08-09 21:49 .
drwxrwxrwx 24 root root 4096 2010-08-10 12:49 ..
lrwxrwxrwx  1 dave dave   56 2010-08-09 21:43 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
drwxrwxrwx  5 dave dave 4096 2010-08-10 09:25 .cache
lrwxrwxrwx  1 dave dave   30 2010-08-09 21:43 .ecryptfs -> /home/.ecryptfs/dave/.ecryptfs
lrwxrwxrwx  1 dave dave   29 2010-08-09 21:43 .Private -> /home/.ecryptfs/dave/.Private
lrwxrwxrwx  1 dave dave   52 2010-08-09 21:43 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt
dave@dave-desktop:/media/c4db98fa-0925-4511-972c-7e03e2777399/dave$ 

```

I implore, can someone help me please?

---

### Post by Splork on 2010-08-10
Folowed the readme:

```
dave@dave-desktop:/media/c4db98fa-0925-4511-972c-7e03e2777399/dave$ ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly
dave@dave-desktop:/media/c4db98fa-0925-4511-972c-7e03e2777399/dave$ 

```

Dave

---

### Post by Splork on 2010-08-10
```
brw-rw----   1 root disk      8,   0 2010-08-10 15:48 sda
brw-rw----   1 root disk      8,   1 2010-08-10 16:05 sda1
brw-rw----   1 root disk      8,   2 2010-08-10 15:48 sda2
brw-rw----   1 root disk      8,   5 2010-08-10 15:48 sda5
brw-rw----   1 root disk      8,   6 2010-08-10 15:48 sda6
brw-rw----   1 root disk      8,   7 2010-08-10 15:48 sda7
brw-rw----   1 root disk      8,   8 2010-08-10 15:48 sda8
brw-rw----   1 root disk      8,   9 2010-08-10 15:48 sda9

```

I also think sda6 is where my previous system was installed, think it's running on sda9 currently I don't know what sda is or how I know this, I just do  :)

---

### Post by Splork on 2010-08-10
I would also like to apologize if this sort of issue has been reported/resolved, I see several issues with bootloading, /home, etc read through dozens of threads of each individual event I encountered regarding this issue but since I am not yet an Ubuntu expert, I have failed to see any resemblance to my specific problem.

---

### Post by Splork on 2010-08-10
Okay...

 Through the bootloader after many attempts to restore it, finally got the full bootloader showing all sda's, so booted Ubuntu on the correct sda, although it didn't let me into the Gnome GUI, I managed to give myself permissions through the prompt and sudo mv * /storage and then backup my stuff after rebooting into the correct install.

---

