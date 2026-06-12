---
title: "slow windows"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by JohnDillinger43 on 2012-12-08
I just upgraded from Oneiric to Precise, and now I'm getting some strange effects in using certain programs.  Nicotine+ is now phenomenally slow when changing tabs or minimizing.  LibreOffice is usually fine, but today when I had multiple workbooks open in Calc everything got incredibly slow.  I've had spotty issues with slow minimizing/maximizing with other programs as well.  Because it's not a specific program I'm assuming this is a compiz issue.  I made the (perhaps unwise) choice to upgrade rather than clean install 12.04, so I was thinking it might have to do with old settings.  I found a post on how to reset unity, thinking that might work, but when I tried it nothing happened.

I'm not an expert user, so I'd appreciate any direction on diagnosing or correcting the issue.  Glad to post more specifics if people can tell me what I should be looking for.

---

### Post by JohnDillinger43 on 2013-02-01
Still having this issue.  Definitely a graphics problem, because now I've noticed that with all my programs minimizing/maximizing is a little jerky.  Not mind-numbingly slow as with Nicotine (and DOSBox), but not smooth like it should be.  I downloaded a more recent NVIDIA driver, but I'm not sure how to install it, or if that's the most likely problem.  When I run the install script at the command line it tells me I have to log in as root.  Before I tried that I wanted to ask if that's the best course of action or if I can run a driver installation like that with sudo.

---

### Post by 2F4U on 2013-02-01
These two documents provide information about how to install nVidia drivers. nVidia drivers are provided by Ubuntu and it is recommended to use these. But there is also a way to install drivers directly downloaded from nVidia:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by JohnDillinger43 on 2013-02-03
Success!  Your comment about using drivers provided by Ubuntu made me go check to see what driver I was using, and it turned out to be nvidia-173 instead of nvidia-current.  Switched over to current and now things are much better -- no more slow windows in Nicotine+, DOSBox, or LibreOffice, no more choppy minimizing/maximizing.  I guess 173 was good enough for 11.10, but just couldn't hack it when I upgraded to 12.04.

Thanks!

---

