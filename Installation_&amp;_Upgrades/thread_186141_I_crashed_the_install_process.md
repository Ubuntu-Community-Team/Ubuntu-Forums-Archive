---
title: "I crashed the install process"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by Baasha on 2006-06-01
I just upgraded from Breezy to Dapper, using sudo update-manager -d, and got all the way through the new install, until just before the end.  The update manager was at the cleaning up stage and I got a message to close all open applications to prevent data loss.

I looked at my screen and thought, wrongly as it turns out, that the update manager was a separate process from the terminal, so I shut the terminal off.  Wrong, wrong , wrong.

I thought, ok I'll just reinstall from the beginning, but the computer says I am up-to-date.  How do I begin again?

---

### Post by johnc4510 on 2006-06-01
When you do:
ctrl+alt+backspace
Does the brief text screen say: Ubuntu 6.06 LTS
If so you are up to date

---

### Post by Baasha on 2006-06-01
Yes, it says 6.0.6, and so far everything seems to be working.  I was just worried that the install process did not complete.  I think it was just about to erase a bunch of files when I accidently shut it down.  Will these extra files, and whatever was to be done in the following steps, cause me a problem in the future?

---

### Post by johnc4510 on 2006-06-01
It shouldn't
Good luck and enjoy

---

### Post by Video Toaster on 2006-06-01
The installer was probably cleaning up all the old installation packages on your drive.  You can do the same thing manually by running "sudo apt-get clean" in a terminal window.

Enjoy Dapper!  I know I have. :D

---

### Post by az on 2006-06-01
[QUOTE=Baasha]Yes, it says 6.0.6, and so far everything seems to be working.  I was just worried that the install process did not complete.  I think it was just about to erase a bunch of files when I accidently shut it down.  Will these extra files, and whatever was to be done in the following steps, cause me a problem in the future?[/QUOTE]

You can run the package manager and have it complete any pending tasks.

You can also run

sudo apt-get -f install

to do that.

After which you are fine fine fine.

---

