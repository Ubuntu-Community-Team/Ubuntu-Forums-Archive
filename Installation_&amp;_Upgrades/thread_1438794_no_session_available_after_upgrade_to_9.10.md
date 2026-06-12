---
title: "no session available after upgrade to 9.10"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by otz070 on 2010-03-25
I upgraded jaunty to karmic and now I when I click on my username there is no password prompt.
I can't login to a normal gui

tty works but anything that don't run in terminal I get an error (see below)

heres the rundown of what happens:
Everything goes fine until I get to the login screen.
There I get the standard new karmic login. I click my username,
then all the misc stuff pops up at the bottom (keyboard ect.)
[B]but for session there is an "X" icon and the box is greyed out.
additionally there is no password prompt.[/B]

what I tried:
I went into tty1 and run aptitude "update" & "dist-upgrade" 
did checks for broken packages (found nothing)
attempted to access anything via different programs (firefox, pcmanfm, ect) I get error something like "cannot open display"
I checked to makesure that I had openbox & lxsession installed
(was running openbox on previous installs as well)

Every other machine I've upgraded to karmic I've had maybe a couple problems but their managable, this machine seems to have a difficult time with the upgrade reguardless...

right now I'm running Crunchbang, but I posted here, cause I  seem to get errors like this on this particular computer reguardless of  which Ubuntu install I upgrade to 9.10.

I'd try reinstalling but its kinda usless since the problem happens reguardless.

Thanks to anyone who can offer some help:)

---

### Post by otz070 on 2010-03-27
ok well tried more stuff today:
removing and reinstalling:
lxsession, gdm

also stopping/starting various things

reguardless I still have no password prompt!

sorry to say but this is getting frustrating especially since this is the computer that I do all my work on.:-(

please help?!

---

### Post by wolfkstaag on 2010-03-28
Nvidia card, by any chance?

If so, try upgrading to the newest driver; I've heard that's supposed to be causing some problems, though I seem to remember than being more related to 10.04 than 9.10, but it's a thought.

I had a problem recently where I was stuck in a login loop after upgrading from 9.10 to 10.04 Beta1; the primary similarity here is that my Session box had exactly what you've described. A user in the #ubuntu+1 IRC room on Freenode (whose screen name I sadly don't recall) had me do something a long the lines of CD'ing into my home directory and renaming .config, .gconf, .gconfd, and .gnome2 to something else (.config_backup, for example) and then trying to login. It worked in my case; don't know if it will help you (especially since you aren't seeing a prompt),  but it's an idea!

---

### Post by otz070 on 2010-03-28
yes as a matter of fact I do. :oops: I forgot to list my computer specs:
NVIDIA GEForce 6200 512mb gddr2
1gib ddr (2x 512)
AMD athlon xp 3000+ 2100mhz
Kernal ver: 2.6.31-20-generic

sorry bout that
hopefully this will make things easier to diagnose?

---

### Post by otz070 on 2010-03-29
anyone have any suggestions at all?

---

### Post by otz070 on 2010-03-29
got it fixed:
```
sudo apt-get install gnome-control-center
```

it ended up installing alot of packages as per dependencies, so not really sure exactly what it needed...

anyways I just installed it on a whim, for some reason I had a hunch I guess that if I installed gnome that I could atleast *maybe* get gnome to work.

Anyway seems that everything (well almost) works correctly now:D
I didn't even have to login to gnome either, after the install everything was fixed, and openbox was there in sessions, and the password prompt returned!

go figure

---

### Post by diablo666 on 2010-04-06
The tweak worked for me, but i got to use command

apt-get purge gnome-control-center [FONT=monospace]
Probably some config make some strange

Cya
[/FONT]

---

