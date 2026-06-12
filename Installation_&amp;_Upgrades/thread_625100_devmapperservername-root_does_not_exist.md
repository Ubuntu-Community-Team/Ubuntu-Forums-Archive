---
title: "/dev/mapper/servername-root does not exist"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by academiphiliac on 2007-11-27
I attempted to install Gutsy Server from CD twice, and twice I got this message on startup:

```
Loading, please wait...
        Check root= bootarg cat /proc/cmdline
        or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/mapper/myservername-root does not exist. Dropping to a shell!
```

So, what do I do?

---

### Post by Stryker777 on 2007-11-30
Same issue here.  Just wondering, did you use lvm or not?  Was it 64 or 32 you installed?

I dont have an answer yet but am going to get this thing running tonight somehow.  We may have to install fiesty.

---

### Post by academiphiliac on 2007-11-30
Yes, I tried to install LVM. Perhaps that's the crux of it.

I think I was using 32-bit, but I'm not quite sure.

I'll give it another go tonight as well.

---

### Post by Stryker777 on 2007-11-30
It wasnt lvm.  In fact, I have tried everything I could think of.
I get it installed, then next boot it loads some stuff, gets through the usb, at that point the hard drive light turns on and never turns off again.  Then the cd/dvd drive loads, and that is the last activity I get at all.  It loses sda1 then.  Oh, the mapper issue was an lvm thing though.  It just is not the full fix.

Oh well.  I am installing fiesty right now because I am pretty sure I can get it working with the older kernel.  It is something in the new kernel and I just cant seem to find it.

I will let you know how it goes for me.  If you figure it all out, please dont forget this poor soul lol.

---

### Post by academiphiliac on 2007-12-01
An install without LVM didn't work for me either. 

I was having some trouble upgrading from Feisty a while ago. That's why I went with the CD install. It looks like I'll have to try that tack again.

---

### Post by Stryker777 on 2007-12-01
Fiesty works fine.  It is touchy though.  If I get any updates I lose it again.  I installed the drivers from nvidia for video, realtek for sound, and ar5007 with ndiswrapper for the wireless.  Everything on it is working.

One other odd thing, when I did gdmsetup to modify the login page, gdm would then fail to load after rebooting.  

I really believe it is how the kernel is handling the nVidia chipset and this thing is half controlled by nVidia.  I guess I will keep trying.  I really want to be able to get basic updates without crashing.

If nothing else, I keep making full system tar files so if I cant get back in, i can load a live cd and untar the system back to the working state.  Have done that a few times today lol

In case you need a backup command, here is what I use:
```

Backup:
tar cvpzf backup_`date '+%m.%d.%Y'`.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/home/myDirectory/backups /

Restore:
tar xvpzf nameofbackupfile.tgz -C /

```

---

