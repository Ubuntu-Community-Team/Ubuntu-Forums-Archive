---
title: "Ubuntu 17.10 won't shut down"
date: 2017-10-29
forum: Installation &amp; Upgrades
---

### Post by spencer2 on 2017-10-29
I upgraded from 17.04 to 17.10 earlier this week & I've not been able to correctly shut down my laptop since then. The only way to shut it down is to hold the power button: I've done multiple updates since the upgrade & still no luck. Please help me figure out how to turn my computer off correctly please

---

### Post by jpberes on 2017-10-29
Dear Spencer,
You can try the following inside a terminal window (to open the terminal press <CTRL> <ALT> T) and enter shutdown -P now
This should shutdown your computer properly and immediately ...
Normally the next times the normal shutdown should work
Regards,
JP

---

### Post by starhawk2 on 2017-10-29
**poweroff** [ENTER] in Terminal or CLI does it nicely for me, usually...

---

### Post by spencer2 on 2017-10-30
Thank you for the responses, but those didn't work. I've read that there are issues with Nvidia video cards -- my card is intel & I'm using an Acer Aspire F15. This only started happening after the 17.10 upgrade.  

```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
```

Could my shut down issue be similar to Nvidia issues? Does not being able to do proper reboots/shutdowns effect my updates?

---

