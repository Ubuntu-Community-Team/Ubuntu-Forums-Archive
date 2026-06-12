---
title: "Installed NVIDIA drivers now no desktop."
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by freshmeat20 on 2011-01-10
I ran the 64-bit .run for the latest nvidia drivers. ha the correct kernels and everything but when I boot I see the two icons i have (computer and terminal) and a movable mouse but no task bar. It plays the startup sound but cant open anything. Any ideas? bump from previous post.

---

### Post by mystika1 on 2011-01-10
Hi,
I don't know if this will fix your problem but I discovered it today and it helped me end my video driver installation problems in minutes. 
In konsole 
Sudo
then run:
cd /usr/local/bin && wget -Nc smxi.org/sgfxi && chmod +x sgfxi && sgfxi

Get out of konsole and ctrl+alt+f1
Run
sudo sgfxi

Follow the prompts until it is done!

Hope this works for you like it did for me. 
More info on this nice little problem solver can be found here [http://smxi.org/docs/sgfxi-manual.htm#xorg-drivers](http://smxi.org/docs/sgfxi-manual.htm#xorg-drivers).


Penny

---

