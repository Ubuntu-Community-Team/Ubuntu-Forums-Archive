---
title: "Upgraded to v14.04, can't log in. &quot;Session lasted less than 10 seconds&quot;"
date: 2015-07-16
forum: Installation &amp; Upgrades
---

### Post by TheBigH on 2015-07-16
Yeah, I think the title says it all. I did the one click upgrade, and now after the reboot I cannot log in. Or, I am getting logged in very briefly then immediately dumped back to the login screen.

I am also getting a slew of error messages when the computer boots up along the lines of "system-udevd[1250]: failed to execute 'lib/udev/socket'" and my xsession-errors file has some lines in it "Failed to connect to the VirtualBox kernel service"

Does anyone know how to fix my problem? Thanks.

**EDIT: **Giving up. I've decided to nuke the whole thing and start from a fresh install.

---

### Post by ubfan1 on 2015-07-16
Can you successfully login to a guest session?  If so, your (dot) files (the ones with a . as the first character) which may be listed by including -a in an ls command or "show hidden" in a gui) may be causing problems.  Start by moving to a temp directory or deleting .Xauthority,  then the contents of .cache.  If necessary, get rid of them all.  Some saved configs for programs might be lost, but if you copied the originals to a directory, you can copy back the pieces you need.

---

### Post by TheBigH on 2015-07-16
There's no guest account for me to log into, unfortunately.

---

### Post by ubfan1 on 2015-07-16
Isn't there a "guest session" choice under your regular user login on the login screen?  That comes with 14.04, it's not one you had to set up.

---

### Post by TheBigH on 2015-07-17
Nope, I can only select my own user name. There is no guest session option available.

I have also tried booting to a command line through recovery mode to see if I can look at .cache and .Xauthority that way, but all I have there is an empty directory.

Then I tried booting from an old Puppy Linux USB stick I had lying around, but I cannot mount my linux partition.

I really hope the upgrade hasn't ruined my partition.

---

