---
title: "how to run clean up after upgrade"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by mehtdosa11 on 2008-04-30
i upgraded a couple of days ago and the process halted right at the end before the clean up and reboot options.
i've managed to sort out the the network-manager problems, but i would like to run the clean-up. [if needed]
 i've seen the instructions on the forum before but now i can't find them!!
can anyone help please?

p.s. i have two versions of firefox now; the new beta3 and the old 2. is this right after the upgrade or is it because of the non clean-up?

---

### Post by bigken on 2008-04-30
you could go to add/remove and install Remove orphaned packages also clean out the temp folder thats about it as far I know

---

### Post by Wobedraggled on 2008-04-30
```
sudo apt-get autoremove
```

This will clean up any packages that are no longer needed.

---

### Post by OrangeCrate on 2008-04-30
Here's a good tutorial on keeping your computer clean:

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

(Be careful, if you decide to follow tip #3.)

---

### Post by mehtdosa11 on 2008-04-30
thanks for all the help, i've run the apt-get one and its removed some unnecessary packages.

i will try some of the other ones later...

---

### Post by Huss on 2008-11-14
Thanks! Worked for me.

---

