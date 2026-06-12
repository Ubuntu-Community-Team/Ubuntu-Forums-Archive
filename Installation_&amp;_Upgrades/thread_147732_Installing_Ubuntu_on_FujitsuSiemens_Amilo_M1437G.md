---
title: "Installing Ubuntu on FujitsuSiemens Amilo M1437G"
date: 2006-03-20
forum: Installation &amp; Upgrades
---

### Post by NDGsleeper on 2006-03-20
I used ubuntu, mandrake, debian and pclinuxos distros about a year 
ago on my desktop computer for few months without big problems. 
Then I bought a new Fujitsu-Siemens Amilo M1437G laptop with win XP installed, so I gave up linux for a while. 

Couple of days ago I wanted to give a try for Dapper Flight 5 
Live CD, but myexperiment ended in Live CD boot and a nice Ubuntu text (only the text, no menu). Then I tried with Dapper Flight install CD and the
same problem. Just the nice Ubuntu text and the computer freezes there.
(I checked md5 and burned the disks with a slowest possible speed.) I couldn't find any help from the forums for that problem so I downloaded the stable version 5.10. Now I get to the installing part but after rebooting I get stuck with the "starting hotplug subsystem". It's because ubuntu doesn't seem to like the onboard intel soundchip. I get pass this problem with pressing Alt+Sys Rq+E (Ctrl+c doesn't work) and the install continues, untill it's installing sound drivers and crashes and I can't complete the install.

I know that I can disable sound system by adding lines snd_hda_intel
and snd_hda_codec to hotplug blacklist. After that there's no errors
in "starting hotplug subsystem" anymore. The question now is that is there a way to continue the installing somehow?

I'd really liked to know some hints for my dapper problem as well.
The sound chip problem is probably fixed in dapper, so I wouldn't
have to care about that if I could just get the dapper work!
The most confusing thing is that my laptop seems to be supported
in this list [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsFujitsu](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsFujitsu) .

Even Kororaa Live CD with all the fancy xgl eye candy 
worked flawlessly!!
So what's wrong Ubuntu?!:confused: 

Thanks

---

