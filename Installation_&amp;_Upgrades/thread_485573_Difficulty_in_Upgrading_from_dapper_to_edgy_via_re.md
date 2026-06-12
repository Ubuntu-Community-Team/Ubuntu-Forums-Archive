---
title: "Difficulty in Upgrading from dapper to edgy via repository DVD's"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by ramnarayan on 2007-06-27
Hi

Am currently on Dapper (6.04) and am trying to upgrade to Edgy (6.10) and then hopefully to fiesty (7.04).

The machine is a IBM - Lenovo t 60 with dual boot. Dapper works very well with lots of stuff configured and running. (only exception being the winmodem)

I don't want to do a clean install - i leaves me with too much tweaking and reinstalling to do and am afraid i might break a running system. 

Secondly i don't have a connection to the internet that will allow over the net install or upgrade (in fact its a 45 kbps dial up).

Third - i have the complete edgy repository (1 Boot CD and 4 DVD's worth). 

The problem is that synaptic does not seem to recognize the CD or  DVD's or load the packages of edgy - making it not possible to upgrade via synaptic. The DVD's work because i upgraded from dapper to edgy on another laptop (gateway) - the dvd's were recognized and i marked them as edgy_main, edgy 1  and so on. The boot cd works because i used it live to check. 

So, on the T60 , to work around i created an two  iso images of the first boot cd and of another package dvd (edgy_main) and mounted them as 

/media/SEA_DISC/edgy/

The sea_disc being a removable usb hard disk  and the mount partition (where i mounted the iso at)  are  VFAT file system.

then added the following lines into sources.conf

deb file:///media/SEA_DISC/edgy/ main restricted

After this i tried synaptic again and tried to reload the packages where i got this error message

file:///media/SEA_DISC/ubuntu_edgy/dists/main/restricted/binary-i386/Packages.gz: File not found


I tried removing one of the two iso images and reloading - but the same error message crops up.

I tried keeping the two iso images in two different locations and reloading (after editing sources.conf) i still get the same error message(s)

Would someone please advice and help as to what can be done to do the upgrade - using these dvd's .

much thanks
ram

---

