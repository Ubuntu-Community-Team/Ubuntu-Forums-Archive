---
title: "Upgrading from Edgy to Fiesty has killed Ubuntu"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by Sturm on 2007-05-05
It started out like any normal upgrade scenario.  I clicked the orange icon and began updating a couple of things.  When it was done, I noticed that 7.04 was released and I could upgrade to it.  I chose to do so, let it download things for over an hour, then it started installing.

Roughly 1/3 to 1/2 of the way through installing stuff, I got an error notification.  It said that it was probably a bug and recommended that I report it by jumping through a bunch of hoops that I did not feel like doing right then.  So I just told it to continue, and it said that it could NOT continue and would need to restore everything back to the way it was, but that even doing so might NOT work.

Well, sure enough, it caused the system to hang completely after a while of this "restoring" procedure.  I reset the machine and it will not go to the login screen anymore.  And I've tried several things at [The Grub Page]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"), but none of them work, either.  It seems as if my Ubuntu system is hosed.  Thank goodness all the data is on a separate drive.

The last few things I see on its screen, in case it helps, are:

```
FATAL: Could not load /lib/modules/2.6.20-15-generic/modules.dep: No such file or directory
(repeat)
ALERT! /dev/sda1 does not exist. Dropping to a shell!

BusyBox v1.1.3 .........(etc.)
/bin/sh: can't access tty; job control turned off
(initramfs)

```

So, I'm currently downloaidng Feisty and I'll burn it to a CD to see if just installing it over top of the Edgy installation will get me back into the system, even if it hoses Beryl and the nVidia driver downloader.  Unless someone has some better ideas, that is...

---

### Post by oaschal on 2007-05-05
Same problem for me!

---

### Post by Sturm on 2007-05-06
Well, since there's no replies to this post, I guess there's no hope for recovering my system.  :-(  So I'll just format & install 7.04 on it again.  I'll probably post somewhere later asking how to have it automatically mount existing ext3 partitions once I get it up and running properly.  Later.

---

### Post by Sturm on 2007-05-06
Done.  Didn't take but a couple of hours or so...  And I even got Samba working again after only a fraction of the time it took me the first time around.  Perhaps I'm learning, after all...

So after installing Feisty and getting everything back the way I like it, including installing video drivers, I realized my faux pas (is that the right term?).  I had Envy installed on that computer, which is the program that installs and updates nVidia & ATI GLX drivers.  Turns out that I was supposed to *remove* those custom drivers *before* upgrading from Edgy to Feisty, replacing them with Ubuntu's default NV drivers.  I didn't know that and tried upgrading while the custom GLX drivers were still installed--bad mistake.  Well, lesson learned.  I hope perhaps others may learn from my mistake.

Well, take care! :)

---

### Post by Cannaregio on 2007-05-07
Happened to me too once.
This different solution worked for me, so I'll bump it here as well.

This error "BusyBox /bin/sh can't access tty" and so on is mostly due to the fact that you have a XP partition and dual boot and you just pulled off a USB stick without due ejecting either in your XP partition or in Ubuntu itself.

Solution is to live boot from a feisty live cd, and then terminal, and then (not really necessary) check with system --> administration --> gnome partition editor, if you want to check it's a sda1 and see what happens, but the important life-saving command is:

```
sudo e2fsck -y /dev/sda1
```

the corrupted drive will be checked and healed.

It worked for me, your mileage may vary.

---

