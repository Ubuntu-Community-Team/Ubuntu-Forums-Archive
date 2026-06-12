---
title: "Use ram instead of disk, write to disk at shutdown"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by Icovada on 2011-03-21
I have a netbook I'm not using and which I transformed into a server with Apache, Tomcat6, Netatalk, Webmin, BIND9 and Tor.

Problem is, the disks never stop spinning because all of the programs write a few kb at least every few seconds to disk, even when nobody is connected to it.

My question is: Is there a way to have the computer boot from disk like normal (maybe even a squashfs), keep ALL CHANGES to ram and then save to disk when either the ram is full (unlikely because the server is rebooted every few days) or at shutdown?

I thought about a mixture of ramfs and unionfs but I'm not good enough yet...
Anybody have any ideas?

---

### Post by An Sanct on 2011-03-21
Welcome to the forums!

Here's a way to [get firefox cache (and other programs...) into ram]("http://ubuntuguide.net/speed-up-firefox-by-moving-cache-into-ram-in-ubuntu"), also you can [move all your logs and tem files to ram]("http://www.fewt.com/2010/07/move-your-logs-and-temp-files-to-ram.html") to make the disk stop spinning all the time.

Warning: You can lose all the logs or modified data this way!

---

### Post by Icovada on 2011-03-21
Thank you, but is there a way to keep ALL changes into ram and write them at shutdown? (or every, say, half an hour?)

---

### Post by An Sanct on 2011-03-21
The *write "down on shutdown* - *using cron to sync*" is covered in this [Firefox sample]("https://wiki.archlinux.org/index.php/Speed-up_Firefox_using_tmpfs"). Note, that this is only a Firefox sample, other applications can work this way too.

---

### Post by Icovada on 2011-03-21
Awesome, I'll try it tomorrow morning. Too tired right now!

---

