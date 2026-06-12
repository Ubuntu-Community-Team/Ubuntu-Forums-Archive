---
title: "Upgrade to 9.10 and lose wireless"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by solomonhomicz on 2009-12-14
I upgraded to 9.10 today. Wireless connection worked fine to download and upgrade. Upon restart no more wireless. I checked the drivers the driver is still installed and active.
How do I get my connection back?
It worked fine after upgrade from 8.10 to 9.04.
I suppose I could back up my important files on Windows and reinstall, but what a pain.
Oh yeah, I figured what Windows is good for, getting on the imternet to fix Ubuntu.

---

### Post by phillw on 2009-12-14
> **solomonhomicz said:**
> I upgraded to 9.10 today. Wireless connection worked fine to download and upgrade. Upon restart no more wireless. I checked the drivers the driver is still installed and active.
How do I get my connection back?
It worked fine after upgrade from 8.10 to 9.04.
I suppose I could back up my important files on Windows and reinstall, but what a pain.
Oh yeah, I figured what Windows is good for, getting on the imternet to fix Ubuntu.

I figure that anyone who updates their OS without running it from the LiveCD in "don't alter my computer mode"  deserves a dunces hat -- but there you go.

Gotchas happen on new releases of operating systems - look at the sticky on this thread for video ones, or - especially for you - the sticky on the wireless area would be a good place to head ;)  ---> [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

The people on that area put a lot of time and effort in to it.  It is maddening when people don't test vid / network / audio etc. before they move from a totally working operating system to a different one - and then come on and complain.

You will find a *slight* change in attitude will go a long way on these boards. 
You went from a fully working system, you didn't test the new one & it broke. - Huh ??!!

Anyways, my little rant over. If you head over to the wireless area, they'll get you sorted, I'd still suggest trying the LiveCD in 'try' mode - without your ethernet plugged in. I had nightmares about getting mine to work - I forgot to plug the ethernet lead in on a re-install and the little bugga found my wireless connection .... Heck, it's worth a try ;)

Hope you get it sorted,

Regards,

Phill.

---

### Post by solomonhomicz on 2009-12-14
Wireless is working, I'm on now.
No idea what actually fixed it.
But, here's the sequence of events;
After posting I saved a copy of the Wireless Troubleshooting Guide from the Ubuntu community documentation.
I restarted on Ubuntu and checked my device manager icon and wireless was now visible but listed as not activated.
Hmmm..., so I began to wonder if my previous problems with nspluginwrapper had anything to do with it. I had marked nspluginwrapper and flashplugin installer for complete removal before the upgrade (these went kaput on last upgrade, got sick of being prompted to send yet another freakin' bug report on every freakin' update). So, I marked them for reinstallation (I know there's not a network connection, but I've found packages remain even after "complete removal"), it said it failed to connect to repository, continued anyway, it installed some packages lib..32, didn't catch whole name.

Nothing different with network manager tried to unlock networks to edit no response, had to kill the app, it died after entering password.
Tried to get to Windows, no way, BS!

So I rebooted (if all else fails), hey the network manager was running, it recognized all the available networks, but would not connect, it would run and then say wireless network disconnected, then 5 or 10 seconds later it would start running again, same thing again and again.
Tried mounting Windows, no problem, got right in, copied the troubleshooting guide.

And then tried the hardware testing utility, it made a report, it all looked good. What the hell??? Meanwhile the little network icon swirling away throwing up popups "network now disconnected". NO s**t Sherlock.

So, what the heck, one more reboot, picked up a network within seconds after I could see the desktop........ok.....cool.....I guess?

So maybe you should just keep rebooting forever? Maybe whatever update snafu glitches out nspluginwrapper also glitches out the network manager? Is it because I'm on a 64-bit machine and I needed one of those 32-bit libraries? Who knows.

Anyway, I'll call it solved for now.

---

