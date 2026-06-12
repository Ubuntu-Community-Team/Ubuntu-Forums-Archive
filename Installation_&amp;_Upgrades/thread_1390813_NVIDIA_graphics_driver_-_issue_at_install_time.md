---
title: "NVIDIA graphics driver - issue at install time"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by Kim Beech on 2010-01-26
Dear Ubuntu Forum,
I'm a new Ubuntu user (or trying to be :) and this is my first post.  

I have just installed Ubuntu (9.10) and noted that in order to successfully run the trial off the CD I had to test in "safe graphics" mode.  I have an NVIDIA GEforce 6600 GT card - which was discovered by Ubuntu in the first few minutes of the trial and so I activated the recommended driver and continued to test.  

After a successful trial I installed Ubuntu (dual partition Ubuntu / Windows XP), however, it seems the install didn't activate the required driver (as part of the process) and so I'm unable to get into my newly-installed Ubuntu at all.  All I get is a flashing tty screen asking for my username and password - however it's erratic and won't recognise what I type.  

So - I'm stuck in a catch-22 as there doesn't seems to be a safe graphics mode option via the start (GRUB?) menu list.  Any advice very welcome.

Many thanks,
Kim.

---

### Post by tommcd on 2010-01-26
> **Kim Beech said:**
> 
I have just installed Ubuntu (9.10) and noted that in order to successfully run the trial off the CD I had to test in "safe graphics" mode. 
Do you mean the only way you could run the live CD is in safe graphics mode? Is that correct?
> **Kim Beech said:**
> 
 I have an NVIDIA GEforce 6600 GT card - which was discovered by Ubuntu in the first few minutes of the trial and so I activated the recommended driver and continued to test.  
How did you do this from the live CD? Did you go to: system > administration > hardware driver, and enable the nvidia driver? Or something else?
> **Kim Beech said:**
> 
After a successful trial I installed Ubuntu (dual partition Ubuntu / Windows XP), however, it seems the install didn't activate the required driver (as part of the process) and so I'm unable to get into my newly-installed Ubuntu at all.  All I get is a flashing tty screen asking for my username and password - however it's erratic and won't recognise what I type. 
Can you boot to recovery mode from the grub menu? If so, then boot to recovery mode, login, and install the nvidia driver:
```
sudo apt-get install nvidia-glx-185
``` 
Then to make sure the driver is enabled, run:
```
sudo nvidia-xconfig
```
Post any error messages you may get if this fails.
If the nvidia driver installes ok, then try to reboot to the Ubuntu desktop. 
I used to have a nvidia geforce 6600. I never had problems with it in Ubuntu. The nvidia 6600 GT is supported by the nvidia-glx-185 driver:
[http://packages.ubuntu.com/karmic/nvidia-glx-185](http://packages.ubuntu.com/karmic/nvidia-glx-185)

And welcome to the Ubuntu forums!

---

### Post by Handssolow on 2010-01-26
I send you my sympathy. I keep trawling through the Installation & Upgrade Category looking for others who possibly have the same bug as this-

[http://ubuntuforums.org/showthread.php?t=1305459](http://ubuntuforums.org/showthread.php?t=1305459)

Can you boot to a command line? Pressing ESC at boot up should get you to Grub options then choose recovery. Next you'll have to select command line. You then might be able to enter sudo stop gdm and then your password to stop the flashing. You should then be able to enter the instructions given above and hopefully get the Nvidia driver properly working. 

I've also got a Geforce 6600GT video card and I'm unable to run 9.10 live CDs because of a flashing screen. (Incidentally I can run 9.10 from my hard drive with the current recommended Nvidia 185 driver but it wasn't a fresh install). With the flashing screen I get with the live CD it took me ages to correctly enter anything without getting character repeats or deleting stuff I've already got correct.

Edit: Having a wired Ethernet connection is far preferable in situations like this than having to also configure wifi.

---

### Post by tommcd on 2010-01-27
> **Handssolow said:**
> 
I've also got a Geforce 6600GT video card and I'm unable to run 9.10 live CDs because of a flashing screen. (Incidentally I can run 9.10 from my hard drive with the current recommended Nvidia 185 driver but it wasn't a fresh install). With the flashing screen I get with the live CD it took me ages to correctly enter anything without getting character repeats or deleting stuff I've already got correct.

For situations like this you should install Ubuntu with the alternate install CD. This will eliminate any graphical problems during the install.

---

### Post by Kim Beech on 2010-01-27
> **tommcd said:**
> Do you mean the only way you could run the live CD is in safe graphics mode? Is that correct?
 
Hi,
I don't know how to reply to your quotes so I hope you see this: ) Yes, that's correct. Safe mode works - seems to get around the constraints of the lack of NVIDIA xxx driver in the Ubuntu set. However, wouldn't of course be good for a longer term solution.
 
How did you do this from the live CD? Did you go to: system > administration > hardware driver, and enable the nvidia driver? Or something else?
 
The system (in Safe Graphics Mode) picked up the lack of an NVIDIA driver AND also recommended three drivers to activate. It did this by showing a 'driver' icon in the status section at the top right hand corner of the screen. A very intelligent touch, I thought.
 
Can you boot to recovery mode from the grub menu? If so, then boot to recovery mode, login, and install the nvidia driver:
```
sudo apt-get install nvidia-glx-185
``` 
Then to make sure the driver is enabled, run:
```
sudo nvidia-xconfig
```
Post any error messages you may get if this fails.
If the nvidia driver installes ok, then try to reboot to the Ubuntu desktop. 
I used to have a nvidia geforce 6600. I never had problems with it in Ubuntu. The nvidia 6600 GT is supported by the nvidia-glx-185 driver:
[http://packages.ubuntu.com/karmic/nvidia-glx-185](http://packages.ubuntu.com/karmic/nvidia-glx-185)
 
Excellent!! I am very impressed. A simple solution and you were on the money immediately. It worked perfectly and I thank you for a great response to my first-ever Ubuntu forum question. Thanks, "tommcd"!!
 
And welcome to the Ubuntu forums!
Thank you.

---

