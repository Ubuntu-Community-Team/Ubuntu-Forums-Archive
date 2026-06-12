---
title: "Fontconfig issue"
date: 2005-10-27
forum: Installation &amp; Upgrades
---

### Post by daveguy on 2005-10-27
I recently upgraded from Hoary to Breezy using apt-get. During the upgrade, it ran into one problem it could not get past (there were some files in OpenOffice.org2 that it could not delete), and would kick me out to the command line. I got past that by deleting the files manually, then it finished the upgrade and would boot to the GUI.

However, I'm still having problems finishing the upgrade. Now it stop when it gets to "Regenerating fonts cache". The actual lines are:

    Setting up fontconfig (2.3.2-1ubuntu4) ...
    Not replacing deleted config file /etc/fonts/local.conf
    Updating font configuration of fontconfig...
    Cleaning up category cid..
    Cleaning up category truetype..
    Cleaning up category type1..
    Updating category type1..
    Updating category truetype..
    Updating category cid..
    Regenerating fonts cache...

After that it pretty much stops. I've let it run for a few hours before, and it hasn't gotten past it yet. And since it can't get past setting up the fonts, it pretty much won't set up anything else.

I'm stuck. Help!!!   Thanks!!!

Dave

---

