---
title: "Freshly installed system freezes just after loading screen. How do I diagnose?"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by Jiminy Cricket on 2010-01-27
I recently upgraded from Hardy to 9.10 Kubuntu. The install went smoothly, and when I boot up, the loading screen (the one with the progress bar) does its thing. Then I see the 'waiting' cursor (in Kubuntu, the two dots chasing each other around in a circle). I see this for about two to three seconds, then the entire thing freezes up and I can't do anything, including switching to a virtual console. How do I figure out my system's dying words so I can figure out what's going wrong?



As a (sort of) aside, when I open files in /var/log for reading with cat <file> | less, I have to Page-Down a whole bunch to get to the most recent stuff. Is there a way to jump to the bottom, or read with something other than what I have been using?

Edit: Though I did say that I was having this problem with Kubuntu, I also tried installing vanilla Ubuntu and Xubuntu and had the same problem. I think it may be a problem with X and my ancient ATI Radeon 9200 PRO, but as I said, I don't really know how to find out.

---

### Post by mikewhatever on 2010-01-28
Looking at the logs is a good idea, if you aren't daunted by cryptic messages. To look at the last 10 lines of the log, use <tail log-name>.
<tail -n XX log-name> will show XX lines from the end, for instance, 50.

---

