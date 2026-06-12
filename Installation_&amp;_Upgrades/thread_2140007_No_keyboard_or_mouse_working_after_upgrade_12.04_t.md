---
title: "No keyboard or mouse working after upgrade 12.04 to 12.10 and 12.10 to 13.04"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by benzan on 2013-04-28
Hi,
I have been running Ubuntu 12,04 for quite some time now and decided to upgrade to 13.04. I did start the upgrade to 12.10 which had to be installed before upgrading to 13.04

The upgrade to 12.10 took about 2 hours but after rebooting the system I was left with a login screen and not functioning mouse and keyboard. My keyboard and mouse are Microsoft (sorry) 2.4 GHz wireless with one receiver. I added a Dell USB keyboard and noname mouse but still no mouse or keyboard functions. Did some reading in the forums and on the internet and did read some messages about the same problems, where it was adviced to press the shift key and choose an earliers kernel.

So, I rebooted the system, did hold down the shift but in the menu there was no previous kernel, only 3.2.0-36. So, I decided to choose the Ubuntu with Linux 3.2.0-36 generic pae. After booting my mouse and keyboard do work without problems.

In my ignorance I supposed that this problem perhaps was allready solved in 13.04 so I decided to run the upgrade to 13.04.

Same thing happened, no keyboard and no mouse functioning. Again, booting with the shift held down gave me the Ubuntu 3.2.0-36 generic pae option and then again the mouse and keyboard do work. 

So now I could change the grub loader to load this by default, but I am curious what I am missing to have the mouse and keyboard working after a normal upgrade and reboot.

Thanks for your time and ideas,

Kind regards,
Ben

---

### Post by mareid on 2013-04-30
I am experiencing the same problem with Ubuntu 13.04 (upgrading from 10.04 LTS).  My mouse and keyboard do not work and I can't log in.  I submitted a bug report, but no one seems to be paying any attention to it because I can't post any debugging files (obviously--the computer is non-functional!)

Any ideas?

---

### Post by mörgæs on 2013-04-30
I recommend a fresh install, plain and simple. Upgrades are basically too risky.

More info in the link in my signature.

---

