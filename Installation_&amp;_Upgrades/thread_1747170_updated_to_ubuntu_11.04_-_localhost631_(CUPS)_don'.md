---
title: "updated to ubuntu 11.04 - localhost:631 (CUPS) don't work"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by megafedt on 2011-05-02
Dear All

I just upgraded to ubuntu 11.04 - now localhost:631 (CUPS) doesn't work anymore. However, I can still print. When I try to reload on localhost:631 I get:

"Unable to connect - Firefox can't establish a connection to the server at localhost:631."

This is really really annoying. Please help. I've tried to google a lot, but I cannot see what's wrong. I've tried to completely re-install all cups-packages with synaptic, but that didn't work. Right now I think cups is running:

$ status cups
cups start/running, process 899

Worst thing is that previously today, it worked... Please advice...

---

### Post by dburns on 2011-05-02
I have the same problem....localhost:631 worked ....and then it didn't. Restarting cups doesn't do anything....removed it and reinstalled it and still no joy.  Had no problem with Ubuntu 10.10.

---

### Post by megafedt on 2011-05-03
> **dburns said:**
> I have the same problem....localhost:631 worked ....and then it didn't. Restarting cups doesn't do anything....removed it and reinstalled it and still no joy.  Had no problem with Ubuntu 10.10.

Thanks for supporting me and making it clear that apparently it's not just me who did something stupid. So, AFAICS cups *IS* running but it's only the web-interface that doesn't work. I don't know too much about IP-tables (or if there are other firewall mechanisms in Ubuntu that could cause problems), but I don't think it's my hosts, hosts.allow or hosts.deny -files. Is CUPS running using Apache web server? If yes, then please tell us how to verify that Apache is running so the CUPS-webinterface can begin to work again.

---

### Post by wilddice on 2011-05-04
SOLUTION:

System> Administration > Printers  (in 'classic gnome mode')

Under the Server menu, settings, make sure the printer is published, and allow printing from the internet).

Seems the upgrade turned these settings back off (Bad package managers!!!:razz:)

---

### Post by dburns on 2011-05-04
Sweet!  Thanks wilddice....worked like a charm!

Cheers1

---

### Post by dburns on 2011-05-04
Still get the "Unable to connect to CIFS host...." but at least Firefox can find localhost:631

---

### Post by megafedt on 2011-05-05
> **dburns said:**
> Sweet!  Thanks wilddice....worked like a charm!

Cheers1

Oops, I accidentally wrote the below answer in another thread which is now marked as "SOLVED", however, my problem with CUPS is only 50% solved now... Thanks for the help, here's my updated situation:

The GUI web-interface is back (using the above-mentioned procedure by system->administration->printers with the old classic gnome-desktop), but after I enable the printer and  reprint some of the stopped jobs I get this: "Print Error" + "There was a  problem printing document 'Test Page' (job 272): 'Stopping job because  the sheduler could not execture the backend."

I've tried to google for this and I found some suggestions, primarily a  few years back. I tried a few things, however please advice/suggest  something if you have an idea about what might solve this...

I've also tried to use the "Printing troubleshooter" by "Enable  Debugging" (should cause the scheduler to restart). I then click  "diagnose" and also get this error message in my "Document Print  Status"-queue: "There is a missing print filter for printer 'PDF'".

My debug output is the following:

E [05/May/2011:10:50:39 +0200] [Job 272] Stopping unresponsive job!
E [05/May/2011:10:50:39 +0200] Unable to execute /usr/lib/cups/backend/cups-pdf: No such file or directory
E [05/May/2011:10:50:39 +0200] [Job 273] Stopping job because the sheduler could not execute the backend.

Please help / suggest me some advice so I can begin printing to PDF again, thanks!

---

### Post by ChosenOreo on 2011-05-12
Hate to bring this thread back from the dead, but how would I go about fixing this using only the terminal (I have Ubuntu Server 11.04 Installed, No GUI exists on it)

-ChosenOreo

---

