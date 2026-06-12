---
title: "Networking not working on Feisty!!!"
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by hopestorm on 2007-01-25
Hi Guys,

I got a real headache.

I upgrade to Feisty 2 days ago. At the beginning, the wireless doesn't work. The wired connection is fine. I then follow the help on desktop to install "ndiswrapper", follow the steps there, unsuccessful because I can not find my wireless card CD. I then try to use the "network" utinity in the "control center". There are no wireless item at all. However, I did modify some settings for "wired connection".

After a while, I found my wired connection refuse to work any more.  every time I enable the wired connection, it is disenabled after I close the dialog.

Now no networking for my computer at all. I can not even install any necessary packages to make the network work.

Please help!!!

---

### Post by FXWGBill on 2007-01-27
Kind of the same thing here....  I've kept up with the upgrades and this last one seemed to crash my networking.  at this point trying to download the alternate cd to see if I can fix it with it.  I get basically the same thing Hopestorm is saying...  My NIC is not listed in the network connections at all, nor in the network tools.  Loop back is there, but eth0 is gone.  ANY suggestions would be appreciated.  As soon as I get this cd downloaded and burned I'll try a few more things.  I did notice that there are changes in the 'network discovery and setup' that are going to be included in the final release... Something ain't right.... (yet)


EDIT:
It's amazing how just a few letters can ruin your whole day.  After browsing and browsing through directories and the forums, what I FIANLLY discovered was that somewhere along the way, in the file:  /etc/network/interfaces      eth0 was deleted....

so I manually edited the file and added eth0 back in so that now we have:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

and it works fine...

Oh well... Live and learn 

You might check that too, hopestorm...

---

