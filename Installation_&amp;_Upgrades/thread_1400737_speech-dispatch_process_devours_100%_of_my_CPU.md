---
title: "speech-dispatch process devours 100% of my CPU"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by nenes on 2010-02-07
Hello.

After my ubuntu 9.10 had updated automatically it started talk something when login screen appears. Also after every startup, process named speech-dispatcher appears and it uses almost 100% of CPU and I have to kill it manually. I removed file speech-dispatch from /etc/init.d, but it didn't help. Can someone help me, is it some speech synthesizer or sth like that? How to get rid of it?

---

### Post by Mark Phelps on 2010-02-08
Have you checked your BIOS settings? Some machines have speech enabled by default in the BIOS and that has been known to cause lots of problems.

---

### Post by Noobuntu-qa on 2010-02-21
I have a similar problem using Kubuntu 9.10 (64 bit) on a machine with an AMD dual core CPU and 4GB RAM. I noticed one of the processors had remained at 100% utilization for many hours. Checking system monitor reveals that the culprit is "speech-dispatcher" (version 0.6.7+git20090914). Killing this process bring the CPU utilization back to approximately 20%. Also of interest, I had the desktop clock set to speak the time every 15 minutes and this had stopped functioning. Immediately after killing speech-dispatcher, the clock speech began working again. I do not have any speech setting in my BIOS.

Has anyone had success solving this issue with speech-dispatcher? If not, I suppose the best solution is to uninstall speech-dispatcher?

---

### Post by windyweather on 2011-09-08
This is still a bug in 11.04. Yes uninstall speech-dispatcher. You may have installed it with Orca or some other Accessibility app. Kmag2 does not bring it in if you need a magnifier. BTW, I had to reboot to get rid of it. One would think that uninstall using Package manager would kill it, but it didn't. Apparently Python and Speech-Manager are in a deadly embrace of some sort that eats up the CPU. I'll check for a bug and put one in if there is not one.

Cheers,
ww

---

### Post by wilsonB on 2012-03-15
Having same problem here with speech_dispatcher

How to remove it?

---

