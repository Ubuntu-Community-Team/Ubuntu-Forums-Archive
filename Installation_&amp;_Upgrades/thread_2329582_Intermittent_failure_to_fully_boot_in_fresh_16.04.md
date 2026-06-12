---
title: "Intermittent failure to fully boot in fresh 16.04"
date: 2016-07-03
forum: Installation &amp; Upgrades
---

### Post by snowmobiler on 2016-07-03
After using 14.04 for a long time, I did a fresh install of 16.04. I realized my SSD was not running the TRIM function but is set now to do so in 16.04. I had no issues with install. After changing the desktop background I noticed that sometimes after logging in, I would not get to the desktop. I would power down and then it would work. It was beginning to look like 'every other time' that it would not work. I also used ctrl-alt-f1 and typed REBOOT at terminal command and that seemed to work too. i went back to default background and it booted up fine this morning. Is this a Ubuntu bug, a memory bug, a video driver bug, etc? 14.04 ran fine on this laptop so not sure why 16.04 would have issues with default settings. That was my only thought about going back to original background. Otherwise, once I am up and running, all runs well and fast!

---

### Post by ubfan1 on 2016-07-03
Did you ever look at the SSD with the program smartctl -a /dev/sd?   ?   That might indicate any problems.

---

### Post by snowmobiler on 2016-07-03
I dont think its the SSD. Because it is Crucial, not Samsung, by default TRIM was not on. I just mentioned it in why I was upgrading. The completion to the GUI seems to be prevalent in 16.04. But with the default background, I have had successful back to back logins. Using some of the others, I would get intermittent hangups not getting to the desktop. The other backgrounds do have different resolutions, so maybe that has something to do with it. keeping the default for now.

---

