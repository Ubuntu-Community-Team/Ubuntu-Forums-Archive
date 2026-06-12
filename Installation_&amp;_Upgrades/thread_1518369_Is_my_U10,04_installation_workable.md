---
title: "Is my U10,04 installation workable?"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by Randy Schilling on 2010-06-26
System: Intel EM64T Pentium(D)
Problems with U10.04 installation:
1. Live Ubuntu-10.04-desktop-amd64.iso cd does not boot consistently; meaning
there might be 1, 2, or 3 failed boot attempts before a successful boot into the cd.
iso was dloaded using bittorents and its md5 hashes were verified after burning.
Boots attempts fail at screen with 5 progression dots. 
2. Installed U10.04 suffers same boot inconsistencies.
3. Post installation problems.
     a. Tried to create a new directory using mkdir from a terminal. Response:
         "mkdir: cannot make directory 'com'. Read only file sytem."
     b. Tried to install 149 updates using Update Manager. Clicked Install - no response.
     c. In one session system stopped responding to any and all clicks.
         Click on a menu item - no response.
         For example click on Restart - no response. Had to hard boot.
 
Do I have a workable installtion? What's causing my problems?

---

### Post by darkod on 2010-06-26
Did you burn the cd at low speed, like 4x? The ISO might have been good, but the burn bad.

---

### Post by aphatak on 2010-06-26
Ubuntu 10.04 works beautifully with Pentium D - I have one working as a home theater PC.  I would suspect the CD burn.  If you have another PC, you might want to set it up with TFTP server, and try a network boot.  Alternatively, you could try putting the live image on a USB drive and boot from that.

---

### Post by Randy Schilling on 2010-06-26
I burned the cd at 4X and verified md5 hashes on the newly burned live cd.

Anyway, I'll try suggestion to use my USB drive.  If that fails, I'll try download/burn from a friend's pc,
and if that fails I'll try to learn something about TFTP and network booting.

Its encourqging to hear that U10.04 works with Pentium D.  Thanks

---

### Post by Randy Schilling on 2010-06-27
The responses to my post convinced me that my problem was in burning the live cd.

I tried the burn one more time with both my cd/dvd drives, each failed with boot problems.

Then I put the image on a USB stick.  Things went smoothly from there.  - Many Thanks

---

