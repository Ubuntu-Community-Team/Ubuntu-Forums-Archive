---
title: "A heads up on kernel upgrade 6/20/2008"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by oldsoundguy on 2008-06-20
Did the kernel updates that were waiting on my three Gutsy boxes this morning and all three boxes lost the restricted drivers and had to have the video re-installed completely.

After the reboot had to re-enter my monitor information to get proper resolution and that still did not do it at first.

Uninstalled the restricted drivers (I use Envy, so that was a piece of cake since it is under applications> system tools)
Re-installed the drivers. (again using Envy)
ctrl/alt/backspace.
went to system and re set the resolution(s)

Because I rotate my monitors had to get into xorg 
Terminal: (sudo nano /etc/X11/xorg.conf) and add the
Option  "RandRRotation"  "yes" to the video card configuration. (re-write and save and exit.)
ctrl/alt/backspace
All was well.

Not sure how you would do it if you are using the restricted drivers manager, but supposed that system> administration> restricted drivers manager would do it for you.

Just be forewarned that it COULD happen.

---

### Post by jimv on 2008-06-20
Same thing happened to me.  Kernel 2.6.24-19 killed my nvidia drivers.  Reinstalled them with EnvyNG and all was good again.

---

### Post by Pumalite on 2008-06-20
This is normal. If you do it through enabling the Hardware Drivers in the first place, nothing happens, but if you have installed proprietary drivers through any other means; then you have to reinstall them after each kernel upgrade.

---

### Post by jimv on 2008-06-20
Actually, I've gone from 16 to 17 to 18 and each time the Nvidia drivers were installed (looked like some kind of script ran at the end of the kernel upgrade).  The script failed to run this time from some reason.

---

### Post by bromix on 2008-06-20
Envy's website is very clear about this.  Whenever there is a kernel update, many people experience an X-crash...this time I didn't.   But if you do...from the prompt you can run envy or envyng with with the "-t" argument and reinstall through it's textual interface.  I'm not sure what happened this time that I didn't result in an X crash, but just for good measure, I did rerun envy just to update with the new headers.

---

### Post by upchucky on 2008-06-20
got a link to envy site?

---

### Post by Pumalite on 2008-06-20
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by rico4295 on 2008-06-20
A fortunate one here. All I had to do was re-add my boot info for xp back into menu.lst. wshooo :)

---

### Post by dasunst3r on 2008-06-20
For those of you who were fortunate enough to not have to reinstall your drivers as a result of kernel updates, you should thank DKMS (Dynamic Kernel Module System) for it.  In the update process, the modules that need to be compiled will be compiled for you.

---

### Post by oldsoundguy on 2008-06-20
Just an addendum.  This was the first time drivers and display properties went bye bye on me with an update.  I have been using some form of Linux for quite a few years, but upgraded the machines with new video cards and displays AFTER I  installed 7.10.  Previously I had used the generic built in drivers, so had no knowledge that an update could possibly eat the restricted stuff!!  That is why I posted this thread.  For those that have NOT had the issue before or for noobs to Linux (and thank God there are more of them every day!)

---

### Post by jrusso2 on 2008-06-20
I have been waiting on the update to see how many have problems.

---

### Post by sports fan Matt on 2008-06-20
I havent been home (out of town) but going to wait on updating. Im still on kernel 18 and just waiting till I get home on the behavior

---

### Post by Pumalite on 2008-06-20
pumalite@pumalite-desktop:~$ uname -a
Linux pumalite-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux
pumalite@pumalite-desktop:~$

---

### Post by upchucky on 2008-06-20
My thanks to the ubuntu gods, (the nice people here), Envy got me nvidia up and running again complete with my beryl settings.

I was wondering tho how it managed to aquire "root" privilege without asking me to enter password.

---

### Post by Pumalite on 2008-06-20
sudo gives you root privileges for about 10 min.

---

### Post by Deutscher Alex on 2008-06-21
Ok this sounds incredibly dumb but I literally CAN'T SEE about 3/4 of my screen because of this problem. I know for sure i can enable my driver through System > Administration > Hardware Drivers, but i cannot see past the first grouping called "Device Driver". I know my gfx card is the first thing on the list but I can't see the radio button that i have to click. Can some1 tell me about where it is? >.<
A speedy reply would be very much appreciated.

Edit: I can't find the link to download envy, because I can only see about 5 lines at once, the left half of the screen is on the right & vice versa, and the homepage is lonnngggg. Could some1 tell me where it is?

---

### Post by Deutscher Alex on 2008-06-21
sorry to double post (or at least i think i'm double posting), but i can't see sh**. Envy failed me. Device manager failed me. Any other solutions??!?!?

---

### Post by Deutscher Alex on 2008-06-21
OK after trying and retrying envy & device manager, and posting on forums for AN HOUR & A HALF, I found myself a solution: Run the kernel in recovery mode & do the xserver fix

---

### Post by Flying caveman on 2008-06-21
I had to re-download the broadcomm 43xx firmware on 2 of my computers. plus another two i'm sure will need it again after i re-boot it. 

Not that big of a deal, but I had to get out the crimping tool and put some ends on some cat5.  

Anybody know where the broadcomm 43xx firmware is, if it was previously downloaded?    

No problems with the nvidia drivers though after the update.

---

### Post by Deutscher Alex on 2008-06-21
```
sudo dpkg-reconfigure xserver-xorg -phigh
``` to reconfigure the xorg.conf file (same thing as running xfix in recovery mode)
I can't install my video card's driver anymore without it bugging out. Any suggestions?

---

### Post by oldsoundguy on 2008-06-21
uninstall it first .. then re-install.  Does NOT require a reset (ctrl/alt/backspace) between as when you uninstall (using Envy) it actually removes it and does not hold it for a reboot like Windows does.

But trying to install a restricted driver (to "repair") OVER an existing restricted drive does not work.

---

### Post by punkybouy on 2008-06-21
I had the same problem with a box where I had used Automatix to install the Nvidia drivers.  It has been working fine for two years with Ubuntu upgrades all along the way from Edgy to Gutsy with never any video issues.  Yesterday's patches wiped out the drivers and I resorted to Envy which worked like a charm and thanks to this post which directed me Envy.  I have two other Gutsy boxes which updated with a hitch.  The only difference I could see was that in those two the restricted driver was checked off AND in use and on the oldest box that had issues it was not checked off but was shown to be in use anyway.  Thanks again.

---

### Post by Deutscher Alex on 2008-06-21
> **oldsoundguy said:**
> uninstall it first .. then re-install.  Does NOT require a reset (ctrl/alt/backspace) between as when you uninstall (using Envy) it actually removes it and does not hold it for a reboot like Windows does.

I have tried this multiple times but it isn't working. How can I manually uninstall the driver?

---

### Post by oldsoundguy on 2008-06-21
since I do not KNOW what reaction you will get, you could try doing the reset after the uninstall

once again:  ctrl/alt/backspace

and IF your screen will let you, re-install using Envy when you can.

BUT .. repeating .. I really do not know what issues may come up doing it that way.

---

### Post by Deutscher Alex on 2008-06-21
> **oldsoundguy said:**
> since I do not KNOW what reaction you will get, you could try doing the reset after the uninstall

once again:  ctrl/alt/backspace

and IF your screen will let you, re-install using Envy when you can.

BUT .. repeating .. I really do not know what issues may come up doing it that way.

My screen messes up in a way that I am still able to use envy (tabbing through it partially), but I have tried this multiple times and it's not working.

How do I MANUALLY uninstall the driver, so that I know i'm not just overwriting something

---

