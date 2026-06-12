---
title: "update-desktop-database taking hours to complete"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by dan_c on 2007-09-23
Hi all,

Just wondering if anyone has seen this before. I'm installing xfdesktop4 using apt-get from the console and the process seems to hang before it can get finished. The output from apt-get install xfdesktop4 seems to freeze at:

[FONT="Courier New"]"Setting up xfdesktop4 (4.4.0-0ubuntu3) ..."[/FONT]

I hit ctrl-c and ran dpkg -C, it tells me that xfdesktop is only half-configured (makes sense) so I try reconfiguring as suggested (but with verbose debugging). I get the same output from

[FONT="Courier New"]dpkg --configure -a --debug=2000 [/FONT]

as with apt-get but there seems to be lots of disk activity. When I run top in a console I can see the process "update-desktop-database" taking up most of the CPU. Since the verbose output from dpkg stops at "Setting up xfdesktop4 .." I'm guessing that it is waiting for update-desktop-database to complete before the package can completely configured.

So, the question is - how come update-desktop-database is suddenly taking so long? It seems to be running in quiet mode (-q) so I'm not even sure where to look to get some trace to see what's going on.

Any advice or info on this would be appreciated.

Many thanks,

dan

---

### Post by dan_c on 2007-09-23
Update: 

I solved this particular problem by removing my ~/.wine folder and the ies4linux directory that I had recently installed under /usr/local/share/applications. My guess is that these must have contained some circular symlinks that were causing problems (infinite loop?) when running update-desktop-database. 

Situation normal now :)

dan

---

