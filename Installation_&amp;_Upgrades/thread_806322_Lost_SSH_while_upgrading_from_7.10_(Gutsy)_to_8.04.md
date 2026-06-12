---
title: "Lost SSH while upgrading from 7.10 (Gutsy) to 8.04 (Hardy)"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by neilneil2000 on 2008-05-24
I just attempted an upgrade from Gutsy to Hardy via SSH on my server using the following command:

sudo do-release-upgrade

Everything was going well, all was downloaded and the system was doing the install until I got the blue configuration screen saying something about the new ssh and that it was going to restart ntp and sshd.

This was fine.  I then lost connectivity to the box.  As far as I can tell this is because this is my DHCP server and as I recall part of the upgrade process does something to the DHCP daemon.

I am currently in the situation where the box is running fine (with no DHCP working).  I can ssh and vnc into it but I can't tell what is happening with the upgrade.

Is there a way I can see what is going on?

HELP!

---

### Post by neilneil2000 on 2008-05-25
In the end this is what I tried:

1)Logged back in
2)Altered /etc/resolv.conf to point to router (was pointing to self but this was not working during the upgrade)
3)Restart networking "/etc/init.d/networking restart"
4)Reconfigure the packages which were interupted "sudo dpkg --configure -a"

It seems to be working so far...fingers crossed

---

