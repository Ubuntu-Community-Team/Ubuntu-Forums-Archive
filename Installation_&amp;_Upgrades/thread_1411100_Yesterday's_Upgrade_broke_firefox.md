---
title: "Yesterday's Upgrade broke firefox"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by arvevans on 2010-02-19
I have two computers running Ubuntu Gnome with Firefox.  Upgrades yesterday (18 February 2010) at about 1430 MDT hours (UTC 2130 hours) broke Firefox on both machines.  Firefox is present in the menu, and in /usr/bin/firefox, but it will not launch, not even from the command line.  I have tried "sudo apt-get remove firefox" followed by "sudo apt-get install firefox" but the problem persists.

When attempting to launch firefox, it does give me a tiny brown spot at the upper-left side of the screen.  This can be expanded by dragging so that it is a full screen, labeled "Firefox" but there is no content in the screen...only blank space.

Not sure what to do next.

_._

---

### Post by arvevans on 2010-02-19
Found it!  In my $HOME directory there is a .mozilla directory.  In this is/was a "firefox" directory.  After uninstalling firefox, I removed each and every sub-directory and file in $HOME/.mozilla/firefox..then deleted the $HOME/mozilla/firefox directory itself.  Then I re-installed firefox (sudo apt-get install firefox).  After a reboot, all is well.  Firefox works properly.  I had to rebuild all my firefox preferences data, but that is a small price to pay in order to get firefox back working again.
_._

---

### Post by lefty01 on 2010-02-19
Thanks, I was looking in my home directory for .firefox.
Guess the name stuck in my head =D>=D>:redface:

---

