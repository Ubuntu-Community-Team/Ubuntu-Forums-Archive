---
title: "[SOLVED] Gutsy x86_64: Installation tells me all packages are corrupt"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by odiseo77 on 2007-11-13
Hi people. I'm trying to install Ubuntu Gutsy 64 bits using the alternate install CD on a Intel Core 2 Duo with EMT64 compatibility enabled in the BIOS (so *I guess* there shouldn't be architecture problems). The point is the installation hangs for  a while at 6% when installing the base system, and then it comes up telling me "package xxx-nnn.deb was corrupt", gives me the option to continue or go back and no matter what I do, it keeps trying to install the following packages and telling me they're corrupt; after a while, the installation comes up with an error telling me it failed to install the base system (obviously). Have tried it several times, with two different CD brands (of good quality, I think) and two iso images (downloaded at different times) and it's always the same.

As a side note, I've installed Gutsy 32 bits without problems (well, actually, it did got stuck at 6% when installing the base system for about ten minutes, but then it continued fine), and Debian Lenny 32 bits as well, but I'd like to try Gutsy 64 bits for experimental purposes.

So what do you people think might be wrong here? I would be surprised if it's an architecture mismatch because Core 2 Duo's are supposed to support 64 bits? :confused: Also, on another 'old' hyperthreaded Pentium 4 I could install Feisty 64 bits without any trouble.

Any ideas?

Thanks in advance for your answers.

P.S.: Oh, and excuse me if this is more suitable at the x86_64 section of the forum; I thought that being an installation issue, it would be more suitable here (a moderator can move this thread there if he/she finds it better).

Regards.

---

### Post by K.Mandla on 2007-11-14
It sounds like the disk was misburned, or the ISO was corrupt when you downloaded it. This has happened to me dozens of times. 

Try double-checking the md5sum of your ISO file against the number posted on the download page. Then try reburning, and before you install, let Ubuntu check the CD integrity.

I know, it's a pain, but I find myself doing this quite frequently. It's better to check first instead of botching an install. ... :???:

---

### Post by odiseo77 on 2007-11-14
Hi K.Mandla, thanks for your answer. Well, I checked the md5sum of the .iso file twice, character by character, and it exactly matches the one of the Ubuntu downloads section, so I guess the disc was misburned as you say? I'd be very surprise, because this would be the first time of my 3-4 years using linux that I have this issue. In case this is of interest here, I burnt the cd using k3b (from gnome) with the default options, as I always do; guess I have to check the options then, or maybe give gnomebaker a try to see what happens.

I'll post back about how it goes when I have a spare time for installing Gutsy 64 bits again.

Regards and thanks for your help again :)

---

### Post by odiseo77 on 2007-11-17
Hi again. I finally could install Gutsy 64 bits on my machine. Guess either there's something wrong with k3b or I was doing something wrong with it because this time I used gnomebaker to burn the iso image and the installation went flawlessly; maybe it's because I set the burn velocity to 48x and on k3b I was using the default config, which, I think takes the higher velocity (which is 52x in my case). :)

Regards.

---

