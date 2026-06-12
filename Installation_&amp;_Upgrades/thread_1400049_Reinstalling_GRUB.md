---
title: "Reinstalling GRUB"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by Frankiewizard on 2010-02-06
I am trying to us UBUNTU on a TOSHIBA Qosmio G20
in a windows environment "wobi" worked very well until I did an update on ubuntu
now all I am getting is -


GNU GRUB version 1.97 beta
[  Minimal Bash - like line editing is supported. For first time,
TAB lists possible command complications.
Anywhere else TAB lists possible  device/file complications.    ]

When I press Tab I get this


sh:grub
Possible commands are:
. [ badrun boot cat chainleader configfile cpuid dump echo expert halt help initrd
linux list_env load_env loopback is 1smod parser.rescue parser
.sh reader.normal reader.rescue reboot rmod save_env search set sleep source terminal
_input.console terminal_output. console test unset



 my cd driver is a bit shot up and does not read all cds so 
 I thought I may try a reboot on a memory stick
 ! 'but no hope' is there another way around this/my problem of Reinstalling GRUB ?

Cheers Frankie.:-({|=

---

### Post by rknetsch on 2010-02-06
This is EXACTLY why I just logged on today.  This is precisely the problem I am having and have no idea what do do.  Someone help us!!!  I LOVE wubi because I don't have to worry about partitions, but I think the upgrade screwed that up.

---

### Post by darkod on 2010-02-06
It's a "famous" bug in wubildr, a file which is on the partition where you installed wubi (C:, D:, E:, etc).
Boot windows, download an improved copy of wubildr and replace the existing file:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

NOTE: This is only for wubi installs.

---

### Post by rknetsch on 2010-02-06
BRILLIANT!  Works like a charm.  I can go back to the joys of Linux again.

---

### Post by Frankiewizard on 2010-02-06
Super Darkod !!! you have made my day ! week-end ! week ! Cheers and may the mighty ubuntu smile upon you for a long time.
Frankie.

---

### Post by ozgurozturk on 2010-02-07
i am very very thankful to you man. thanks from turkiye. by this way i've just rescued my os. i'm using karmic koala but id doesn't start after kernel update, gives a message "minimal bash line..." but i've solved problem by this way. again thank you.

---

