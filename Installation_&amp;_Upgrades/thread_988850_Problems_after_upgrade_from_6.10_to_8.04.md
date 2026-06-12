---
title: "Problems after upgrade from 6.10 to 8.04"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by jaytu on 2008-11-20
Hi All,

Just tried to upgrade from 6.10 to 8.04 via the upgrade mangager. All was going well, then when it had about 2mins remaining the whole system froze. Mouse & Keyboard were not responding.

Eventually, I did a hard reboot. It was booting using the upgraded information, but when it get to the login screen, the system will freeze. The mouse can be moved over the screen but won't click on anything and the keyboard does not respond.

Reset button is the only way to reboot. On some boots the login screen will on half load before freezing. Once I did get to login, typing the password was very sluggish and once the desktop loaded it froze again. I did notice thought that the upgrade settings seemed to be load on the desktop, slightly icons etc.

I have tried booting from the various versions in ther grub menu but still get the same problem. I have noticed as it's booting that "load hardware devices -FAILED" does show up ?

I have tried dpkg --configure (update, upgrade etc...) from the recovery terminal, same result.

I do have a 8.04 live cd. Can I run the dpkg --configure but utilise the live cd ? Is there any way I can complete the original upgrade from the live cd ? I want to try and keep my setting from the upgrade rather than a clean install.

Any help anyone could offer would be very much appreciated. Thanks

---

### Post by jaytu on 2008-11-21
I've been trying various thing to try and correct this, but I'm still getting the same results. I'm just wondering if I'm looking for the right problem...

If I'm getting to the log in screen would that mean that boot sequence and loading of ubuntu is OK ? ie The correct harddrives are being read and mounted correctly.

or

Could it be a graphics card thing... meaning it's not loading the the correct devices and therefore freezes at the login screen?

---

### Post by lswb on 2008-11-21
Unfortunately upgrading from 6.10 to 8.04 is not supported. The only supported upgrades were from 6.06 to 8.04 (6.06 was the previous LTS version) and 7.10 to 8.04. (And lots of people had trouble even with those supported upgrades) 

It may be possible to complete the upgrade with a lot of manual futzing around, but the easiest thing is probably to backup whatever data you want to keep and do a clean install.

---

### Post by jaytu on 2008-11-22
Ahhh... well that explains it. So that's why it would be freezing at login ?

With out sounding to stupid, could you please advised how to backup from the terminal ?

Also, will most of my setting transfer into 8.04 ?

With a clean install from a live cd will it change the partition or will it just install where the old files were ?

Thanks !

---

### Post by lswb on 2008-11-22
You can backup when running the live CD. I don't know how you have your system laid out as far as storing data. If you just need to copy your home directory, and you have a large enough USB drive or other backup location, you can just open nautilus from the live CD, navigate to /home on your hd ubuntu partition, and drag and drop your home directory to the backup location. I'm pretty sure that the live CD can mount the hd without needing to use a terminal. 

If you need to compress the files so they fit on the backup drive, from a terminal you can 

tar cvfz /path/to/backup.tar.gz /path/to/your-home-directory.

data from location other than your home directory can be saved the same way.

If you have a large enough backup drive, you can also use gparted from the live CD to clone the entire partition. That way you'll be sure to have saved eveything.

There is a howto thread running on the forums you can check:
[http://ubuntuforums.org/showthread.php?t=35087&highlight=backing](http://ubuntuforums.org/showthread.php?t=35087&highlight=backing)
for more info.

When you do the install from the live CD I believe you can choose to install to an exisiting partition, however, old files on that partition will be lost. That presents another option, if your hd has enough space, you can install to a different partition, leaving 6.10 on the hd. Then, when you're running 8.04, you'd be able to copy info over from the 6.10 partition when you needed it.

---

### Post by jaytu on 2008-11-23
lswb: Thanks for the information... I just tried to run the live cd  (using  'install ubuntu without changing any setting' )and when it gets to the desktop I get the same problem as I originally described, that is the mouse pointer will move over the screen but wont click on anything and the keyboard wont respond. On a second attempt at booting...when it got to the desktop the screen didn't display correctly, a strange pattern was displayed.

Could the issue be a graphics thing ?

I can boot into windows (dual boot system) with no problems just can't get ubuntu to work. Everything was working fine before I tried the upgrade ??????

---

### Post by jaytu on 2008-11-23
-- SOLVED --

Got it to work... 

I went into the BIOS settings under 'CHIPSET MANAGEMENT' and changed  'AGP MODE' to '1x'(It has always been set to '4x'). 

I verified this by again changing it back to '4x' rebooted and had the freezing problem. I have now set it to '2x' and this seems to work fine also.

If anyone could explain the reasoning for this I'd be interested to know.

This may also mean that I had 6.06 and not 6.10 as stated.

Thanks for responses.

... how can I can this post to 'solve' ?

---

