---
title: "Failed Upgrade : HELP  (6.06 to 7.10)"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by heislord5 on 2008-03-05
I tried to do a mark all upgrades upgrade from 6.06 to 7.10.  changed sources list from 6.06 sources to 7.10 sources.

Upgrade failed partially through because of xserver stuff being in more than one package or something like that.

Now when I reboot, I don't have windows, only command prompt.  I tried different stuff to get the upgrade through but have been unsuccessful.  Can't reinstall xserver.

Important stuff is on the computer and I need help recovering.  Is there a way to install the 7.10 ubuntu over the other one without losing personal files and data?  HELP!

:)

Thank you.

---

### Post by Pumalite on 2008-03-05
Upgrade is done 6.06>6.10>7.04>7.10

---

### Post by Pumalite on 2008-03-05
Get a Knoppix Live CD and save your data: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Burn to disk and boot from it.

---

### Post by heislord5 on 2008-03-05
Is there a way to reinstall ubuntu on top of what I have without losing or having to copy to external my data?

---

### Post by heislord5 on 2008-03-05
could I just as easily boot from the ubuntu live cd? or does Knoppix provide more functionality?

---

### Post by Pumalite on 2008-03-05
Knoppix has the ability to mount all your drives/partitions automatically at boot.

---

### Post by Rocket2DMn on 2008-03-05
You screwed up your install, that method of "upgrading" which you did not does not really work correctly.  I don't even know how you have a working terminal!  You should do the LiveCD deal like Pumalite suggested and backup all your data to an external hard drive.
You can't reinstall without overwriting what's there - it requires you to format the partition.

---

### Post by bsmith1051 on 2008-03-05
checkout my proposed FAQ,
[http://ubuntuforums.org/showthread.php?t=711648](http://ubuntuforums.org/showthread.php?t=711648)

I tried to clearly spell-out that upgrading 'through' multiple versions isn't supported.  You've probably got a 'franken-OS' install now.  I had a similar problem when I tried to upgrade a 6.10 system to 7.04 but it failed because of some web-server modules I'd loaded.  The server continued to operate but it had no idea what 'version' it really was anymore.

P.S. Please feel free to post comments on my FAQ, e.g., if it would've been helpful to you or not.

---

### Post by heislord5 on 2008-03-05
Thank you all for your posts.

I've used the Ubuntu 7.10 cd to live boot.  I am able to access a usb drive and move stuff over from the HD to it.  I was also able to just zip up the home directory and move that zip file to the USB drive (I did it as root).

Thanks a lot....so now I know there is no other way.

---

### Post by bsmith1051 on 2008-03-05
If it's any consolation, the soon-to-be-released Ubuntu 8.04 looks like it's gonna rock!  So it's probably a good time to do a fresh install....

---

