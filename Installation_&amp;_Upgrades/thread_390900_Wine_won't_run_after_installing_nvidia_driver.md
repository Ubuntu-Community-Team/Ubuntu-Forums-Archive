---
title: "Wine won't run after installing nvidia driver"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by Straumoy on 2007-03-22
Hello all,

after a little back and forth I managed to get my nvidia Geforce 4200 up and running, so now I don't get a lagg from another world whenever I want to go into WoW. However, I've been trying to install Guild Wars using the same method I used on WoW (copy CD content to folder on harddrive, run Wine installer.exe etc, full details [http://www.ubuntuforums.org/showthread.php?t=312482&highlight=world+of+warcraft]("http://www.ubuntuforums.org/showthread.php?t=312482&highlight=world+of+warcraft"))

At any rate, whenever I type in "wine Installer.exe" command, I get 

```
wine: could not load L"c:\\windows\\system32\\installer.exe": Module not found
```

I can't think of anything else that could have messed up with it besides the nvidia driver. When I installed the nvidia driver the first time, I screwed up, since after the reboot I was stuck with a black screen and white text only. At any rate, I managed to fix it through a "How-to" guide using the ```
sudo dpkg-reconfigure xserver-xorg
``` command and just ran through with the defaults.

So... I'd like to continue to use Wine, though not at the expence of my video card driver. Can it be done? If so how? If not, what are my options?

---

