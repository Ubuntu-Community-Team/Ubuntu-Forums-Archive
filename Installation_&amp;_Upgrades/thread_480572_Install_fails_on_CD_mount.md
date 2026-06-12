---
title: "Install fails on CD mount"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by Gafanhoto on 2007-06-21
I've been trying to migrate to linux for a long time, but never had the time to do it. I run an AMD64 3.2GHZ, ATI Radeon9600, and ASUS A8X-X mobo. I've got Windows XP running.

Recently a friend of mine told me that Slackware 11 was really easy to install, so I gave it a shot and had no problem at all.

BUT( and there's always a but), I'd like to try a Debian based distro, and since there's this big fuzz about Ubuntu and how easy it is to install, it was my first choice. 

So I downloaded the iso for 7.04 version, verified checksum, burned it, verified CD checksum. Rebooted my pc with the CD on the drive, and BAM!, there was a nice Ubuntu configuration screen. BUT( and if there wasn't a but I wouldn't be posting ) every time I tried one of the avaiable options that involved mounting the CD, the system would just hang for a long long long time, and then warn that it was unable to mount the filesystem.

"Damn"- I said to myself- "Maybe if I get the other avaiable version". And there I went, downloaded 6.06 alternate desktop iso, verified checksum, burned it, verified CD checksum, rebooted with the CD in and BAM!, there was that nice brown Ubuntu screen with all those options.

Sadly, the same problem occurred. I kept getting this "Cannot mount filesystem" message after a long time.

So I did some digging, asked the Wise One Google, and could not find ONW single post that would help.
Then something occurred to me...how did slackware managed to mount my CD drive, and Ubuntu didn't?!

So I booted to Slack, and tried to mount my cd from /dev/cdrom and it didn't work. Running KDE I managed to find that my cd was actually mounted using /dev/hdd.

So I'd like to know wich device does Ubuntu installer uses to mount the CD? Is it possible to change that?

---

### Post by Gafanhoto on 2007-06-23
So I got the Ubuntu CDS from the website and got the same problem...

I think I'll stick with slack...

---

### Post by brendan6 on 2008-04-04
Hey man..did you ever find out why this happens and how i can fix this?

---

