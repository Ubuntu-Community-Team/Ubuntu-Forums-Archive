---
title: "Frozen - cursor moves, no keyboard response, no desktop response"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mykrob on 2009-04-09
Running Jaunty Beta with all updates on a Gateway M-6881 laptop.
This same laptop ran just fine with Intrepid. I replaced the stock INtel 3945ABG wifi mini PCIe with an Atheros 5007eg, which works great with the madwifi-hal driver.

Anyway, somewhere in the update series, a problem was introduced... My laptop freezes totally at random and without warning.It cannot be traced to any specific event that I can tell. I was using it for less that 2 minutes this morning when it froze. Peculiar thing is, when it freezes, I can still move the cursor, but nothing onscreeen responds to clicks. The screen may be frozen with a window mid-minimize or something... The keyboard will not respond, i am unable to drop to a virtual terminal, i have to hold the power button to power down then start up again.

This morning after the two minutes, I booted into recovery mode and ran all updates and noticed an update to the Intel driver.
Not sure if that will fix my issue, but best I can remember, this all started when and xorg-intel package was updated to improve performace. I may be wrong, though.

Just looking for help to track down the root of the problem and resolve it.

Thanks,
-myk

---

### Post by DizzyTech on 2009-04-09
Do you have an Intel Graphics Card?  If so, congratulations!  We all have this problem!

This bug is reported in Launchpad... check up on it at the following links:  
[https://bugs.launchpad.net/ubuntu/+bug/345119](https://bugs.launchpad.net/ubuntu/+bug/345119) (my bug)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/327844](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/327844) (exact same issue, mine is probably a duplicate)

---

### Post by mykrob on 2009-04-09
yup, an Intel 965GMA

Thanks for the info

---

### Post by mykrob on 2009-04-09
I realize I may be jumping the gun here, but after todays updates (ran in recovery mode), I have been on the laptop for a little over an hour using it as normal, and it is still running. There was an update to the xorg-intel package, hopefully that fixed it.

---

### Post by go7Ul1ai on 2009-04-09
Darn, and I thought this was happening because of my hard disc starting to fail, or some sort of over-heating problem.. at least I know it's a software and not a hardware problem ^_^

---

### Post by mykrob on 2009-04-09
dammit... I guess i did speak too soon. It just crashed on me.. Worked fine for three hours earlier today.

Just crashed after five minutes this time...

Oh well, such is the nature of betas, but I hope this gets ironed out REAL soon..

Sad part is, I see no way to revert to the original driver that shipped with the beta, it worked fine for me. I tried Force Version in synaptic, but there is no other version available.

---

### Post by mykrob on 2009-04-11
still crashing, no logical cause for this.. I cannot pinpoint any specific event that triggers it. Temperatures for hard drive and cpu are normal, just using the laptop like I have for the past year, nothing abnormal going on here... just locks up...

Hope this gets resolved.. Looks like activity on the bug report has stopped.

---

### Post by bigbrovar on 2009-04-11
Been having this issue for quite a long time. I installed some updates with includes the intel video driver and for a while it stopped. but just like 4 minutes again i had another freeze. Iam surprised this kind of thing should happen with an open source driver, but am confident that it would be resolved before the final release comes out.

---

### Post by bigbrovar on 2009-04-16
I just had this issue again .. just hours before release candidate for ibex.. if this issue is not sorted out it would be a major set back for jaunty since lots of laptop and netbooks use the intel GMA

---

### Post by Mindless Automata on 2009-04-17
Ugh!  Jaunty has kind of been a nightmare with intel video :(

---

### Post by trot2millah on 2009-04-17
> **Mindless Automata said:**
> Ugh!  Jaunty has kind of been a nightmare with intel video :(

Tell me about it! I don't think I will even be able to upgrade with the i945 graphics card on my desktop...it flat out fails.

---

