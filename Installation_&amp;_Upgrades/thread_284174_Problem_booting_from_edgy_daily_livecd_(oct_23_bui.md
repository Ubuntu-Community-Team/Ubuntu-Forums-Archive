---
title: "Problem booting from edgy daily livecd (oct 23 build)"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by anewbie on 2006-10-25
Last night I attempted to boot from the daily live cd (made last night - so it was the oct 23rd daily).

I validated the md5 of the iso i downloaded and validated the md5 from the cd after it was burned.

When I boot from the cd i get the start menu - if i hit return (to start) it shows the ubuntu logo for a while and then eventually a black screen with a single '_' in the top left corner. After that nothign happens. I tried to validate the cd (i think it was option 4 or 5) and it seems ok for a while but eventually i get a vbuff error. I tried to boot from the prompt (hit return to get a lilo prompt) and then gave the arguments "live noapic nolapic" but the same thing happened.

--
This is an older machine (msi kt3 (via kt333)) athlon 1.7 eide drives). The iso was the iso.386. THe reason I'm trying the daily live cd is that I will be building a new machine next week with a p965 and I wanted to test the cd as well as test install - first time running linux at home.

Btw I seen similar problems ([http://kubuntuforums.net/forums/inde...topic=9895#bot](http://kubuntuforums.net/forums/inde...topic=9895#bot)) but no answers...

[posted this in newbie but now i think maybe it goes here - not sure.]

---

### Post by jamaas on 2006-10-25
I had a similar problem and simply re-burning the iso, at a much slower speed made a better cd ... but is still dodgy and inconsistent.

Give it a try and good luck.

Jim

---

### Post by anewbie on 2006-10-25
I burned the cd twice (tried with two different cd). I also read the iso image (via dd) from the cd and validated the md5 - so it should be correct - shouldn't it ?

---

### Post by anewbie on 2006-10-26
Bleh.Problem was with the daily snapshot - now the hard part is finding a daily snapshot of edgy that works.

---

