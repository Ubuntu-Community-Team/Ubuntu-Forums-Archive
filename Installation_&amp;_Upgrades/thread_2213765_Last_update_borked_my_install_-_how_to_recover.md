---
title: "Last update borked my install - how to recover?"
date: 2014-03-28
forum: Installation &amp; Upgrades
---

### Post by coolbreeze472 on 2014-03-28
Hi everyone

A few weeks ago I downloaded Ubuntu (Gnome) 14.04 beta 1 and installed it, hoping to update my way to the final version. Everything was going smoothly for awhile but after the last update (yesterday) I rebooted and was greeted by a dark-grey screen with only a mouse cursor.

I tried the shift key, "s", startx, gnome-shell, etc. I tried rebooting into the recovery mode and tried a number of different options. Nothing. I tried going into the shell (via the recovery mode) but it was read-only so I tried mount, mountall, mount --all, mount -o remount,rw /, etc. Not sure if any of these worked but a few commands seemed to.

Next, I tried apt-get update and apt-get dist-upgrade hoping to update/upgrade my way out of the problem (ie; maybe a fix would be included with the updates). However, I was greeted with messages telling me that the repository could not be found and got lots of "failed to fetch" error. Next, using my browser (on a different PC) I typed in the URL of one of the "failed" official repos and discovered that they were accesible and not down or anything. As a note, I do not have any PPA's or other extra repos installed. I also checked my connection.

I'd be really greatful for any help and advice on this. I realize that I could just download beta 2 or wait until the final version is released but 1# the whole point was to save some time, get a head start on this and update my way to the final release AND 2# it would take days to start from scratch with a fresh install and get everything set up again and I'd really rather avoid this and just learn how to get out of messes like this so I can deal with them in the future.

Thanks so much for your help. Unfortunately I'm not going to be able to provide any output of various config files here since I don't seem to have any way of even bringing up a simple terminal so I can type commands (especially to update the machine). Is there any way out of this without doing a reinstall?.

---

### Post by Rob Sayer on 2014-03-28
Borked systems after updating a beta release aren't that unusual ... there's a reason this is a sticky in the Ubuntu+1 section:

[http://ubuntuforums.org/showthread.php?t=1970289](http://ubuntuforums.org/showthread.php?t=1970289)

---

### Post by coolbreeze472 on 2014-03-28
Very helpful but I ended up doing a fresh install of beta 2 this time. Thanks again :)

---

### Post by Navneet_Kumar on 2014-03-28
I think u can wait for a month or so for the stable release of 14.04 and then there would be no such problems.beta version generally causes such problems,when 13.10 beta was launced i was caught up in the same situation then i waited from the stable build to release and from nowthen its working perfectly.

---

