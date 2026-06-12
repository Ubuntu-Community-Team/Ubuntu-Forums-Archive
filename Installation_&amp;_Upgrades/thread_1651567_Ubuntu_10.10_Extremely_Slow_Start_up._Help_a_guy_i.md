---
title: "Ubuntu 10.10 Extremely Slow Start up. Help a guy in Sudan."
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by Jim_Hope on 2010-12-23
Dear All,

Since I upgraded to Ubuntu 10.10, my computer spends 5+ minutes starting up. Of that, two minutes or so are spent getting to log-in, which is longer than Ubuntu 10.04 took. After I log-in, it takes up to 5 minutes, just to load.

I am not entirely sure what is causing this. Almost every time I start up, all the panel applets crash (e.g. "The panel encountered a problem while loading "OAFIID:GNOME_ShowDesktopApplet"). 

The panels that reliably fail to load are: the clock, indicator applet, indicator applet session, *and* fast_user_switch, though the latter is not an applet I have added to the panel.

Deleting and reloading the applets, changing their location etc. does not change the problem. 

I know this problem has been much commented on in the forums. I have tried all the following solutions:

-- Resizing the panel
--sudo /etc/init.d/gdm stop 
sudo aptitude reinstall gnome-applets
-- sudo apt-get install indicator-applet-session
(its already installed)
-- reinstalling: gnome-panel/gnome-applets/gnome


Does anyone have any other suggestions? Any help would be gratefully appreciated.

cheers,

Jim

---

### Post by Jim_Hope on 2010-12-31
I have made a pretty thorough survey of ubuntuforums.org, and tried all the solutions suggested, and I can't make any headway with this problem. Anyone have any ideas?

---

### Post by banago on 2011-02-16
I have EXACTLY the same problem! Were you able to solve it? What was causing it? Thanks!

---

### Post by mörgæs on 2011-02-16
With so many errors it is not worthwhile to try to rescue the system. Rather go for a clean install:

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by banago on 2011-02-16
I got this problems after the clean install - just fomated the whole hard dirve and I get this. What shall I do :)

---

### Post by mörgæs on 2011-02-16
Please begin with a thorough description of hard- and software and all the steps you have done to diagnose what is going on.

---

### Post by banago on 2011-02-16
Hi mörgæs,

I made a fresh thread for my case - please read here: [http://ubuntuforums.org/showthread.php?t=1689204](http://ubuntuforums.org/showthread.php?t=1689204)

Thank you very much!

---

### Post by Jim_Hope on 2011-02-16
No banago I was not able to solve the problem.

[mörgæs]("http://ubuntuforums.org/member.php?u=939075"), my problem is as follows.

I run an X61 tablet, since upgrading to Ubuntu 10.10, everything works fine, except...

When logging in. (a) it takes upwards of five minutes from the login to get to the desktop. (b) During this time, a variety of the applets fail. They do not fail all the time, perhaps 70% of the time, and display the message:

"The panel encountered a problem while loading "OAFIID:GNOME_ShowDesktopApplet..."

I have found the relevant error in .xsessions:

** (gnome-panel:2842): WARNING **: panel-applet-frame.c:1310: failed to get Bonobo/Control interface on applet OAFIID:GNOME_IndicatorApplet:
Unknown CORBA exception id: 'IDLmg.org/CORBA/COMM_FAILURE:1.0'

This is repeated for each applet failure. 

I have searched the forums, and the internet, and have not found a solution that works. I have tried all the solutions mentioned in my first post, and more besides. Any assistance would be gratefully appreciated.

regards,

Jim

---

### Post by thefinalfrontier1701 on 2011-02-16
I'd go back to 10.04. I tried 10.10 on my desktop computer and it screwed it up. My laptop is running it just fine. (There are a few issues here and there.) 10.04 is much more stable than 10.10.

---

### Post by banago on 2011-02-16
I thinks the same.

---

### Post by Jim_Hope on 2011-02-16
Sadly changing back is just not an option at the moment. (Irregular access to electricity, no HDs onto which I can transfer all my files etc.). So I am stuck trying to fix Ubuntu 10.10.

---

### Post by mörgæs on 2011-02-16
If you have space on the hard drive, you could try installing 10.04 next to 10.10.

10.04.2 is expected tomorrow, so aim for this one.

---

### Post by Jim_Hope on 2011-02-17
I am afraid I am stuck with trying to solve the problems with 10.10. I have no space on this hard drive. I need to move stuff off the computer, but that is going to have to wait until I get to somewhere which sells HDs. So September.

---

