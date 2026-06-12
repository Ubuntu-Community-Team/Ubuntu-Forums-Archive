---
title: "Can't get to X in new Ocelot install"
date: 2011-11-10
forum: Installation &amp; Upgrades
---

### Post by joshuajon on 2011-11-10
So I just installed ocelot from USB using the minimal / netinstall.  Everything went smoothly, except that grub was installed to /dev/sdb (usb drive) even though ubuntu was installing to a partition on /dev/sda.... go figure...

Now grub works, but I'm greeted with just a blank screen with a blinking white cursor.  If I press ctrl-alt-f7 I see a message "Checking for running unattended-upgrades:" and that's it.  

I can log in to the system on another tty and everything appears to be working.  When I try to start X I just get a blank screen.

Where should I go from here?

P.s. I just attached a copy of Xorg.0.log.  I had to .tar it because of the file size limits on this forum though.

---

### Post by joshuajon on 2011-11-10
So I feel a tad foolish.  I think I simply misunderstood how minimal a minimal install was.  I didn't have xinit or any window managers installed :-/  I'm apt-getting it now, so I should be all set.  :lolflag:

---

