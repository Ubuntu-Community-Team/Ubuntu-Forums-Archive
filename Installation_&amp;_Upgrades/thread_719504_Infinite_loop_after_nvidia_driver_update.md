---
title: "Infinite loop after nvidia driver update"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by sonnyg on 2008-03-09
Greetings,

I think I've nearly tried every suggestion  I've found on google and on these forums on how to install the latest nvidia drivers (restricted and even the driver from nvidia.com).  I want to install the proprietary one since I understand that the default one does not support the nice eye candy that can be used on the UI.  

First thing I did was enable the  Restricted Nvidia driver, but after the required restart, it kept going in a infinite loop that would restart the notebook at the point where it should bring up the login screen.

So I went into recovery mode and entered the command 

```
sudo dpkg -reconfigure -phigh xserver-xorg
```

This allowed me to log in to my account, but in low-graphics settings.  I decided to try and disable the  restricted driver and after restarting I was able to get back the default video settings that came on installation.  But I still could not choose the option to run the "extra" visual effects.

I tried installing the latest Linux drivers from the repo but it said that I already had the latest package installed.  

So I installed Envy and let it install nvidia drivers automatically.  After the necessary restart, i was back to the infinite loop:(

I made a big mistake of running 
```
sudo dpkg -reconfigure -phigh xserver-xorg
``` again. 

 I think I should have isntead ran envy again in recover mode to uninstall the driver.  Now I'm stuck in low-res mode but don't know what to do this time.:confused:

I've been at this for about 3 hours now and its starting to get frustrating.  Installing ubuntu on my desktop was a lot easier.  I did have issues with the video driver as well but it was because I had two screens connected to my vid card...  And that was easily resolved.

For my laptop (Asus F8sv-b1), I installed Ubuntu Gutsy, 64bit version.  The notebook has:
T7700 Core Duo Processor (Santa Rosa)
Nvidia GeForce 6800m gt video card

It's already 4 in the morning here so I probably did not mention all steps taken to get to where i'm at now Im pretty tired now.  I'm pretty much brain dead trying to figure out what's been happening :(

I dont know what direction to take now.  If I can't get this to work, probably just gonna keep laptop strictly vista (ugh) and have eye candy fun on my desktop.  Although aside from eye candy, I would also like to try and do some software development in a linux environment as I've only been doing it on windows.

Any help or suggestion to the right direction will be greatly appreciated.  Thank you.

Edit:  Yay its my first post!  Finally have a reason to post =D

---

### Post by taurus on 2008-03-09
I have a XFX GeForce 6800XT on my machine at home and didn't have any problem running nvidia driver from the System -> Administration -> Restricted Drivers Manager.

Not sure why it gives you that infinite GUI login screen.

---

### Post by oddin85 on 2008-05-02
```
sudo dpkg -reconfigure -phigh xserver-xorg
```

should be

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

save ppl the google search ;-)

---

