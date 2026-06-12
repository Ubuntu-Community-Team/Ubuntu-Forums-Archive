---
title: "Installed Gutsy, Rebooted, &amp; Monitor Goes To Sleep"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by ChronoSphere on 2007-11-18
I installed from the alternate CD. Upon reboot, I see the grub menu, the splash screen with the orange progress bar, then the monitor enters standby mode.

I blindly type my name/pw and can hear the successful login sound even though the monitor stays asleep. From here, I type CTRL-ALT-F4, login and do a "sudo reboot" so I can get out of Ubuntu.

I added these kernel flags: nosplash noapic. The monitor doesn't fall asleep but it's all scrambled even when I switch to a text terminal. The video card is an nvidia 7300GT. What can I try next?

:KS **Solution: I read about this in another thread and it worked! I simply installed a cheap vga-to-dvi plug/adapter between my card and the monitor and everything works as it should. Ubuntu is great!**

---

### Post by gsiliceo on 2007-11-18
Try starting in recovery mode and
dpkg-reconfigure xserver-xorg

When prompted disable all the resolutions your screen doesnt support. And choose nv as your driver, once in ubuntu install the restricted drivers.

---

### Post by ChronoSphere on 2007-11-19
OK, I did that and answered all the questions. It wrote out a new xorg.conf, which was almost identical to the original. Then, startx still produces scrambled and unusable video. Perhaps I need to manually adjust the horiz and vert range? My monitor didn't come with those specs, though. I had 7.04 installed and working fine with my previous ATI card.

---

### Post by gsiliceo on 2007-11-19
But does it boot as it should? or you have to do that everytime?

---

### Post by ChronoSphere on 2007-11-19
No, it doesn't start the GUI properly. And CTRL-ALT-BS doesn't drop me down to a text terminal -- the video is still unreadable. I found the correct H and V ranges for my CRT online and will try those values next.

---

### Post by ChronoSphere on 2007-11-19
The problem is still there, even with my monitor's corrected H and V frequencies. Now I'm stumped. Could the login screen be causing this? The "nv" driver? Any suggestions are appreciated.

---

### Post by gsiliceo on 2007-11-19
i think is the resolution when doing the dpkg-reconfigure xserver-xorg in the resolutions step make sure you only keep the lowest possible like 1024x768, you can change this later.
And you dont happen to have 2 graphic cards dont you? maybe one integrated or 2 video output plugs

---

### Post by ChronoSphere on 2007-11-19
I'll try the lower resolution. I have just one card installed and no integrated video. But my card has a dvi plug also.

---

### Post by TJ1234 on 2007-11-19
I had the exact same problem as you. I've managed to get back onto my desktop after using the dpkg-reconfigure xserver-xorg. However, my resolution is stuck at 600X800 and I can't change it. When I start Ubuntu it tells me I'm running in low graphics mode and gives me some screens where I can reconfigure it but it doesn't seem to work. Any ideas why?

---

### Post by ChronoSphere on 2007-11-19
Well at least you can see what you're doing. Perhaps you can try to add the higher resolutions when you use dpkg-reconfigure xserver-xorg.

---

### Post by TJ1234 on 2007-11-19
Yeah, I figured out it was loading the screens and graphics program under system -> administration. I've managed to get Ubuntu to load again with a higher resolution. However FireFox seems to be stuck on a low resolution. I have no idea why.

---

### Post by gsiliceo on 2007-11-19
I think that's compiz fault, try installing the compizconfig-settings-manager and you can find it in system>preferences, the plug in i think is causing the problem is windows resize or something like that.

---

### Post by TJ1234 on 2007-11-19
Hmmm.. I can't find the windows resize option but I dug around the app. and found something similar. But it didn't work.

---

### Post by gsiliceo on 2007-11-20
Both you guys installed the restricted drivers after sucessfully booting ubuntu with graphics? didnt you?

---

### Post by ChronoSphere on 2007-11-21
I solved my problem, see 1st post.

---

