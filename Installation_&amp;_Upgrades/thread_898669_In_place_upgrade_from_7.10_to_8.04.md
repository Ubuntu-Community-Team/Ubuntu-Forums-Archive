---
title: "In place upgrade from 7.10 to 8.04"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by jmangan on 2008-08-23
I've just used the update-manager utility to upgrade an installation of edubuntu 7.10 to 8.04. The required packages were successfully downloaded and the installation was progressing well when I left it alone. On my return the system appeared to be locked up (no display, no response to keyboard, no apparent disk activity). After a suitable interval I took a deep breath and cycled the power. The machine rebooted with the same GRUB menu as I had before the upgrade (same kernel versons, options, etc.). The machine boots okay but when I try to logon with eith of the two user accounts I had set up I get a message that there is no HOME directory and do I want to use 'root' temporarily. If I do this I have no usable desktop.

I tried the 'Recovery' Grub menu option and started a terminal session. The 'home' diectory is indeed empty but so is 'boot' and 'grub' folder doesn't even exist (even though GRUB is still working and has the previous menu entries).

Clearly the partition I am looking at is not the only one that's available. Is there any way to either step back or move forward without destroying the data on the disk? There is nothing critical on the disk but it would just be a bit of a pain to re-create.

Any advice or (preferably) simple instructions to repair the situation would be very welcome!

---

### Post by cariboo on 2008-08-23
Start up in recovery mode and install the missing packges:

```
sudo apt-get install -f
```

This should install the rest of the packges you need to upgrade.

Jim

---

### Post by Edifier1007 on 2008-08-24
Hi 

I had the same problem on Ubuntu upgrade to 8.04.1. In my case it hanged while trying to reinstall locales. This is a bug and one of the workaround is given here - [http://www.archivum.info/ubuntu-bugs@lists.ubuntu.com/2008-07/msg38393.html](http://www.archivum.info/ubuntu-bugs@lists.ubuntu.com/2008-07/msg38393.html)

May be yours is the same case. As far as I could find out there is no way to go back after this fails during actual upgrade process. The only way is to go thru Failsafe mode and the do upgrade thru command line.

---

### Post by jmangan on 2008-08-24
Thanks Cariboo907, I tried that command and got an error message telling me that I needed to run 'sudo dpkg --configure -a'. After a lot of disk thrashing and screeds of text I got an error message about X. However when I rebooted I seemed to still be on 7.10, with X broken but my other data now visible. I am going to try fixing X and then have another go at the upgrade.

Thanks for the help.

---

### Post by jmangan on 2008-08-25
Well, all done!:) I had a couple of odd problems. After I fixed 'X' I had to redo the 'dpkg --configure -a' before applying over 300 updates but which kept sticking on 'locales'. I followed the advice in another thread to select the previous kernel version in GRUB and re-run 'dpkg --configure -a' from there. Completed the updates and I now have a functioning 8.04 system with just one little bugbear.

I am using a 'gb' keyboard layout with 'PC105 Intl' keyboard. In console sessions this works fine but in GNOME or in terminal sessions under GNOME it isn't. How hard can it be to fix . . . .

Thanks again for the initial suggestion!

---

