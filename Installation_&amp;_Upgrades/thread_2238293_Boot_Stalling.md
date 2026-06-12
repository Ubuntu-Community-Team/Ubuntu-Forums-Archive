---
title: "Boot Stalling"
date: 2014-08-07
forum: Installation &amp; Upgrades
---

### Post by Kirkx on 2014-08-07
I've been running Xubuntu 14.04 for a few weeks without problems but in the last few days the boot process keeps stalling at the following line:

```

Aug  6 20:21:21 linxub kernel: [    6.433252] scsi4 : usb-storage 2-4:1.0
Aug  6 20:21:21 linxub kernel: [    6.433757] usbcore: registered new interface driver usb-storage
Aug  6 20:21:21 linxub kernel: [    7.439092] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Aug  6 20:21:21 linxub kernel: [    7.445081] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Aug  6 20:21:21 linxub kernel: [    7.451079] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Aug  6 20:21:21 linxub kernel: [    7.457079] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Aug  6 20:21:21 linxub kernel: [    7.457397] sd 4:0:0:0: Attached scsi generic sg2 type 0
Aug  6 20:21:21 linxub kernel: [    7.458685] sd 4:0:0:1: Attached scsi generic sg3 type 0

```

At this point I have to hit Ctrl+Alt+SysRq to get it going and after that there are no more problems:

```

Aug  6 20:21:21 linxub kernel: [    7.458889] sd 4:0:0:2: Attached scsi generic sg4 type 0
Aug  6 20:21:21 linxub kernel: [    7.459113] sd 4:0:0:3: Attached scsi generic sg5 type 0
Aug  6 20:21:21 linxub kernel: [    7.687085] sd 4:0:0:2: [sdd] Attached SCSI removable disk
Aug  6 20:21:21 linxub kernel: [    7.697071] sd 4:0:0:3: [sde] Attached SCSI removable disk
Aug  6 20:21:21 linxub kernel: [    7.727081] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Aug  6 20:21:21 linxub kernel: [    7.737074] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Aug  6 20:21:21 linxub kernel: [   10.335323] EXT4-fs (sda23): INFO: recovery required on readonly filesystem
Aug  6 20:21:21 linxub kernel: [   10.335394] EXT4-fs (sda23): write access will be enabled during recovery

```

The above stall only happens at the cold start of the PC, reboots done after that are ok. The obvious suspects are the latest upgrades to kernel 3.13.0-32-generic and to distro v14.04.1. I always run the updates using the following commands:

```

   sudo apt-get update
   sudo apt-get dist-upgrade
   sudo apt-get autoremove

```

---

### Post by Kirkx on 2014-08-07
It seems that the problems has resolved itself after the major crash at shutdown that required turning off the PC with the power supply switch (the one at the back of the computer). I will mark the thread as solved.

---

### Post by cathect2 on 2014-08-07
I'm having a problem this morning after the most recent updates to ubuntu. I get the log in screen as expected, input my password, hit enter, then Ubuntu just freezes and gives me just a wallpaper image with no icons. I've rebooted several times but am unable to proceed any further than described. I can't get a terminal to appear either...

---

### Post by cathect2 on 2014-08-07
I got into recovery mode. My filesystem is in read-only mode. #freakingout

---

### Post by grahammechanical on 2014-08-07
You really should open your own thread for your own problem. You will get little help by using someone else's thread. And this thread has been marked as solved. I only looked in the thread out of curiosity.

At the recovery menu if we select Network the script will not only set up the network connection to the router (hence internet) but will also put the file system into Read/Write mode. Then we can use Root - root prompt. My guess is that you need to change video drivers.

What happened when you exited recovery mode by selecting Resume? That tries to bring us to a desktop using a fallback open source video driver.

Regards.

---

### Post by cathect2 on 2014-08-07
Ok, moving to a new thread. FYIgrahammechanical, on resume I have the same stalled boot.

---

