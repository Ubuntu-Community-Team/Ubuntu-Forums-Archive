---
title: "After install, kernel loads, but never boots"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by bdlamprecht on 2006-07-14
I have an VIA M10000 board that I have tried multiple times to install 6.06 and it appears that the install finishes just fine, however, after rebooting to run the new install, grub loads, uncompresses and loads the kernel, but then just hangs after it states that it is "Loading Linux."  I just installed 5.10 to see if the problem existed there, but it does not and boots completely without issue.  This was with a server install and running the LAMP install where I encountered this problem.  I have tried the Normal LiveCD install, but in that case, the LiveCD starts fine, but after selecting install, it begins to ask a few questions, but then just hangs (although the CD continues to spin up/down) for up to 1 hour before I finally give in.  Ideas, suggestions, hints?

---

### Post by gratefultux on 2006-07-14
When it said "Loading Linux", how long did you wait?  I know that for the first boot it can take a little longer than expected, since it will install some more packages right after loading.

Just a thought.

---

### Post by bdlamprecht on 2006-07-14
I waited for around 30 minutes before I gave up.  There was no disk activity or anything of the sort.  It said the kernel was uncompressed and ready, but I never see any drivers loading, hardware recognition, disk verfication, etc.  It would almost appear that there was issues with grub not functioning correctly, but I verified that the grub config looked okay.  Still left a little clueless.

---

