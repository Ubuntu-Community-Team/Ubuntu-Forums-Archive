---
title: "nvidia drivers 10.04"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by saias on 2010-05-12
Hi, 

i have an hp 3560 and i just upgraded to 10.04. after the installation and before the initiall screen comes up i recieved an error message saying the system runs in low graphics. I tried to both the recommended drivers but could be installed. 

I also tried to install the latest nvidia drivers from the nvidia website. In this case everything seems to work fine except the extra visual effects options which disables compiz and glx dock.

I am really disappointed and i cannot understand how fixed problems in previous versions reoccur. 

Please help!
Thanks

---

### Post by saias on 2010-05-13
is there any  way to go back to 9.10?

---

### Post by Grenage on 2010-05-13
I don't believe there is a way to 'downgrade'.

When you try to activate the driver in Ubuntu, what does it say?

---

### Post by wojox on 2010-05-13
Yeah, they did some weird stuff with the video drivers this release.

About all you could do is reinstall 9.10.

---

### Post by saias on 2010-05-13
for both the proprietary drivers i recieve the following message:

"Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log"

on the log: "nvidia_173 is not the alternative in use"


formatt will be the last option but it looks like the only one.

---

### Post by wojox on 2010-05-13
Try this [[HOWTO] Install NVIDIA drivers manually on Lynx]("http://ubuntuforums.org/showthread.php?t=1467074")

---

### Post by saias on 2010-05-13
That was perfect!

Everything works just like before! I was very disapointed.

thank you!

---

### Post by wojox on 2010-05-13
Your welcome. :)

---

### Post by vwbug on 2010-05-13
> **wojox said:**
> Yeah, they did some weird stuff with the video drivers this release.

About all you could do is reinstall 9.10.

That's what I did. :)

---

