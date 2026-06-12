---
title: "Accidently canceled upgrade"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by Axis on 2008-10-31
So while upgrading I accidentally canceled out of the terminal which canceled the upgrade. Well after a reboot ubuntu is running in only 800x600, i can't update all of the way. After I try and do a "Partial upgrade" it says I can't. I don't know what to do, I have updated as far as I can however its not fixing anything.

I NEED HELP!!!

Thanks,
Axis

SOLVED PART 1:
I updated to 8.10 fine by doing the following
> **rolandsabang said:**
> 
i run below commands to complete the upgrade:
dpkg --configure -a
sudo apt-get dist-upgrade


However as of now, I am still in 800x600 would this be at all linked to the fact that "ubuntu-desktop" needs updating, but it wont? Its darkened in on the update manager and it wont let me install it.

---

### Post by rolandsabang on 2008-10-31
Hello Axis, I run in to the same problem but find a fix in this forum posted by blwegrzyn as follows

i run below commands to complete the upgrade:
dpkg --configure -a
sudo apt-get dist-upgrade

I am running it right now, but my internet connection is slow so it will take a few hour to see the result. I will come back to you and report the result ( if my system still is alive )

---

### Post by Axis on 2008-10-31
That deffinatley got me in 8.10, but I can't use restricted drivers, I can't get out of 800x600, none of my start up services are starting. HELP! I'm almost there guys :)

would this be at all linked to the fact that "ubuntu-desktop" needs updating, but it wont? Its darkened in on the update manager and it wont let me install it.

---

