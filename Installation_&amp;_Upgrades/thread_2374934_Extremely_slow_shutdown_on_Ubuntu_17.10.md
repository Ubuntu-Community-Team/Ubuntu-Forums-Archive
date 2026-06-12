---
title: "Extremely slow shutdown on Ubuntu 17.10"
date: 2017-10-20
forum: Installation &amp; Upgrades
---

### Post by silverslimer on 2017-10-20
After installing Ubuntu 17.10, the shutdown process takes about 10 minutes to complete. It seems to be unable to stop wpa_supplicant properly. Has anyone else experienced this?

---

### Post by slickymaster on 2017-10-20
Thread moved to **Installation & Upgrades** for a better fit

---

### Post by pparo on 2017-10-21
Hi,
same problem as you, check here -> [https://www.reddit.com/r/Ubuntu/comments/77opsd/ubuntu_1710_slow_shutdown/](https://www.reddit.com/r/Ubuntu/comments/77opsd/ubuntu_1710_slow_shutdown/) 
now for me shutdown's time is normal and everything is OK.
if you make a mess whit your PC i don't take any responsibility, I'm the newbiest person in the world:)

---

### Post by silverslimer on 2017-10-22
I tried a more recent version and ended up with a boot loop so I went back to the original. 4.13.8 will be fine by me if it works. I'll try and let you all know.

---

### Post by silverslimer on 2017-10-22
I just want to confirm that using 4.13.8 works flawlessly.

---

### Post by colmeweb on 2017-11-12
I just updated using 4.13.12, startup is still a little slower than 17.04, but shutdown is fine. 
The kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) worked fine.

---

### Post by nipunwaas1 on 2017-11-13
I fixed this ...follow this.
First you have to log into your account in ubuntu on Xorg (just click the wheel next to the sign in button in the log screen)
Next press alt+f2 and enter the command gksu nautilus and hit enter..after that u will get a pop up window asking for password and enter it.
Next you will get the owner permission to your ubuntu and you will get file window..next go to the location etc/systemd/system.conf and click the file after that change the value in DefaultTimeoutStopSec to 4s..then save the file and restart your computer..
Now it should work..

---

### Post by markackerman8@gmail.com on 2017-11-15
Thanks, nipunwaas1 

"go to the location etc/systemd/system.conf and click the file after that change the value in DefaultTimeoutStopSec to 4s"

For Newbies - Easy-Peasy and Thanks Worked For Me!

In Terminal
> sudo gedit /etc/systemd/system.conf
Find Ridiculous Default of 90 seconds and change to 4, 
note the '#' must be removed
> #DefaultTimeoutStopSec=90s

change to
> DefaultTimeoutStopSec=4s
Save / Exit /  Reboot

Esay Peasy Thanks, Mark :)

---

### Post by Scott Deagan on 2018-02-06
> **nipunwaas1 said:**
> .../etc/systemd/system.conf and change the value DefaultTimeoutStopSec to 4s..then save the file and restart your computer...

Thank you! Every now and then (about every 3rd or 4th shutdown) my Kubuntu 17.10 would hang for a couple of minutes. After changing DefaultTimeoutStopSec to 4s (4 seconds), I haven't had a single slow shutdown. It has only been 24 hours since I applied this "fix" ("workaround"?), but so far, so good.

---

