---
title: "oem-config failure &amp; solution"
date: 2014-03-12
forum: Installation &amp; Upgrades
---

### Post by Nopposan on 2014-03-12
I just want to share this little wisdom I've gained from an experiment that I just performed.

I wanted to see if, contrary to popular wisdom, oem-config-prepare would work on a low-memory laptop.

It doesn't.

When I rebooted my machine after entering the oem-config-prepare command, I got a blank screen that lasted at least forty-five minutes; I stopped counting. Honestly, if ubiquity would have eventually come up, I don't care after forty-five minutes of waiting. My end-users won't have the patience for that.

No offense to ubiquity or oem-config though, I was just trying it out.

So I was in a situation. Did I have to totally reinstall? No. The answer was to boot into recovery mode, choose "clean up" to "try to make more space" and THEN arrow down to "drop to root shell". (By choosing "clean" you make the system writable for when you go to root.) Then, you can issue the easy and obvious command, "apt-get remove oem-config". You might go ahead and do an "apt-get clean" and "apt-get autoremove" too. When you reboot, voila, no more oem-config-prepare trying to use ubiquity and therefore your system will boot normally.

'Hope this helps somebody.

Thanks for reading.

---

