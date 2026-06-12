---
title: "ext device problem since fresh install"
date: 2012-11-23
forum: Installation &amp; Upgrades
---

### Post by unibroker on 2012-11-23
I installed 12.10 and have been this recurring problem every shutdown/startup which I do daily.  I've finally isolated it to my external hard drive (HP Pocket Media which sits in a slot in the tower).

On startup I am initially hit with ```
ata- ID 258: HD IO Get Identity failed for dev/sdf:  Invalid argument
``` which displays right before the login screen.  Then I get to the desktop and wait for it to finish loading before I do anything.  I am hit with a series of errors, at least one system error having to do with ```
/usr/lib/udisks2/udisksd
``` saying ```
udisks crashed with SIGSEGV in ffiz.......
```  This is followed by computer freeze after which I have to do a hard shutdown.  Strange but I have go through this one more time after reboot.  The third time the system seems to stabilize and I am good to go for the rest of the day.  From what I have researched the udisks error is initiated on the previous shutdown.

Today I decided to try and shutdown with the ext drive disconnected from its bay.  From nautilus I unmounted and then physically took the drive from the bay.  I then received a crash report from usr/bin/whoopsie.  I have not researched this.  I then tried to shutdown but when I got past the dialogue box asking it I wanted to shutdown the system froze and I had to do a hard shutdown.  However, when I initiated the startup without the ext drive connected I got none of the notices before login nor when it finished loading.

I did all of this assuming I could just physically attach the hard drive and then mount it during the session.  I cannot.  ```
mount /dev/sdf
mount: can't find /dev/sdf in /etc/fstab or /etc/mtab
```  I then do a lsusb and the return ```
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```  No ext hard drive.  Not sure what the problem is as this device is supposed to be hot-swapable.

The best would be to get this problem addressed on startup/shutdown but I do not know how to proceed and googling has proven fruitless.  Any suggestions on how I might proceed would be appreciated.

Edit:  I hadn't completely pushed in the ext drive to its bay.  Nautilus does recognize it and indicates it's already mounted.

---

