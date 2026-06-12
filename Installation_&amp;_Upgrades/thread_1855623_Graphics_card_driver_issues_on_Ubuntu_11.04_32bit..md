---
title: "Graphics card driver issues on Ubuntu 11.04 32bit."
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by woj2011 on 2011-10-06
Hello,

For the past few days I am trying to install a fresh copy of Ubuntu 11.04 on the older Pentium4 2.4GHz computer. The OS installs with no problem, but when it boots it is having problems bringing up the graphics card. The screen will either constantly flash and eventually the desktop will come up, when it does there are either icons not showing at or they look fuzzy. 

I pressed CTRL+ALT+F1 and was able to get to the terminal. What I am seeing is a lot of errors about graphics card lockup showing. 

[396.324036] Radeon 0000:01:0.0 GPU lockup CP stall for more than 10000msec
[412.552032] Radeon 0000:01:0.0 GPU lockup CP stall for more than 10000msec
[428.796032] Radeon 0000:01:0.0 GPU lockup CP stall for more than 10000msec
[445.036034] Radeon 0000:01:0.0 GPU lockup CP stall for more than 10000msec
[456.760033] Radeon 0000:01:0.0 GPU lockup CP stall for more than 10000msec

Also, I am not able to locate the graphics card configuration files anywhere.

The graphics card I have is ATI Radeon HD 4670 (AGP).

Does anybody has any suggestions how this can be fixed, so the system can boot successfully?

Thank you

---

### Post by collisionystm on 2011-10-06
> **woj2011 said:**
> Hello,

For the past few days I am trying to install a fresh copy of Ubuntu 11.04 on the older Pentium4 2.4GHz computer. The OS installs with no problem, but when it boots it is having problems bringing up the graphics card. The screen will either constantly flash and eventually the desktop will come up, when it does there are either icons not showing at or they look fuzzy. 

I pressed CTRL+ALT+F1 and was able to get to the terminal. What I am seeing is a lot of errors about graphics card lockup showing. 

[396.324036] Radeon 0000:01:0.0 GPU lockup CP stall for more than 10000msec
[412.552032] Radeon 0000:01:0.0 GPU lockup CP stall for more than 10000msec
[428.796032] Radeon 0000:01:0.0 GPU lockup CP stall for more than 10000msec
[445.036034] Radeon 0000:01:0.0 GPU lockup CP stall for more than 10000msec
[456.760033] Radeon 0000:01:0.0 GPU lockup CP stall for more than 10000msec

Also, I am not able to locate the graphics card configuration files anywhere.

The graphics card I have is ATI Radeon HD 4670 (AGP).

Does anybody has any suggestions how this can be fixed, so the system can boot successfully?

Thank you

Yes. Your screen is fuzzy because the screen resolution is probably going to 800x600. This is because Ubuntu does not have drivers for your card! Luckily, however, ATI has drivers to fix this for you!

Download this onto your Ubuntu box

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)


Open a terminal

cd Downloads ( or wherever the file is)

sudo bash

chmod +x ati-driver-installer-11-9-x86.x86_64.run

./ati-driver-installer-11-9-x86.x86_64.run

Once it is installed, read the directions about running the ati config. Once you do that, just reboot!

---

### Post by woj2011 on 2011-10-07
Thanks for the info.

I ran "sudo apt-get install fglrx", which downloaded and installed driver from the repositories. Now the OS works without any problems.

---

