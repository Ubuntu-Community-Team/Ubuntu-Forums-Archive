---
title: "No Network after latest updates"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by thonuz on 2010-03-20
Hello,

I just updated last night and after losing gnome-panel was able to get it back from a terminal, but I have no network connections or nm-applet. I have kubuntu installed and when I went there I noticed it was first gone: both wireless and Ethernet no longer work. network manager is installed. Anyone know how I can fix this?? The only other thing I did was install Plymouth which I removed some time ago.
Thanks!

Im on a intel i3 asus with Atheros Ar9285

---

### Post by john@ukgillies.com on 2010-04-22
I have similar problem.  Have not explored this yet, but all networking has disappeared.

Will add details if I get to the bottom of this.

John

---

### Post by john@ukgillies.com on 2010-04-22
Found the following

[http://ubuntuforums.org/showthread.php?t=1168372](http://ubuntuforums.org/showthread.php?t=1168372)

followed the ideas there.

No network, but dhclient eth0 command allowed the machine to lease an ip address from the dhcp server. Networking capability back.

EXCEPT that Network Manager is still greyed out as unmanaged, and right click still gives Network Management Disabled.

Wonder what's going on with Lynx and NM??

John

---

