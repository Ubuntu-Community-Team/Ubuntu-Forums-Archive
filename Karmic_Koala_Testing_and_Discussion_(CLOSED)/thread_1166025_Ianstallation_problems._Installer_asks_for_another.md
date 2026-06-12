---
title: "Ianstallation problems. Installer asks for another disc"
date: 2009-05-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Martijn van Es on 2009-05-21
I have problems installing Ubuntu Karmic Koala during the phase where files are copied to the HD.

At 70% (I think, after setting the sources list) the installer asks

"Please insert the disc labeled: 'Ubuntu 9.10 _Karmic Koala_ - alpha amd64 (20090513.3)' in the drive '/cdrom/' and press enter"

[LIST]
[*]As far as I know the disc the installer is asking for is in /cdrom/
[*]If I wanted to open the tray of /cdrom/ I couldn't probably because it is still mounted so I'm not able to change the disc
[*]The buttons <Go Back> and <Continue> don't send the installer to the previous or next screen
[/LIST]

I have tried it with 2 discs. One burned with K3B, the other using the CD burn instruction linked to from the download page.

---

### Post by ronacc on 2009-05-21
which cd are you using ? alpha1 or a daily ? livecd or alternate ?

---

### Post by Reiger on 2009-05-21
Hmm... Easiest thing to do, probably, is to grab a copy of a Jaunty Live disk, then dist-upgrade it.

---

### Post by Martijn van Es on 2009-05-21
I used the .iso linked to from in the sticky post Karmic Koala Alpha 1 Released
I picked the Ubuntu alternate install CD (64-bit PC (AMD64) alternate install CD)
This is the best version for my core2 quad CPU right?

---

### Post by ronacc on 2009-05-21
either should work , if it was the livecd I was going to ask if it ran ok in live mode. What kind of cd drive do you have , I had a problem a couple of distros back where it would install ok from my sata dvd ( I have 2 1 sat 1 ide ) but rhe same disk would do what yours is doing if I tried to install from my ide dvd .

---

### Post by Martijn van Es on 2009-05-21
My drive IS a IDE drive. (NEC ND3500) Could it be Karmic has a problem with IDE drives?

---

### Post by ronacc on 2009-05-21
I don't know I installed a fresh jaunty and have  been updating , I haven't seen other posts about it though and something like that should have caused a bunch of squwaks , Try dl'ing the livecd and see if that works .

---

### Post by Reiger on 2009-05-21
> **Martijn van Es said:**
> My drive IS a IDE drive. (NEC ND3500) Could it be Karmic has a problem with IDE drives?

Would be strange... In that case chances are that there's a BIOS setting spoling your fun (because usually it's the chipset controlling whether or not the SATA device runs in IDE mode or AHCI/SATA). And it is usually the ACHI mode that yields trouble (in particular WinXP won't like AHCI too much).

---

### Post by Martijn van Es on 2009-05-21
Well I just finished installing 9.04 from the live CD so I will upgrade to 9.10 alpha after I figure out how to do it.

---

### Post by ronacc on 2009-05-21
to go from jaunty to karmic open /etc/apt/sources.list and change all instances of jaunty to karmic and then update and upgrade .

---

### Post by Martijn van Es on 2009-05-21
I inserted the alternate installer CD I previously burned. The upgrade messagebox popped up and I clicked upgrade. That also worked just fine :)

Another thing
I tried to start all the programs that are visible under Applications and all started as expected except from the game Chess. Can someone confirm I'm not the only one with chess problems before I file a bug report?

I filed Bug #379190 for the glchess problem

---

### Post by ronacc on 2009-05-21
confirmed your bug .

---

