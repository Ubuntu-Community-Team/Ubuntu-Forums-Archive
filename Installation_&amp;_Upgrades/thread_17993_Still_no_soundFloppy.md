---
title: "Still no sound/Floppy"
date: 2005-03-04
forum: Installation &amp; Upgrades
---

### Post by ardvark on 2005-03-04
This is becoming a bit irratating. I've fully loaded Ubuntu several times and at the initial login and entering the Gnome desktop, I have sound and access to the floppy drive. At that point I change a few things, such as updating repositories, adding numlock,  turning off ntpdate, etc.  I then reboot, at that point I know have no sound  (I do get the drumbeat at login, but not after Gnome starts), and no access to the floppy drive. (/dev/fd0 doesn't exist)

I found out the problem so I'll post this in case some one else runs into this. I was trying to solve the slow internet access by turning off IPV6. The method I found to fix this was faulty (at least on my setup or the instructions weren't complete. The fix I used:

add these lines to file /etc/modprobe.conf

        alias net-pf-10 off
        alias ipv6 off

Well, that made the internet faster, but must have stopped modprobe from detecting  the floppy drive and the sound card..

---

