---
title: "dapper to edgy upgrade annoyance"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by macubergeek on 2006-10-28
I'd appreciate any help you all could give me. 
I'm using Kubuntu
I upgraded dapper to edgy this way

edited /etc/apt/sources.list
using this in vi
%s/dapper/edgy/g
then did
apt-get update
apt-get upgrade
apt-get dist-upgrade

After the upgrade everything seems to work except one annoyance.
I boot the computer
I see Kubuntu splash screen and progress bar
I see black screen
I hit enter once or twice and get a console login
I hit alt-F7 then I see normal kde graphical login

My question is how do I reconfig to boot directly into the graphical login? What did I hose during the upgrade? What file do I need to edit and how?

---

### Post by surian on 2006-10-28
I'm having the exact same problem.

I restart the machine and it gives me the normal (although upgraded) kubuntu splash screen with a progress bar.  The progress bar completes and then I'm taken to a black screen with a cursor in the top left which blinks forever.

If I press "esc" to get into grub during the boot process and select the "safe" mode option (I forget the actual name of the boot option) I can log in as root to a command line and then do a "startx" to log in to KDE (although I prefer to use fvwm2 and can't seem to get that to start because the display isn't set correctly).

---

### Post by surian on 2006-10-28
UPDATE:

I got it working again by logging into the command line (as I described above) and then doing a dpkg configure: [FONT="Courier New"]dpkg --configure -a[/FONT].  Now I can get into the graphical login screen.

Hope that helps!

---

