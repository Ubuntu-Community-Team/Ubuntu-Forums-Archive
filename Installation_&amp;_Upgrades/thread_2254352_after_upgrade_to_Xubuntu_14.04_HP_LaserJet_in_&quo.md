---
title: "after upgrade to Xubuntu 14.04 HP LaserJet in &quot;Idle - Filter failed&quot; (SOLVED)"
date: 2014-11-26
forum: Installation &amp; Upgrades
---

### Post by pvanos2 on 2014-11-26
[SIZE=3]Upgraded from Xubuntu 12 to 14.04
Printer : HP LaserJet p3015 connected via WiFi router.

When attempting to print anything, the job stays in the print queue with status "Idle - Filter failed"

A first searching through various forums about this problem yielded no solution.
Seemed to be a bug.

Then I checked into my log:
[FONT=fixedsys]tail -1000 /var/log/syslog  | grep -i "hp"[/FONT]
Then I found these lines of particular interest:

[SIZE=2][FONT=fixedsys]Nov 26 19:32:12 LUNA colord: Device added: sysfs-Broadcom_Corp-HP_Integrated_Module
Nov 26 19:32:12 LUNA colord: Profile added: HP-LaserJet-p3015-Gray..
Nov 26 19:32:12 LUNA colord: Profile added: HP-LaserJet-p3015-RGB..
Nov 26 19:32:12 LUNA colord: Device added: cups-HP-LaserJet-p3015
Nov 26 19:42:41 LUNA hpcups[2687]: prnt/hpcups/HPCupsFilter.cpp 548: cupsRasterOpen failed, fd = 0[/FONT][/SIZE]

The last error got me to    _[[COLOR=#0000ff]https://bugzilla.redhat.com/show_bug.cgi?id=1010580[/COLOR]]("https://bugzilla.redhat.com/show_bug.cgi?id=1010580")_[COLOR=#000080][U][URL="https://bugzilla.redhat.com/show_bug.cgi?id=1010580"]
[/URL][/U]
[/COLOR]feel free to read this post, but to cut a long story short, these are the commands to solve this problem:

[COLOR=#ff0000][FONT=fixedsys]$ lpstat -p[/FONT][/COLOR]
--> this line will return the name of your printer. Mine was called 'HP-LaserJet-p3015'
[COLOR=#ff0000][FONT=fixedsys]$ sudo lpadmin -p HP-LaserJet-p3015 -m raw
$ sudo service cups restart[/FONT][/COLOR]

Problem solved  ![/SIZE]

---

