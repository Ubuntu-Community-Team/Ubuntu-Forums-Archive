---
title: "startx 'X' died"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by Xgates on 2005-04-11
After installing Ubuntu for 2 days it ran just fine, then I wanted to clean out the /tmp directory and clean up some of the temp stuff laying around as well, old logs, etc.. In /tmp I cleaned it out, and in /var/log I removed old .0 logs, then I installed gxine, and when I rebooted my box, and tried to startx it came to the Nvidia screen and died, then in the /var/log/Xorg log it said something about EDID failure for CRT:0, now how does cleaning out the box and installing gxine kill X is what I'd like to know?

I can't figure this out to get X going again, and am afraid I have to reinstall the box. I ran xorgconfig, and dpkg-reconfigure xserver-xorg over and neither one helped, any ideas here as to what happened here?

Thanks

---

### Post by alastair on 2005-04-11
I've been using Linux for a long time and have never been in a situation that meant a reinstall. Really. I'm sure it could happen but it's hard. 

So - having tried to "startx", post the Xorg.0.log and Xorg.conf. Perhaps someone can spot a problem.

---

### Post by Xgates on 2005-04-11
xorg.conf is configured correct, the box ran fine for 2 days as I mentioned, and as SOON as I cleaned out the /tmp and removed some old logs and installed gxine it died. Xorg log says:

EDID failure on CRT:0

I mean the exact second I cleaned out the /tmp and some old logs in /var/log and installed gxine it died, what I'm trying to figure if Ubuntun needed something in /tmp but from my past experience in Linux you can clean it out, but then you'd better reboot which I did.

Actually when I get back to my box I'm going to check the perms on /tmp since I removed it and did mkdir on it, I just remove it when there is alot in there, simpler then removing everything in it one by one, maybe the perms are off,  but I don't see how since I created it as root

Oh by the way when I logout before from X back into console, I'm not running GDM, I see this mentioned in console:

Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o": No symbols found

What is this all about?

---

### Post by nad on 2005-04-12
The X server puts a lock file in /tmp. My /tmp has all permissions set plus sticky. ' chmod 1777 /tmp ' should do it.

As far as:

Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o": No symbols found

I'm getting this also. Anybody?

Dan M

---

### Post by graabein on 2005-04-27
I get the same error as you do nad, with Ubuntu's nvidia-glx etc...

---

