---
title: "Gutsy &amp; gnome-ppp"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by muka on 2007-11-01
Just thought I'd share my experience with Gutsy and gnome-ppp.

Due to circumstances I'm on dialup and using a laptop I employ the help of Luxiant HSFConfig to use the internal soft modem.

For some reason [seems it might be a script error] gnome-ppp is broken in Gutsy. So if you uninstall gnome-ppp and instead install KPPP then you should have a better result.

Cheers :)

---

### Post by edjski on 2007-11-03
> **muka said:**
> Just thought I'd share my experience with Gutsy and gnome-ppp.

Due to circumstances I'm on dialup and using a laptop I employ the help of Luxiant HSFConfig to use the internal soft modem.

For some reason [seems it might be a script error] gnome-ppp is broken in Gutsy. So if you uninstall gnome-ppp and instead install KPPP then you should have a better result.

Cheers :)

Thanks, using kppp seems to have helped but seems to hang when trying to start ppp.
Any thoughts? 
I had gnomeppp connecting to Cingular without issue under feisty.

---

### Post by edjski on 2007-11-03
> **edjski said:**
> Thanks, using kppp seems to have helped but seems to hang when trying to start ppp.
Any thoughts? 
I had gnomeppp connecting to Cingular without issue under feisty.

The log showed that the problem had to do with pap-secrets and chap-secrets. I found this webpage:[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html")
and learned what the two -secrets files needed. I created a text file with the correct info, saved it and then copied it into chap-secrets and pap-secrets (basically it was the log in info -username and password). Pretty simply in the end but took a while to find

---

