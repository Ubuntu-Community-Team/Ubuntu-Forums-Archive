---
title: "Startup sound in LiveCD, then locks up so can't install"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by vettejock99 on 2008-02-01
I feel like this is going to be something where someone screams "Search!", and I want you to know that I have.  Unfortunately, I haven't found a similar situation even with tons of hits.  Anyway, help would be appreciated.

I am trying to install Ubuntu, or Kubuntu Gutsy on my HP zt3000 notebook that is a few years old.  It is a custom model, with the ATI 9200 and a Broadcom bluetooth chipset.  I believe sound card is standard.  When I try to boot to install Ubuntu/Kubuntu, no matter what settings I use, the desktop starts, the startup sound plays, and then it either just freezes immediately or crackles a bit during the sound and then stops dead.  For a few seconds up until that point the mouse even works.  Truth be told, I have tried a few other distros this week as a result of this not working for me, and even some non Ubuntu based distros such as Sabayon and Mepis fail in the same way.  Others, such at OpenSuse and Puppy Linux do work, but I really want to try Ubuntu again.  Can someone help me fix it?  I have heard of many Gutsy problems with HP, but none like this.  Will a Hardy Alpha fare better?

Thanks again.

---

### Post by taurus on 2008-02-01
At the first boot screen from the CD, there is an option to scan disc for defects.  Pick that to make sure everything on the CD is good when you burnt it.

---

### Post by vettejock99 on 2008-02-01
Sorry, I guess I should add that I did do that.  It said there were no problems with the media.

---

### Post by vettejock99 on 2008-02-02
No other suggestions?  Really?

---

### Post by SpiderGorilla on 2008-02-02
Is the LiveCD really important or can you install from the Alternative CD?

---

### Post by zoke on 2008-02-02
If Ubuntu fails but other linux distros work, this appears to be a bug. Before you go filing a bug at launchpad, could you try to figure out what sound card you have ? This means either installing another OS and then using that to figure out what kind of soundcard you have, or using a linux livecd based on one of the distros that work.

---

### Post by vettejock99 on 2008-02-05
I wanted to get back to everyone so they would know their responses helped.  I did use the alternate install CD, and the install worked.  Not really sure why it acted so funny with the sound driver (which uses ADI Soundmax drivers under Windows), but it is at least working now.  ATM, I am tempted to try Hardy Alpha 4 as well....

---

### Post by Partyboi2 on 2008-02-05
If you are wanting a stable system I suggest sticking with gusty till April when Hardy is released.

---

### Post by vettejock99 on 2008-02-05
> **Partyboi2 said:**
> If you are wanting a stable system I suggest sticking with gusty till April when Hardy is released.

Yeah, I decided that is sage advice!  I'm sticking with Gutsy for now.

---

### Post by vettejock99 on 2008-02-06
Well, although it did install and runs fine mostly, including through the playing of the startup sound, I tried playing music and it locked up again.  The chipset is an Intel 8201DB(M)ICH4 on a i855PM motherboard.  Guess I will look for a bug listed, or post one myself.

---

