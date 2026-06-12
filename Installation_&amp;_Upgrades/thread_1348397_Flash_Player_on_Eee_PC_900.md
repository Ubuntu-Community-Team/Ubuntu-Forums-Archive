---
title: "Flash Player on Eee PC 900"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by FRanzH on 2009-12-07
Hello,

I have been searching, reading and trying for the past few days to successfully install Flash Player on my Eee 900 running UNR.

I have tried using the software centre, which I get told: Not available for your hardware architecture.

I have tried 10 and have read that it doesn't work with Eee 900, and I have tried downloading 9 and moving the .so file to /root/.mozilla/plugins/ and also the 10 .so file but none have worked.
(I have restarted firefox and even the laptop :) )

I finally have come here to ask for help after searching the forums and google trying what I can with my limited knowledge of Linux.

So, is anyone able to help me install Flash Player on my ASUS Eee PC 900 running UNR so that at least youtube works?

Thanks for any help!

---

### Post by leclerc65 on 2009-12-07
Try this
1- Close Firefox sessions
2-  sudo gedit  /etc/apt/sources.list
  make sure that the bellow 2 lines exist
    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner  (replace karmic by the appropriate release)
    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner (replace karmic by the appropriate release)
3- save the sources.list
4- 
sudo apt-get remove flashplugin-* --purge
sudo apt-get update
sudo apt-get install adobe-flashplugin

---

### Post by FRanzH on 2009-12-07
Thank you very very much!

I followed your instructions and now it works perfectly! 

Thanks again, leclerc65! 

Much appreciated,
Francis

---

