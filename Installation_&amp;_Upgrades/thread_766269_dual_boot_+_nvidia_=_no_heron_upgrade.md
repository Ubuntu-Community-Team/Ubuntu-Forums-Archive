---
title: "dual boot + nvidia = no heron upgrade ?"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by harrykh on 2008-04-25
thank god i haven't clicked that button yet, it's fine if gutsy gets hosed but Windows is still my main OS. actually it's fine if either gets hosed as I have partition images of both. i'm confident i can restore windows but my last attempt to screw around a linux partition has been disastrous (resizing partition).

Anybody out there actually able to upgrade a computer with dual os (gutsy 7.10 and windows) and (because it's personally applicable) nvidia graphics card (glx-new)?? I haven't seen one, maybe i missed them.

can i assume that most successful upgrades are from fresh/minimal customized installs or installs with no use of any restricted drivers or what not?

thanks :guitar:

---

### Post by Malfet on 2008-04-25
> **harrykh said:**
> Anybody out there actually able to upgrade a computer with dual os (gutsy 7.10 and windows) and (because it's personally applicable) nvidia graphics card (glx-new)?? 

I did right now, but NVidia card doesn't work and can't be recognized in new Ubuntu 8.04, while in Ubuntu 7.10 it was perfectly fine. Actually, I would like to go back now to Ubuntu 7.10, where everything was working fine and I had no troubles wth hardware or keybourd layouts.

---

### Post by harrykh on 2008-04-25
sorry about that. personally i have tried a fresh install of HH when it was still beta and everything was working fine (video, audio, etc)...then came one particular system update (-16) and everything went south. it was the nvidia drivers(also wifi i think), it broke and no matter how many times i uninstall, reinstall it, it won't recognize the nvidia graphics and always goes back to VESA. also did the nv=nvidia thing, etc, etc...nothing!!

then i went to supposedly more stable 7.10 (at least it's not beta). 

the above was my main reason for not clicking to upgrade gutsy, and now I hear that the upgrade is removing (or something) windows from grub.

maybe couple more weeks of tweaking was in order especially for the desktop version. right now upgrading is something to be weary about.

---

### Post by Dale61 on 2008-04-25
I upgraded from Dapper to Heron, on a dual boot system, running an nVidia FX5200.

I just clicked the upgrade button in update manager, and 100 hours later, I was running Heron.

---

### Post by Malfet on 2008-04-25
> **Dale61 said:**
> I upgraded from Dapper to Heron, on a dual boot system, running an nVidia FX5200.
I just clicked the upgrade button in update manager, and 100 hours later, I was running Heron.

Really? And you card is working normally?
I'm also using GeForce FX Go5200, but 8.04 does not recognize it :((( For 7.10 I had no problems, but not here. Did you use special driver or just run Drivers manager?

---

### Post by Dale61 on 2008-04-25
In Hardware Drivers (System - Administration - Hardware Drivers) I have nvidia-new enabled, but it indicates that it's not in use (?).

I searched these developmental forums for threads that related to any minor problems I was having, and found something about the replacement for the old *sudo dpkg-reconfigure xserver-xorg* command, which got my monitor running at 1440 x 900.

Don't trust me, but I think I typed *sudo envyng -t* in a terminal, and all was sweet.  However, I was still able to use my pc immediately after the first re-boot after the upgrade, so I assume that nvidia cards are recognised, but need to be manually fine tuned.

---

### Post by Smudger on 2008-04-25
I upgraded to 8.4 using a NV44A [GeForce 6200] graphics card, and it rendered my monitor completely unusable. All I can see is a message saying **"Out Of Range"**, and then the I hear the sound when the log in screen comes up, but I am unable to see anything, most annoying.

---

### Post by Malfet on 2008-04-25
> **Dale61 said:**
> Don't trust me, but I think I typed *sudo envyng -t* in a terminal, and all was sweet.

When I selected my card in Restricred driver manager I always got a message after system restart that system can not recognize my card and monitor (in Ubuntu 7.10 I had no problems with it) and screwed up keyboard layouts as well.
Now, I have removed old NVidia drivers and after that restricted driver manager did not see NVidia card at all. Then I install Envy, it has recognized my card properly and install dome drivers but after restart I got the same old message: Your graphic card and monitor can not be recognized and screwed up keyboard layouts in addition... :((
That's really stupid when NEW version of OS has a worse hardware support then an old one.

---

### Post by abraxas334 on 2008-04-25
I upgraded fine from 7.10 to 8.04 with a dual boot xp. Got a GeForce 7300Gs graphics card and run 2 monitors with it. Only thing that got a bit messed up was my fake Mac os theme after the upgrade but apart from that everyting works just fine :).

---

### Post by harrykh on 2008-04-25
someone actually got off relatively unscathed. but still looks like the odds are againts me :p I'll keep 7.10 for a while coz i'm still enjoying compiz, etc. 

The only thing thats better in HH when I was trying it out was that the power management for my laptop was more accurate (detected my maximum brightness, lowered the brightness during afk, etc). Not sure what else was so different from 7.10...Firefox beta 3 kinda messed up my most used addons so I had to install swiftweasel. :popcorn:

---

