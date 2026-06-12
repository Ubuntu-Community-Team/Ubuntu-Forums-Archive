---
title: "Several issues following Lenny -&gt; Karmic upgrade"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by hazelsct on 2009-12-13
Hi, I just upgraded from Debian Lenny to Ubuntu Karmic.  I blew away and reinstalled / but kept /home, and the new user I created works fine, for the most part (except for the first issues below).

There are several problems with my old user(s) though:

[LIST]
[*]Wireless network reliability is worse than before (Dell Latitude D830n, iwlagn).  In Lenny, when it crapped out, I would just re-select the network in N-M, and it would re-find it, though I sometimes had to do this twice.  At worst, "rmmod iwlagn && modprobe iwlagn" fixed the problem.  In Karmic, neither of those works, the least painful way to reset the wireless is to hibernate and resume.  The iwlagn process often consumes 100% of CPU, which I had never seen in Lenny.
[*]Setting the background image doesn't work: I see all of the images in the dialog, but when I select one, all I get is a solid color for the background.
[*]CompizConfig is impotent: every time I change a setting, it gets reverted in a matter of seconds.  I saw something about a gconf backend; could this be overwriting my config?
[*]Speaking of which, where is the gconf editor?  "Configuration Editor" is not in any of my menus, though gconf-editor is installed.  I could run it from the command line, but it's supposed to be somewhere in the user interface, right?
[*][SOLVED - I think] The SQLite change in evolution metadata management was a bit scary -- at first all I got in all folders was "Unable to retrieve message\n[?]".  Restarting evolution fixed that, and got evolution started on a 6-hours-and-counting campaign to "Storing folder" for my whole system.
[/LIST]
Any ideas on the first four would be much appreciated; I'll post again if the fifth issue remains a problem.

Aside from these, the upgrade has been pretty painless, and has fixed a number of pretty big problems I had with Lenny.  And there's a lot to like about Karmic that I hadn't expected.  Thanks for a great release!

---

### Post by hazelsct on 2009-12-16
Fixed the second issue in gconf-editor desktop -> gnome -> background, checked "draw_background".  And evolution finally seems happy after about three days of various flailing.

Found info on the iwlagn problem at [http://ubuntuforums.org/showthread.php?t=1239871](http://ubuntuforums.org/showthread.php?t=1239871) -- apparently it also applies to my 4965.

That's two down, one known issue, one very minor (gconf-editor), and one serious issue left (ccsm) - submitted the ccsm problem to a separate thread [http://ubuntuforums.org/showthread.php?t=1356586](http://ubuntuforums.org/showthread.php?t=1356586) .

---

