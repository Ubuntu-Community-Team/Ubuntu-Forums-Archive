---
title: "fresh edgy install with separate \home partition"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by raul on 2006-10-29
hi all

i'm running dapper and have a separate \home partition. i have a couple of (related) questions about doing a fresh edgy install:

(1) i seem to have a lot of programs running from \home (e.g. thunderbird, akype, gaim, dvdrip, mplayer, openoffice, wallpapoz, etc). what will happen to all that if i do a fresh edgy install? in particular, will there be a conflict between, say, the newer versions gaim or firefox that come with edgy, and the older versions that i have at \home? should i first get rid of the stuff running from \home? 

(2) i got a bunch of stuff on dapper through automatix. is all that at \home? either way, will i have to run automatix again to get all that?

as it might be clear to you by now, i have a general confusion as to what is at \home and runs from there, and what is not (i'm still a noobie). any help would be greatly appreciated.

---

### Post by _lynX on 2006-10-29
> **raul said:**
> hi all

i'm running dapper and have a separate \home partition. i have a couple of (related) questions about doing a fresh edgy install:

(1) i seem to have a lot of programs running from \home (e.g. thunderbird, akype, gaim, dvdrip, mplayer, openoffice, wallpapoz, etc). what will happen to all that if i do a fresh edgy install? in particular, will there be a conflict between, say, the newer versions gaim or firefox that come with edgy, and the older versions that i have at \home? should i first get rid of the stuff running from \home? 

(2) i got a bunch of stuff on dapper through automatix. is all that at \home? either way, will i have to run automatix again to get all that?

as it might be clear to you by now, i have a general confusion as to what is at \home and runs from there, and what is not (i'm still a noobie). any help would be greatly appreciated.

Your /home partition contains all of your user-based settings, personal files, and anything else you choose to manually place in there. All of your programs are actually installed in the /usr directory. The good thing about having a separate /home partition is that you can reinstall Ubuntu, cleaning out all installations to fix any problems, etc., but you still retain your settings.

---

### Post by raul on 2006-10-29
ok, thanks. just to clarify then: i'll have to reinstall all software when i do a clean reinstall, but my current settings for all programs will be read off from \home. is that right?

---

### Post by dckirba on 2006-10-31
I was thinking of upgrading to edgy from the alternate cd, but then I read this: [http://linux.slashdot.org/linux/06/10/28/239258.shtml](http://linux.slashdot.org/linux/06/10/28/239258.shtml) so I'm going with a fresh install. I too have a seperate /home partition.

My question is a bit related to this, sorry for hijacking the thread, but do I just format and install in the / directory and leave the /home and /swap untouched?

I have another HD with XP on it, I suppose grub will detect that and automatically install right?

Thanks in advance, cheers,
David

---

### Post by NyquistLimit on 2006-10-31
I have a question too. I'm in a situation where I think some of my settings might be causing some problems with my current installation of edgy (which i upgraded from dapper).

What would happen if I did a clean install of edgy with my existing home partition? Would the installation restore important settings to their defaults or would the OS continue to use potentially bad configuration files in my home folder?

Would the best option be to remove everything in /home except my valuable data and do a clean install?

---

