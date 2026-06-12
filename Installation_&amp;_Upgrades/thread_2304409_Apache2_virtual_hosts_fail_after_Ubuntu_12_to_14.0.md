---
title: "Apache2 virtual hosts fail after Ubuntu 12 to 14.04 upgrade"
date: 2015-11-26
forum: Installation &amp; Upgrades
---

### Post by iansavell on 2015-11-26
Last night I decided to upgrade my Ubuntu 12 LTS test server, evidently to Ubuntu 14.04.3 LTS. Throughout the update I selected the default of keeping the existing configuration files when asked. I don't recall being asked about any Apache files, and those appear to be new. Apache2 is now version 2.4.7.

After the upgrade none of the websites on that test server, which were all name virtual hosts, worked. Even the "default" website didn't (doesn't) work. All attempts to access the web server land in /var/www and show a directory listing of /var/www (which obviously it claims is /) including an html folder, which is where the default Apache2 page is now (it was in /var/www before the upgrade). sites-enabled/000-default.conf says the default document root should be /var/www/html but that clearly isn't happening. I've now stripped out all my virtual hosts except for 000-default to narrow the options. I did earlier note the requirement that virtual host configuration files now have to have a .conf extension but making that change (the new 000-default file was already .conf) had no noticeable effect.

I must have made some really obvious mistake and need to understand it rather than just starting again from scratch, the whole purpose of upgrading was to see what would happen if I upgraded my production server. I've been running this for several years and never broken the server with previous upgrades, clearly I've been getting cocky!

Ideas?

---

### Post by TheFu on 2015-11-26
Config options changed between the apache versions. There should be a migration doc somewhere.

Sorry, I don't recall the details anymore, but they were trivial.  Grant? That comes to mind.

---

### Post by iansavell on 2015-11-27
TheFu: There's a migration document of sorts for Apache2 [here]("https://httpd.apache.org/docs/trunk/upgrading.html"). Its main point is that access control has changed from the rather obscure "order/allow/deny" to a slightly more obvious "require granted/denied" syntax. That might be what you're thinking of. There's a compatibility module that permits the "old" syntax though. Also the virtual hosts configuration files should end with a .conf extension, which the new 000-default does have and which I added to all mine.

In attempting to fix this I deleted all virtual hosts configurations, except for the 000-default supplied by the upgrade which uses the v2.4 syntax, and even that default didn't work, specifically Apache2 ignored the "DocumentRoot /var/www/html" directive in the virtual host conf and used "/var/www" as the document root for all sites. In effect Apache2 was ignoring all virtual host configurations. The default page was still available if you knew to go to "server/html" (virtual hosts were not available in the same way because without the conf files access to their folders was denied)

So, for the benefit of anyone else looking at this thread, everything now works. But why?

Essentially I've done nothing, except to **restart the server**. Yes, I know, I should have tried that first. Tech support 101, turn it off and back on. I thought all the reloading of Apache2 would do the trick, but no.

True story. A few years ago I was on a train - one of the then new "Pendolino" electric trains on the UK West Coast line. Something was wrong with the heating/aircon making the carriage somewhat hot. Halfway through the journey the train manager announced that they'd consulted the engineers and been told to reset the system. The train stops, all the lights go out, the lights come back on, the train sets off, the climate goes back to comfortable. To reset a Pendolino train you turn it off and back on...

Ian

---

### Post by TheFu on 2015-11-27
Reload should have worked.

I was stuck on an overnight train from Rome to Vienna that had the 6-bed cabin heater stuck on. The Austrian conductor demanded we close and lock the door, so thefts won't happen. Must have lost 5lbs in sweat that night. Only the top 4inch windows would open and without the door open no cross-ventilation was possible. The huge windows where sealed for the winter. Never plan to travel overnight by train again.  ;)

---

