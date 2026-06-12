---
title: "Intel video flakiness???"
date: 2009-09-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mariner09 on 2009-09-08
Is anyone seeing Intel video flakiness of late?  I had a system that was alpha2 installed and updated over time to alpha 4.  I had to reload and this time around did not enable the proposed repo and am now seeing a lot of video flakiness that I was not seeing in the past.  Is it just me or is there some magic Intel video update that was in the proposed repo that hasn't made primetime yet?

I'm getting a lot of green hinting on the screen edges and when I rotate my cube, the non-focus faces are all the same neon green.  Reminds me of the old TPB app for screen notification.

---

### Post by n6yga on 2009-09-08
I have a Dell 1405 that I installed Alpha 5 on on Saturday. Then The updates that came through on Monday updated another 129 megs of stuff. So far, Karmic is very fast and the Intel crap has been fixed.

I really put the machine through it's paces and have found the only problem is with Empathy. Otherwise, rock-solid.

Mark.

---

### Post by VMC on 2009-09-08
> **mariner09 said:**
> Is anyone seeing Intel video flakiness of late?Of late?! I'm experiencing "flakiness" since I installed karmic. It all depends on what Intel chip you have. There are several topics that have some sort of fix on the problems.

The strange thing is something is being done, I just don't know what. I use to have to use "nomodeset" on the kernel line, now I don't. So the kms portion works. I'm just about to remove the old intel2.4 driver and see if the new one works again.

---

### Post by mariner09 on 2009-09-09
What I'm seeing is a green, maybe neon green haze to certain things like edges, under the awn bar, in the non-focus panes of the compiz cube.  Seems like it happens more when heat climbs, this tells me I may have a bad CPU fan which I've been suspecting for some time.

---

### Post by VMC on 2009-09-09
Actually, the topics I was thinking about are for jaunty. Karmic is another matter altogether. I don't know what Intel chip your IBM Thinkpad has, but I have a i865 chip. 

I just today removed the old Intel-2.4 driver an installed the newest one. It sometimes works for extended periods of time, and other times it freezes up sooner. I did notice some color problems.

If I use "vesa" mode then everything works. Only problem is I'm limited to 800x600. Can't live with that.

there's already a bug report against the i865.

---

