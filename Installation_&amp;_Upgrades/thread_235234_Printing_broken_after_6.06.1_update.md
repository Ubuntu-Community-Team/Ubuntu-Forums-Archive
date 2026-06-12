---
title: "Printing broken after 6.06.1 update"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by spirilis on 2006-08-12
After the 6.06.1 update it seems my printer no longer works.  I have a setup with an Ubuntu 5.10 server downstairs printing to an HP PhotoSmart 7960 over USB; after installing dapper drake initially, I had no trouble at all adding this network printer via IPP.  However, after the update on my desktop machine it no longer prints properly--I look at the printer and it says "Printing..." with nothing coming out.


On the print server (Ubuntu 5.10) box, here's an entry in /var/log/cups/error_log that looks curious--this was produced after doing a Test Page in Gnome's print manager
```

D [12/Aug/2006:17:59:25 -0400] [Job 50] cups->ppd = 0x89e7fb0
D [12/Aug/2006:17:59:25 -0400] [Job 50] cups->ppd->flip_duplex = 0
D [12/Aug/2006:17:59:25 -0400] [Job 50] width = 800, height = 1000
D [12/Aug/2006:17:59:25 -0400] [Job 50] PageSize = [ 612 792 ], HWResolution = [ 100 100 ]
D [12/Aug/2006:17:59:25 -0400] [Job 50] HWMargins = [ 18.000 36.000 18.000 36.000 ]
D [12/Aug/2006:17:59:25 -0400] [Job 50] matrix = [ 1.389 0.000 0.000 -1.389 -25.000 1050.000 ]
D [12/Aug/2006:17:59:25 -0400] [Job 50] Finishing.
D [12/Aug/2006:17:59:25 -0400] [Job 50] -dict-
D [12/Aug/2006:17:59:25 -0400] [Job 50] -dict-
D [12/Aug/2006:17:59:25 -0400] [Job 50] -dict-
D [12/Aug/2006:17:59:25 -0400] [Job 50] -dict-
D [12/Aug/2006:17:59:25 -0400] [Job 50] -mark-
D [12/Aug/2006:17:59:25 -0400] [Job 50] -dict-
D [12/Aug/2006:17:59:25 -0400] [Job 50] true
D [12/Aug/2006:17:59:25 -0400] [Job 50] END INIT 170 2025624 684975 1622424 338736 true 1065 4 <0>
D [12/Aug/2006:17:59:25 -0400] [Job 50] END GLOBAL 170 2025624 688459 1622424 339142 false 1064 4 <0>
D [12/Aug/2006:17:59:25 -0400] [Job 50] END GC 190 2045720 657292 1622424 328078 false 1053 3 <0>
E [12/Aug/2006:17:59:25 -0400] [Job 50] **No pages found!**
E [12/Aug/2006:17:59:25 -0400] PID 16580 stopped with status 1!
D [12/Aug/2006:17:59:25 -0400] UpdateJob: job 50, file 0 is complete.
D [12/Aug/2006:17:59:25 -0400] CancelJob: id = 50
D [12/Aug/2006:17:59:25 -0400] StopJob: id = 50, force = 0
D [12/Aug/2006:17:59:25 -0400] StopJob: printer state is 3

```

Any ideas?

---

### Post by spirilis on 2006-08-12
I seem to have fixed it.  I deleted the printer on both client and server, recreated it, and enabled Browsing in cupsd-browsing.conf on the server.  After that, gnome-cups-manager on the client autodetected the network printer and a test page printed perfectly.

---

### Post by leemckusic on 2006-09-07
Regarding Printing Broken after 6.06.1 update.

My printing stopped when I did the distribution upgrade from Breezy Badger,

for the simple case of a local printer, no server involved:

The solution that worked for me is to "remove" the existin printer and "add " it again.

Solution for me was to remove the existing printer and add the printer back in. The new cupsys software does not like to run with the previous printer configuration.

Here is a command line way to get at the printer utility with root privilege:

sudo gnome-cups-manager

--------- yes I am cross posting here from the Desktop Support section. I spent 2 days figuring out this staggeringly obvious thing... hope this saves you some digging.

---

