---
title: "Upgrade to Lucid on a headless box stopped VNC workign"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Tass on 2010-03-27
Hi

I have a headless box that I've been running 9.04 on without any issues.  I have VNCed into it to manage my drives, etc., but otherwise used it as a file server.

I upgraded to 10.04 and I can no longer connect using VNC.  If I plug in a monitor & reboot it boots up fine, automatically logs in and I can VNC in.  Unplug the monitor & reboot I can ping the machine so know it's up, but can't VNC in.  If I then connect the monitor, nothing comes on.

So - something isn't starting up with a monitor.  Any ideas?

Edit: working, that is - not workign

---

### Post by Tass on 2010-03-30
So - I've done some more troubleshooting:

With a monitor plugged in it boots up fine, automatically logs in, the desktop is displayed on the monitor, I can VNC in, I can ping it, I can browse to a share on the machine from another machine using a UNC path.

Without a monitor plugged in it seems to boot up, I can ping it, I can browse to a share on the machine from another machine using a UNC path, the additional drives specified in fstab are automatically mounted but I can't VNC in.
NOTE: When I attach a monitor at this point nothing is displayed - the monitor detects that it has been plugged into something, but changes to what looks like standby mode.

So - I'm hoping someone has a solution? :D

---

### Post by Nirami on 2010-03-30
I have the exact same problem but no solution. I was using the same xorg.conf that I had to use in order to make it work in Karmic. Removing the xorg.conf did not work either.

I've since downgraded to Karmic again, but I'm thinking about installing Lucid on a VMWare-box in the mac to try it out from there.

---

### Post by Tass on 2010-04-18
So I presume no one's made any miraculous breakthroughs with this then?

As an update for any anyone reading, I've reinstalled from scratch, using 10.04 Beta 2, with the same results.

Hopefully this will be resolved in the final release.....

---

### Post by psyke83 on 2010-04-18
> **Tass said:**
> So I presume no one's made any miraculous breakthroughs with this then?

As an update for any anyone reading, I've reinstalled from scratch, using 10.04 Beta 2, with the same results.

Hopefully this will be resolved in the final release.....

Check your /var/log/Xorg.0.log for any useful information. It seems possible that Xorg is refusing to start due to no monitor being present. Keep in mind that VNC only works when the graphical environment is already up and running.

Another option would be to connect to the computer via freenx, because a) it's faster than VNC, and b) freenx runs a custom X server on-demand each time you connect, which means that it should work without a monitor connected.

---

