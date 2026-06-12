---
title: "[UNSOLVABLE] Ubuntu 12.10 - fatal crashes since the beginning"
date: 2013-03-17
forum: Installation &amp; Upgrades
---

### Post by Titanio Verde on 2013-03-17
Greetings again.

I installed this **fresh** Ubuntu 12.10 amd64 two days ago. I got great experiences with Ubuntu some years ago, and I opted to get back.

From the first boot I proceeded to install most of my common packages, and **the system randomly crashes**. Only the mouse responds to my movements once every 5 or 10 seconds, and at the same time the (default) sound system goes one step further on its buffer. Everything else gets locked up, including the keyboard (even SysRq keystrokes), leaving me with the only option of a hard reboot.
This can occur 15 minutes since its boot, or sometimes when changing tab on Firefox, or playing on Steam. This gave me worse problems when installing nVidia drivers and/or frglx (on Steam demand), losing panels on Unity.

I gave a couple of looks to syslog. The only last entries before reboot are about **AptDaemon.PackageKit starting and quitting every 5 minutes**. I don't think this one is the killer, but I'll leave it here for extra information: [http://pastebin.com/y0dAv34F](http://pastebin.com/y0dAv34F)

I think my nvidia-current drivers are not active right now, and I read they currently give a lot of problems with Compiz (I was using Mint Debian for a month, and the window manager was almost invisible until I set Compiz off).

It can't be CPU temperature problems, since this doesn't happen with any other OS, and I always keep an eye on cpufreq.

Crashes happen also in GNOME, even no-effects.

Somewhere else to look? Or should I immediately try with another flavor or distro?
Thank you beforehand.

EDIT: It's a general well-known bug, noted here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187)

---

### Post by matt_symes on 2013-03-17
Hi

Random crashes :( They can be very hard to track down.

As sysreq is not working it sounds like it may be the kernel crashing.

Have you checked with top or htop to see the load on the cpu ?

What are the full specs of your machine ?

Those aptdaemon lines in syslog are not a problem.

Do you get the same lockups when using a LIVECD/USB of 12.10 ?

How confident are you that your hardware is not faulty ? Have you tested memory and hard drives ? Any other hardware tests you have performed ?

Kind regards

---

### Post by sanderj on 2013-03-17
You say "crash". Do you mean "lock up"?

Did you run memtest86+ on the system? It's in the Ubuntu boot menu. Run it for a few hours (for example: one night long)

While in Ubuntu, open a terminal and type:
 
tail -f /var/log/syslog

And keep that terminal open and visible. As soon as the system freezes, make a picture of that screen and post it.

---

### Post by Titanio Verde on 2013-03-17
I run it on LiveCD this morning, and crash! After a while, with Firefox at minimum and without Flash.

Yes, it could be RAM. I have no problems like that on Mint Debian (still installed in another partition) nor in Windows 8, using RAM consuming software sometimes.
But the first RAM module has almost 4 years already, and both are common Kingston. It would be worth a try. I'll wait for the next crash and *sigh* continue working on my laptop.

My current session is reaching its first uptime hour. Firefox, Totem and System Monitor up. I uninstalled the Amazon webapp, just in case.

@sanderj I already posted the last entries from syslog in the main post. There's nothing more than those AptDaemon warnings before a crash.

Specs: amd64 Athlon II 2,70x2, 2 x 2GB RAM 1066 MHz, nVidia GeForce GT 240.

I'll keep you informed. For great justice.

---

### Post by matt_symes on 2013-03-17
Hi

> I'll wait for the next crash and *sigh* continue working on my laptop.

I know that feeling. 

I have spent the last day and a half trying to track down random crashes and freezes on a Win7 box for a friend.

After a day and a half, at least i know what it's not :)

Kind regards

---

### Post by Titanio Verde on 2013-03-17
Half an hour of memtest gave me two possibilities: something is wrong with my Gigabyte motherboard, or something is wrong with Ubuntu's default memtest. And I mean the CD one, because the hard drive one complaints about not enough base memory. (¿?)

After 5 or 10 minutes or memtest, it always gave error on the same region. Even changing the RAM cards, switching slots or putting just one or the other. Always the same region.

Anyway I put them in reverse order, having Minecraft as a hard RAM test, and after 30 minutes is still up. I'll keep it for a long while.

If it's really a motherboard trouble, why no other OS care about it? :-/

---

### Post by sanderj on 2013-03-17
When I switched from Mandriva / Mandrakelinux to Ubuntu, suddenly my system was unstable / crashing. Cause: bad ram. Mandriva had the module BadRAM turned on, and automagically blacked out bad ram.

In Ubuntu, it seems you can manually turn off the bad memory part. See [http://gquigs.blogspot.nl/2009/01/bad-memory-howto.html](http://gquigs.blogspot.nl/2009/01/bad-memory-howto.html)

And read [https://help.ubuntu.com/community/BadRAM](https://help.ubuntu.com/community/BadRAM) for the BadRAM method.

HTH

---

### Post by Titanio Verde on 2013-03-17
Crash after 2 hours of non-stop Minecraft on background.
On the next boot the system crashed after few minutes, just typing on Firefox.

Now my guess is GPU temperature, as I had similar troubles in Windows few years ago (hardware crashes when playing, due to a cheap GPU overheat). Despite I think nVidia drivers are not on at all, and Java-based Minecraft is totally rendering through software.

There's no easy way to measure it from Linux, right? I found a pair of programs based on sensors, but they don't seem to find my GPU sensor. Only some "k10temp-pci-00c3" and "nouveau-pci-0100" which, at the moment, I don't know who are they. Anyway, they're pretty cold right now.

---

### Post by iponeverything on 2013-03-17
keep a terminal window open and visible on desktop and in it leave running:

> 
cd /var/log
sudo tail -vF messages syslog daemon.log kern.log debug Xorg.0.log


When it dies maybe a clue will be visible in the window.

---

### Post by Titanio Verde on 2013-03-18
Another one, with just Firefox.

Last messages on...

[QUOTE="kern.log"]Mar 18 18:27:53 gigahertzio-6410 kernel: [ 9049.331008] [drm] nouveau 0000:01:00.0: vm flush timeout: engine 0[/QUOTE]

[QUOTE="syslog"]Mar 18 17:17:01 gigahertzio-6410 CRON[2952]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 18 18:17:01 gigahertzio-6410 CRON[3126]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 18 18:27:53 gigahertzio-6410 kernel: [ 9049.331008] [drm] [/QUOTE]

[QUOTE="Xorg.0.log"][   790.210] (II) NOUVEAU(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.1 kHz e)
[   790.210] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   798.746] (II) XKB: reuse xkmfile /var/lib/xkb/server-1EEA8A8B5282F1A1C5B4CDBD09D3AB33A69761C2.xkm
[   806.915] (II) NOUVEAU(0): EDID vendor "GSM", prod id 22252
[   806.915] (II) NOUVEAU(0): Using hsync ranges from config file
[   806.915] (II) NOUVEAU(0): Using vrefresh ranges from config file
[   806.915] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   806.915] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz eP)
(... lots of screen resolutions)
[   806.916] (II) NOUVEAU(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.1 kHz e)
[   806.916] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)[/QUOTE]

The only hint here for me is this "vm flush timeout". I googled this and found some people with the same problem since Ubuntu 12.04, like this: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187) I'll investigate further later.

---

### Post by Titanio Verde on 2013-03-19
I quit.

That Launchpad post I showed before explains about a one year long bug that it's not yet officially fixed. One bug, or a collection of package dependency bugs.
I tried some workarounds, installing these and those nVidia drivers. But every time it got worse. I also tried Xubuntu, but on Live I got exactly the same problem.

The previous Mint Debian setup still works fine, so I'll keep up in there and wait for the next Ubuntu release. The only price is to miss a bunch of user features.

Thank you for your attention.

---

