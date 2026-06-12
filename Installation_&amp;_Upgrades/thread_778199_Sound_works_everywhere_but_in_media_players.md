---
title: "Sound works everywhere but in media players"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by realGaurab on 2008-05-01
I upgraded to Hardy on Monday.

I have a C-media audio device. I have taken advice from various sources and have reinstalled alsa driver almost 3 times but still no fix.

Thing is sound works great when I watch online videos - youtube, hulu, and other similar streaming video service. I have an application for alarm clock which works great. Wakes me up every morning with its great sound. But there's no sound when I try to play songs using Amarok or Rhythmbox, or video using VLC or Totem. I have all the right audio and video codecs installed so I don't think that's a problem. I also reinstalled restricted drivers package already this evening.

Like I said, I did search a lot on the topic and couldn't find any fix. I would appreciate any help.

---

### Post by wishyjr on 2008-05-03
i get a similar issue. But this also happened to me with gutsy - i was thinking that certain applications kinda 'hold on' to the sound driver. What i found with gutsy is if i quit Firefox then i could hear stuff from rythmbox. Does that work for you?

---

### Post by Minguo on 2008-05-03
I am having the same issues, but quitting Firefox doesn't seem to help. 

Rebooting does, but now I have rebooted for the third time today just to get sound back.  Is there a way to do take back control of your sound without rebooting?

---

### Post by realGaurab on 2008-05-05
I got the Amarok part fixed. 
Went to Settings -> Configure Amarok -> Engine -> Output Plugin
Changed the Output Plugin from Autodetect to Alsa and now I can listen to my music collection again, yay. 

I haven't checed VLC yet. Once VLC starts playing its sound, I'll be a happy man again.

---

