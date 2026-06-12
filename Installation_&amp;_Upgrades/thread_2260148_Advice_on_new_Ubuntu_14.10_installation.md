---
title: "Advice on new Ubuntu 14.10 installation"
date: 2015-01-09
forum: Installation &amp; Upgrades
---

### Post by kaudley on 2015-01-09
Hello,

I'm going to install Ubuntu 14.10 on my ultra book and I'm looking for advice on my HD setup.

Installed currently is a 250gb SSD and a 120gb mSATA drive.  I would like to have my /Home partition as an advanced file system, leaving me with the choice of either BTRFS or ZFS.   

Possible scenarios for installation:

- / on the 120GB msata /home on the 250GB SSD.  Seems like not a very god use of space and no redundancy. 

- create a 120GB partition on the 250gb SSD and mirror that with the 120GB msata drive, use for /home with BTRFS or ZFS.  give the rest of the space to / ?

Any thoughts or suggestions on this?  I also have an old mechancel 1TB laptop drive, I could remove the 250GB SSD and maybe bcache the 120GB .....  so many options.

---

### Post by kerry_s on 2015-01-09
i just installed on my ssd, leaving hd alone. the hd just shows as a mountable drive i used gparted and labeled it storage. i put things i want to save there. this install i just let ubuntu erase and install, usually i select something else and just put /root on the ssd but this time i wanted to see what it would do.

i'm just messing, distro hopping, haven't decided what i want to keep. currently playing with ubuntu gnome 14.10

---

