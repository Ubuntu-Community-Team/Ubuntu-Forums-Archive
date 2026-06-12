---
title: "OFTB disaster in getting Ubuntu to install/run on Compaq 615"
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by DavidLR on 2010-07-13
HI,
I'm an absolute newbie to linux/Debian/Ubuntu. 
 
Problem: Ubuntu is loaded successfully but does not run - I just get a blank screen.
 
The machine specs:
HP Compaq 615
Processor AMD Athlon X2 DualCore QL-64
Processor speed 2100 MHz
ROM date 07/17/2009
ROM Revision 68GVV Ver F.04
Video Bios Revision : ATI 05/07/09
 
History:
I downloaded Ubuntu, burnt a CD and it runs fine on my Saraha machine and it ran fine on the HO Compaq as well - from the CD. So I selected install. At the end of install when I had to reboot, the screen was filled with error messages I/O error on sector ...... pages of the messages.
 
Then downloaded the notebook version and again both laptops ran fine from CD. Installed Ubuntu (deleting everything else) and exactly the same problem.
 
After reading this forum posts I tried pressing F6 and got a screen with options. Selected them all, installed again - but same blank screen problem.
 
Read this forum again - and found lots of posts with the same problem - on the same machine, but it appears no solutions.
 
I'm at the point of walking away, but really would like to give open source a realistic try. I'm afraid to install Ubunto on any other machine as we may end up with nothing working.
 
Thank you for reading this, and moral and/or technical help will be most appreciated.

---

### Post by Rubi1200 on 2010-07-13
What graphics card do you have?

There have been a lot of issues with graphics chipsets.

Also, look here for some possible workarounds for booting a LiveCD (if that is also an issue).

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

You can also post the output of

```
lspci | grep VGA
```

from the LiveCD

---

