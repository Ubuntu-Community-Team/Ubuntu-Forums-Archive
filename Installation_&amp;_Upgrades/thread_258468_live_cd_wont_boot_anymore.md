---
title: "live cd wont boot anymore"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by igknighted on 2006-09-16
OK, I used to be a ubuntu user but have been using suse.  I am trying to go back to ubuntu, but my live cds wont boot.  I have several shipit cd's (standard x86 desktop), and none work, also a kubuntu disk i burned and an x64 ubuntu.  None load, so I have ruled out an error with the disk.  The computer has been working fine under windows xp pro and vista RC1, and the only hardware differences from when I used ubuntu before are a) the removal of my sound card in favor of the mobo sound, and b) the upgrade from an old geforce fx-5500 card to an ati x800.

The computer boots into the xserver, then after it initializes, the mouse curser appears and and then the Ubuntu greeting box, but then the screen hangs and goes no further.  It is also about 640x480 res.  Any thoughts on what the issue might be?

---

### Post by houstonbofh on 2006-09-16
> **igknighted said:**
> OK, I used to be a ubuntu user but have been using suse.  I am trying to go back to ubuntu, but my live cds wont boot.  I have several shipit cd's (standard x86 desktop), and none work, also a kubuntu disk i burned and an x64 ubuntu.  None load, so I have ruled out an error with the disk.  The computer has been working fine under windows xp pro and vista RC1, and the only hardware differences from when I used ubuntu before are a) the removal of my sound card in favor of the mobo sound, and b) the upgrade from an old geforce fx-5500 card to an ati x800.

The computer boots into the xserver, then after it initializes, the mouse curser appears and and then the Ubuntu greeting box, but then the screen hangs and goes no further.  It is also about 640x480 res.  Any thoughts on what the issue might be?

Problems recognizing your graphics card.  You should be able to boot into safe graphics mode.  Or the alt-install, but you will still have poor graphics until you can get the correct driver.

---

### Post by orb9220 on 2006-09-16
Also if you plan to use xgl compwiz in the future? I ask because ati cards are always more problematic than nvidia cards.

---

### Post by igknighted on 2006-09-25
OK, ive been busy so it took a while to get around to trying the alternate install CD.  It installed the system, but I have the same problem booting the system from the HD that I did from the live CD... but ctrl+shift+F1 wont take me to a text terminal so I can do anything.  It simply hangs with a light blue background and a mouse pointer (which moves with my mouse, but there is nothing to click and right click brings up no menu).  Note, this is the kubuntu alternate install, would the gnome version make any difference?

---

### Post by igknighted on 2006-09-25
> **orb9220 said:**
> Also if you plan to use xgl compwiz in the future? I ask because ati cards are always more problematic than nvidia cards.

Unfortunately yes, I am well aware that ATI can be a pain there (I threw out my old 9200 because it didn't work with Compiz), however I have XP and vista on my other hard drive that I use mainly for gaming (or curiosity with Vista) and I got 16 pixel pipes for the price of 8 with a comparable Nvidia offering, so I went with the ATI.

---

### Post by igknighted on 2006-09-25
ok, problem solved.  I booted in recovery mode and got the fglrx driver that way... sorry all, should have read more before posting again.

---

