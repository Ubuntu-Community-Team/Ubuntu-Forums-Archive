---
title: "Canon ImageClass D530 Unable to Print"
date: 2015-01-02
forum: Installation &amp; Upgrades
---

### Post by SpikeLS6 on 2015-01-02
Too late I found this printer is not on the Ubuntu compatible printer lists due to Canon changing the driver codes for thes models, then returning to their proven CUPS drivers.

When trying to print a test page I get error: Idle - src = libcanon_pdlwrapper.c, line = 514, err = 0¥nDEBUG: PID 3857 (gs) exited with no errors.

I have installed a couple of times the latest Canon Driver Update: Canon D530/D560 UFRII LT ver.2.9.

From the Forum I learned that some problems are fixed by installing some 32-bit files such as libc6-i386 and lib32z1. I could not find the ia32-libs on either Software Center or Synaptic.

I have Googled the Internet for this error, but can find nothing about it.

Short of getting rid of this MFP and obtaining a wireless HP model, is there anything else I could research on getting the Canon working with Ubuntu 14.04 64-bit?

Spike

---

### Post by SpikeLS6 on 2015-01-07
Please see Thread "[SOLVED] Printer Model Suggestions for solutions provided by Forum members that made my Canon D530 print normally with Ubuntu 14.10.

---

### Post by asdf14 on 2015-01-09
To save others' time, here is a direct link: [http://ubuntuforums.org/showthread.php?t=2259719&p=13202514#post13202514](http://ubuntuforums.org/showthread.php?t=2259719&p=13202514#post13202514)

And the relevant code:

```
sudo apt-get install libxml2:i386
sudo apt-get install libjpeg62:i386
sudo apt-get install lib32z1
sudo apt-get install libstdc++5:i386 libstdc++6:i386
sudo restart cups 

```

Afters CUPS restarts, just open your Add Printer GUI and the test page should work.

---

### Post by pancho45 on 2015-04-30
Thank you very much!!!!!!!!!!!Now my printer works wow thanks

---

