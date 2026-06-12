---
title: "Upgrade to 7.10 w/ separate &quot;home&quot; partition"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by Bartender on 2007-10-30
Sorry, I'm sure this has been covered but not finding it -

Running 7.04 with a separate "home" partition.  The PC does not have access to broadband.

If I have 7.10 on a CD, how do I install 7.10 over 7.04 and ask it to leave the "home" partition intact?  I've done several installs, both guided and manual, so can probly follow directions if someone can point me in the right direction...
 
Thanks!

---

### Post by taurus on 2007-10-30
Just mount that partition to /home BUT do not format it or your data will be gone (as gone in the wind).

---

### Post by Bartender on 2007-10-31
OK, Taurus, thanks.  A friend gave me a PC last night so I can practice what you're describing.

---

### Post by tact on 2007-10-31
I note you mention no broadband connection but you have a CD.  


If that CD is the "alternate" desktop installer CD:
Just boot up into your 7.04 system.
Slot the alternate installer CD in the drive.  It should auto run and pop up a dialog offering to do an upgrade.

You should have your 7.04 version fully updated first though...

---

### Post by Bartender on 2007-10-31
Well, I will have a CD after I go back to work in a few days with my little 2GB thumb drive and borrow some of their broadband  :)
I won't be able to update the 7.04 install.  Do you think that'll cause problems?  There's nothing of great import in the /home partition, I just wanted to see if I could upgrade without affecting the /home partition.

---

### Post by tact on 2007-10-31
not sure if not updating 7.04 will cause problems with the upgrade.

Perhaps forget about the alternate installer and use the normal desktop liveCD and boot from CD and do a clean fresh install.

even doing that... you can leave the /home folders untouched just fine.  again choose manual method for partitioning... only format the "/" partition...  and all will be cool

---

### Post by Bartender on 2007-11-05
Hey, guys -
Used manual install, let 7.10 format "/".  It also wanted to format the "swap" partition.  Set up "/home" to the original partition, asked it not to format, everything went fine.
The apps I'd parked in the panel under 7.04 were even there after the install of 7.10.

Thanks for the help!

---

