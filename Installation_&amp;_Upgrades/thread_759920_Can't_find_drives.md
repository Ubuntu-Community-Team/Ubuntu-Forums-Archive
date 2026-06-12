---
title: "Can't find drives"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by Maintech on 2008-04-19
For those who have SATA-2 drives and the operating system keeps hunting for the drives and not finding them....usually going into a loop where it tries all drivers and when it reaches the last one and fails it loops back to the first driver and starts all over again.

I have searched these forums and found all kinds of suggestions like: NOAPIC, ACIP=OFF, NOPOLL, etc and none worked. Still had the same issue. I was installing a different distro and having the same issue that I have with the drives in Ubuntu but in the boot options it had an option I had never seen. I tried it and it booted! I was curious so I downloaded the new Hardy that was on DistroWatch and it booted (to my surprise) but took quite a while. After installing it would not boot from my hard drive. So, I put the cd back in and booted it up and added the boot option I had seen in the other distro and booted. It booted up twice as quick. I installed. I am writing this from Hardy. It works great. So, you want to know what the boot option is?   NOMSI

Soon as I close this I am going to go find out exactly what that boot command does. Then I'm going to try to find out why it isn't offered as a boot option in Ubuntu since it works great.

Hope it works for you as well as it did for me.  :guitar:

---

