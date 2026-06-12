---
title: "Screen Off-Centered after upgrade"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by Bodizzle on 2007-05-14
My display is shifted about 1/4" to the right after I upgraded from 6.10 to 7.04.  I dual boot and it does not have this shift with my other OS so adjusting the screen each time I boot Ubuntu would get annoying.  I read somewhere else to adjust using xvidtune then to add a Modeline in xorg.conf with the line from xvidtune.  It works as long as I am logged in but goes back to the shift right when I reboot.

---

### Post by heimo on 2007-05-14
> **Bodizzle said:**
> My display is shifted about 1/4" to the right after I upgraded from 6.10 to 7.04.  I dual boot and it does not have this shift with my other OS so adjusting the screen each time I boot Ubuntu would get annoying.  I read somewhere else to adjust using xvidtune then to add a Modeline in xorg.conf with the line from xvidtune.  It works as long as I am logged in but goes back to the shift right when I reboot.

Yeah, I'd guess that you read about it in this thread (which you started):
[http://ubuntuforums.org/showthread.php?t=441139](http://ubuntuforums.org/showthread.php?t=441139)

---

### Post by Bodizzle on 2007-05-14
True, but the hope was that I would get more responses from a post in the installation and upgrades forum that may help out.  I tried everything you said and it goes back to off-centered when I restart.  Hopefully someone else has had the same problem and fixed it so they can shed some light on the issue.

---

### Post by heimo on 2007-05-14
> **Bodizzle said:**
> True, but the hope was that I would get more responses from a post in the installation and upgrades forum that may help out.  I tried everything you said and it goes back to off-centered when I restart.  Hopefully someone else has had the same problem and fixed it so they can shed some light on the issue.

Do a favor for those other people and post your xorg.conf, latest xorg log file and the modeline you get from xvidtune and they may be able to show you how to do it. I'm out.

---

### Post by Bodizzle on 2007-05-14
No need to get defensive.  All I am trying to do is get my screen centered.  If you have any other ideas, please share.  I will post them if that helps.

---

### Post by xbadger on 2007-05-16
I have the same problem here and I see that no one has a solution. When you reboot the screen remains off center. I tried the modeline but with no result. I think in xorg.conf the modeline sequence is bypassed. Any ideas how to resolve it?

---

### Post by Bodizzle on 2007-05-16
So far, I have found nothing.  I have resorted to going into xvidtune each time I boot and adjusting the screen which gets really annoying.  As far as help, I get the same advice to add the modeline which didn't work and when I reposted, the original resonder got all huffy because I dared ask if anyone else was able to resolve the issue.  

I have added the modeline, reconfigured xorg.conf, and everything else they have suggested but it just keeps resetting to the 1/4" shift to the right when I reboot.  Please let me know if you are able to fix this.

---

### Post by ryanclemson on 2007-07-17
Hey fellas, 

I know this is an old post, but if you read the top of your xorg.conf it says:

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

I helped a buddy of mine with a similar problem, and I think this is the command to run. Let me know if it works.

---

### Post by ryanclemson on 2007-07-17
Oops. I don't think that was it. Lemme do some checking and I'll post back with the correct command.

---

### Post by faif on 2007-07-21
Bodizzle, I have exactly same problem as you. I just installed ubuntu 7.04 with dual boot. I did xvidtune and modeline in xorg.conf for my old debian which works fine. But it doesn't work for this ubuntu, did it work for your old ubuntu6.10?

I will investigate that and try to find some solutions.

---

### Post by faif on 2007-07-21
Strange enough, today I upgraded to use new nivida driver to enable desktop effects. Now Modeline suddenly works. I suppose some generic display card drive made modeline doesn't work before.

---

