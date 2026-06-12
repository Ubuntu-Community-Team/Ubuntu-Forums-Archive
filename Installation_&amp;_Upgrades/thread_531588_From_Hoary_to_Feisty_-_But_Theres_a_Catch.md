---
title: "From Hoary to Feisty - But Theres a Catch"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by gordynash on 2007-08-21
Hello All, I have recently jumped into the ubuntu world with some linux background (not exstensive).  My hardware set-up is as follows:

Abit AN8 Motherboard
AMD 64 3200+ processor
ATI X700 pro video card

It took me a long time to get ubuntu running because it does not recognize my video card.  I wasn't able to install v7.04 because x-windows will not start.  Even with a text based install it would go to black on the first reboot.  I went all the way back to v5.04 in order to get it to work.  I had to do a text install as well of v5.04 (Hoary) and then compile the X700 pro driver from the command line, and then restarted X-windows to get it to work.

Now I want to upgrade/update to 7.04, but I cannot do a brand new install or it will erase the driver that is currently working and I will be back to square 1.  How can I update my OS to the newest without erasing the video settings?  I read some stuff about incremental updating from one version to the next.  Is that my best bet?  Thanks for your help.

---

### Post by Pumalite on 2007-08-21
Incremental upgrade is your ONLY way. As for your ATI driver, you'll probably have to compile it again. I might be wrong and the answer could be found here:
[http://ubuntuforums.org/showthread.php?t=221320&highlight=ATI+X700+pro](http://ubuntuforums.org/showthread.php?t=221320&highlight=ATI+X700+pro)

---

### Post by s3a on 2007-08-21
Wouldn't it work if you upgrade from your current Ubuntu to the next and the next and the next until you reach 7.04? Sounds lengthy but should work...I am not sure, so ask someone else before attempting.

---

