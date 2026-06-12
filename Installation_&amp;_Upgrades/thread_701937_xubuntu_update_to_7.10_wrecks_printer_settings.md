---
title: "xubuntu update to 7.10 wrecks printer settings"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by spetey on 2008-02-19
Hi *buntu fans,

I just upgraded my Xubuntu to 7.10, and the printer settings no longer work - I can print to the same network printer, but the settings (like duplex printing) are lost.  The behavior has been really weird.

My printer's called "ricoh-suave".  The gui in "Applications|Settings|Printing" has the settings there correctly, and when I first tried ```
lpoptions -p ricoh-suave -l
``` it listed duplex as default.  When I try "localhost:631/admin" for CUPS in Firefox, it lists my ricoh-suave and the PDF printer.  But when I print I get single-sided printing.

And I couldn't do administrative stuff in the CUPs browser - it didn't ask for a password when I hit the admin tab, and didn't give me options for the printers either.  So I tried 'sudo firefox' but that doesn't work any more; neither will xubuntu let me log in as root from the login screen.  I can see maybe that's good security-wise, but it leaves me stuck.  Finally I tried ```
sudo lynx
``` and looked at localhost:631/admin from within a terminal.  There it lists *only* the PDF printer!  And now, suddenly, when I try ```
lpoptions -p ricoh-suave -l
```
or ```
lpr -p ricoh-suave file.ps
```
it doesn't recognize that printer!  Yet I can still print from firefox ... what on earth is going on?!

I gotta say - much as I love linux, printing has been a huge pain for me for almost ten years now.

Thanks in advance for any help.

spetey

---

### Post by spetey on 2008-02-21
Sorry that was long-winded.

In summary, duplex printing used to work.  Then I upgraded to Xubuntu 7.10.  Now, though CUPS shows duplex on (at localhost:631) and lpoptions shows duplex on, nothing is coming out duplex.  How come for?

Thanks,
Steve

---

