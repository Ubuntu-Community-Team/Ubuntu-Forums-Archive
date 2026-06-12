---
title: "compaq F700 - Multiple problems upgrading (kubuntu64 9.04 --&gt; kubuntu64 9.10)"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by litspliff on 2009-11-19
[COLOR=Red]equipment:[/COLOR] [COLOR=Black]compaq F700 laptop. 
[/COLOR]
[LIST=1]
[*]came with vista
[*]resized vista to create swap and reiser partitions, kept recovery partition, installed ubuntu i386 9.04
[*]worked great for a long time with just gnome and ugly brown colors.
[*]tried to apt-get KDE, installed, then wouldn't boot linux anymore.
[*]wiped linux partitions, and re-installed same setup with ubuntu amd64 9.04.
[*]installed development version of KDE, added KDE launchpad repository to my sources
[*]worked great for a long time with KDE and gnome and stylish blue colors that match my hardware.
[*]as the 9.10 release approached, a random update session affected performance a bit (nautilus and the gnome desktop became slightly laggy). in hindsight, i should have documented the event better.
[*]on some different hardware i used the update manager to upgrade a couple years ago and the sht broke, so i was reluctant to .... but i clicked it on F700.
[*]took a while....fiinished downloading, then window froze.
[*]**init 6**, **apt-get upgrade**, packages started installing.
[*]got bored, started reading comic books with eye of gnome. started noticing things get all fcky in random things (side effect of packages being upgraded...was fine after reboot).
[*]finished install, told me to restart.
[*]on restart, got kubuntu blue splash.....followed by ugly-ss brown spotlight thing, followed by ....WTF?...a list of all the users on the computer....here's why my laptop sucks now.....
[/LIST]


[LIST]
[*]boot time has been doubled. 9.04 booted in under a minute. now takes 2 minutes (at the least)
[*]instead of just the kubuntu splash screen, i now have an additional splash screen with a brown spotlight thing.
[*]when renaming a file, if i press the 'u' key on the keyboard, it's the same as 'ctrl+v' (paste clipboard), so i have to turn on caps lock, then press shift+u to type the letter u in lower case.
[*]if my wireless connection drops for just a moment, smb4k freaks out. loses connectivity. can't unmount shares, and nautilus freaks out because i have shortcuts to smb shares (unless i close the sidebar before smb4k freaks out). only reasonable action is to **init 6**.
[*]when using transmission, many of my windows will turn sick (grey like a crash), then get well, then turn sick, then get well, then turn sick....
[*]every time i reboot, the "keep aligned" checkbox (when right clicking on desktop) re-selects itself preventing me from organizing my desktop when i have a lot of stuff on it.
[*]flash playback in new firefox is glitchy (periodically goes transparent on some frames)
[*]more of a general complaint, but the new software center sux (add/remove software from 9.04 was awesome, new one doesn't even have ratings, bad interface)
[*]most annoying - gedit when saving to samba share, can't find file (it disappears from nautilus for a second as well), click cancel, then warning - file has changed. reload? i look at the hidden files and i see this crap. (example from editing a *.plx file - .plv~,plw~,plx~,ply~,plz~) making it a pain to use gedit every time (i write all my code to my server with gedit, now i avoid writing code to anything but the local HD)
[*]also, nautilus doesn't always refresh on local directories (have to hit F5)
[*]its also important to me that i do not have a list of local users on my login screen. i really liked the 9.04 ubuntu (not kubuntu) login screen. right clicking on the upper left corner used to access login screen settings, but now it's under system-administration and all of the settings are gone (why remove a bunch of great features? - WTF!?)
[/LIST]

there are also some other random annoyances. for example, my upload speed to my server using wireless is painfully slow. here is a screenshot. keep in mind i have 54Mbps with strong signal and no other traffic on the interface. if i need to push anything to my server, i now have to plug in a cat5 cable.

[IMG]http://www.dynatron.org/imagearchive/forums/gripes.jpg[/IMG]



ANY CONSTRUCTIVE ADVICE WILL BE GREAT TO READ.

should i just re-install 9.04 from DVD? the updates had been slowly breaking that as well. not to mention i will have to do the dsdt (ACPI compiling) again, as well the B43 wireless driver headache to get kismet working.

it seems to me like ubuntu has gone backwards a step in the interface with this upgrade. i still like it better than any other distro, and better than other OS's, but i feel like i've been betrayed by my best friend every tiime i have to wait 3 minutes to get to my desktop.

 thanks for reading and/or commenting.
hopefully someone else with the same problem finds this thread on a google search.


-j

---

### Post by litspliff on 2009-11-24
too verbose?


let's do this one question at a time....

[SIZE=4][FONT=Comic Sans MS]**when i rename a file, typing the letter 'u' instantly pastes my clipboard into the filename.**[/FONT][/SIZE]
what gives? the only workaround i can find is capslock+shift+u.


please help!


thanks for reading...

---

