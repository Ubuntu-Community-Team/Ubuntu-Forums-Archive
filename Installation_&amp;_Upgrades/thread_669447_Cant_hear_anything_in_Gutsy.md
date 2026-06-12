---
title: "Cant hear anything in Gutsy"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by sublime ph03nix on 2008-01-16
I just installed Gutsy, and i am having a ton of trouble with the sound.

Everything works wonderfully (for me) except the sound wont play at all.  When i go to sounds, the only selectable tracks to use are Master and PCM in the ALSA mixer.  I've tried all kinds of stuff from these forums and no luck.  I've tried using realteks drivers from their site but when i run the autoinstalling package it screws things up and i can no longer login.

Any help you can give is appreciated.

I am running
Intel Core 2 T7300 2.0ghz
Intel 965 Express Chipset
nvidia geforce 8600M GS
2 GB DDR2 667
160GB SATA hdd

---

### Post by oldsoundguy on 2008-01-16
you put all those bucks into a really nice set-up and are trying to use ON BOARD SOUND?

---

### Post by dicecca112 on 2008-01-16
is this a laptop? If so what model?

---

### Post by sublime ph03nix on 2008-01-16
Yeah.  It's an HP dv9500t.

I know everyone says that gutsy is shitty for hp, but other than the sound i really like it. Probably because im new to linux.

---

### Post by thechappy on 2008-01-16
I am having the same problems. Just installed 7.10 and kicked Windows out of my life last night. Similar specs, but Toshiba laptop. 

Any suggestions?

---

### Post by sublime ph03nix on 2008-01-16
Ok, so i fixed the problem.  After some research on google, this is what worked for me.

First go to System > Administration > Software Sources
From there, navigate to the Updates tab.
Check "Unsupported Updates (gutsy-backports)"

Now open the terminal and type:

> *sudo apt-get install linux-backports-modules-generic*

Reboot and you're sound should work.


Fixed my troubles with my HP Pavilion dv9500t

GOOD LUCK :)

---

### Post by fahadrather on 2008-01-22
thanks dude.... i had the same problem with my hp dv6516...but your procedure worked....:guitar:....thanx once again:popcorn:

---

