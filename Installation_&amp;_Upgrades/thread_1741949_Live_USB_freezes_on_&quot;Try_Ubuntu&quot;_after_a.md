---
title: "Live USB freezes on &quot;Try Ubuntu&quot; after about 2 minutes."
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by kaldor on 2011-04-28
I've been following the testing and development with a live USB for a long while now. I've used Daily builds multiple times throughout the testing process without any issue.

However, with today's official release, the liveUSB hangs after clicking "try Ubuntu". The cursor spins for a minute or two, then the whole system locks up and I need to do a hard reboot. I tested the .iso in Virtualbox and it worked fine, and the MD5 sum matches. I reformatted the USB drive and used Startup Disk Creator again, but the problem persists.

Is this a common issue? I haven't used the daily builds for a few days now. But, this is the first time I've had any issues at all. I always use Ubuntu's Startup Disk Creator. I am on Ubuntu 10.10, fully up to date.

Suggestions?

---

### Post by Hedgehog1 on 2011-04-28
The video driver for your Vbox and your PC is different.  I am guesing that your video card and the latest LiveUSB/ISO are not jelling.

What is your video card?


***The Hedge***

:KS

---

### Post by kaldor on 2011-04-28
It's an NVIDIA Geforce 8400m GS. It worked fine on the daily builds within the week, so why would that be changed now?

---

### Post by Gas Addict on 2011-04-28
I have an nvidia 330 GT in my laptop and mine takes about 5 minutes after I hit "Try Ubuntu" on 11.04 from my liveUSB.  I thought it was frozen but then I went off to grab a sandwich and came back to see it had worked. 

Could you have the same problem perhaps?

---

### Post by Hedgehog1 on 2011-04-28
> **kaldor said:**
> It's an NVIDIA Geforce 8400m GS. It worked fine on the daily builds within the week, so why would that be changed now?

I don't know - I have installed Natty on 3 different NVidia systems with no hassle.  But every new pull represents a little risk to bust something.

Do you have your earlier ISO from a few day ago that worked? You could install from that and used the update (in a few days when the servers are no longer swamped) to get up to the current level.


***The Hedge***

:KS

---

### Post by kaldor on 2011-04-28
Yeah, I still have that iso. I was just curious about this issue, but it seems to be just me.

---

