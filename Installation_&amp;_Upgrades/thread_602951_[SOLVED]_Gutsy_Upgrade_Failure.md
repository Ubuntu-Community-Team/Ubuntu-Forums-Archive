---
title: "[SOLVED] Gutsy Upgrade Failure"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by beansdad on 2007-11-04
Upgraded Fiesty to Gutsy on Acer laptop and this went without hitch. Looked good s thought I'd do likewise on desktop. Upgrade seemed to go OK until reboot. Grub loads OK and then goes to brown screen and box saying:

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem."

View details gives:

"(process 5490): Gtk-WARNING **. This process is currently running setuid or setgid. This is not a supported use of GTK+. You must create a helper program instead. For further details, see:
[http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)
Refusing to initialise GTK+"

The link provides no solution.

It then repeats this above except with "(process 5494)" at the beginning and then goes on:

/etc/gdm/Xsession: Beginning session setup.
x-session manager: error while loading shared libraries: libgnomecanvas-2.so.0: cannot open shared object file: No such file or directory"

If I click "OK" it goes to a black screen with the timer circle thingy and nothing else happens until I switch off and switch back on when it all happens again.

If I choose recovery mode from grub I end up at a command line and seem to be able to do some things. I've tried (from other posts) to repeat the update, upgrade, reinstall sequence; reconfigure; configure - all to no avail!

I would prefer to clear this rather than do a complete fresh install of a download and burn to CD as I want to avoid having to reinstall all sorts of other stuff.

Any suggestions?

Posted this on Absolute Beginners Talk but think I should have put it here.:confused:

As an aside - these forums have been enormously helpful in the past and this experience has not sent me running back to the blue screen OS that I tried to use for the last 20 years. Thank heavens for Ubuntu!

---

### Post by beansdad on 2007-11-05
Can anyone help please?

---

### Post by beansdad on 2007-11-08
Please, please, please help.

---

### Post by beansdad on 2007-11-09
Solved by default - did a clean install from CD. Thanks to all who looked.

---

