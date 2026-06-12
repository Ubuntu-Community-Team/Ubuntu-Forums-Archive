---
title: "Can't boot  ubuntu after upgrade 9.10 to 10.04"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by Pointswest on 2010-01-03
After upgrading to Ubuntu 10.04 from 9.10 I cannot boot from the grub menu.  Downloaded and installed grub 2 and can now boot my win xp disc but not the Ubuntu upgrade.  When I try to use the new kernel to boot Ubuntu it says "could not connect to Plymouth" then opens a command line sign-in then to a command line after password.  How can I get the Ubuntu harddrive to boot from this point?  I think this plymouth has something to do with the splash screen, but I don' know how it works.  

I can also upgrade using the  fix grub and dpkg choices but can never view anything on the screen after the updates. Any help appreciated. 

 Thanks

---

### Post by gsmanners on 2010-01-03
Upgrading to 10.04 is not advised at this time. Please see the following:

[http://ubuntuforums.org/showthread.php?t=1343449](http://ubuntuforums.org/showthread.php?t=1343449)
[http://ubuntuforums.org/showthread.php?t=1304172](http://ubuntuforums.org/showthread.php?t=1304172)

---

### Post by Pointswest on 2010-01-03
I guess this is good advice not to upgrade to this alpha release just yet, but I have already done it and I would like to fix this if possible.  I have two hdd's, one xp and one ubuntu, and I can't figure out why the windows drive boots with the grub but not the ubuntu.  My xp is on sda and the linux on sdb.  Sdb is the drive I have installed the grub2.  It shows the new revision number and the 32.9 kernel in the new grub list.  Just can't get past the command line after booting.  Using the command line and sudo reboot just starts the cycle over again just like the first boot and stops at the command prompt after using the login and password.  Any ideas or link to a fix?  Thanks


Edit:  If anyone else has this problem you can use the live cd to retrieve any files from the linux drive, then reinstall 9.10 but I was hoping for an easier solution than a reinstall.

---

### Post by Pointswest on 2010-04-20
I kept updating this through the command line in hope that would fix this problem.  I could see the packages being added and removed and the kernels updated but still couldn't get my desktop open.  After updating to kernel 32.21 I noted in my searching that xorg could have been removed with one of the upgrades so I used the command "sudo aptitude install xorg" and now my system boots and opens with the upgraded 10.04.

---

### Post by infamous-online on 2010-04-20
I didn't bother updating my machine and I won't until 10 has been officially released, the best you can do now is re-install 9.10 and wait 9 days until 10 comes out.

---

