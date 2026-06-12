---
title: "[SOLVED] Authentication Failed at Sign in"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Don Cox on 2007-10-19
Version upgrade from 7.4 to 7.10 was performed 18th October using Upgrade Manager. Gutsy Gibbon worked well until a cleanup was done by running  sudo apt-get autoclean and completely removing 36 'Not installed (residual config)' packages via Synaptic Package Manager. These packages are supposedly left-overs from programs that have been uninstalled. Certainly one of them was 'Keyring' which may be significant.

Since then it has been impossible to login; 'AUTHENTICATION FAILED' is displayed, 3 dots like an ellipsis appear at the left end of the Username box and the system freezes. Escape is possible only by powering down the computer (HP Pavilion Zd8255ea, dual boot with XP).

Although I have played with both a console and recovery mode I do not really know what I am doing , and am in dire need of advice.

Is the situation recoverable and if so how? Or would it be best to uninstall 7.10 and start over again? Advice on how an uninstallation could be performed in the absence of the ability to login to Ubuntu 7.10 would be much appreciated. Thank you.

---

### Post by Don Cox on 2007-10-22
How should I have phrased this question to improve the chances of receiving a reply?

Don Cox

---

### Post by fiatguy85 on 2007-10-22
I'm having the same problem.  It occured for me when I cut autologin off.  So far I fixed it once by going into recovery mode, doing ```
dpkg-reconfigure gdm
```,  editing ```
/etc/gdm/gdm.conf
``` specifying autologin again and the username once again, then reloading gdm with ```
invoke-rc.d gdm reload
```.  It worked with autologin once again, but I changed it back to standard, and can no longer fix it in this manner.

---

### Post by fiatguy85 on 2007-10-22
```
gedit /etc/pam.d/gdm
``` remove or comment the line ```
@include common-pamkeyring
``` if it is there.  This solved it for me.

---

### Post by Don Cox on 2007-10-23
I've given up on 7.10 for the time being and reverted to 7.4 using backups and Acronis True Image 9.0. It would appear that completely removing all ' Not installed (residual config)' packages may not always be entirely safe, depite its many enthusiasts.

The experience has quite put me off ever trying again to version upgrade using Update Manager. A fresh install looks a much better proposition.

---

### Post by fiatguy85 on 2007-10-23
Sorry to hear that.  For what it's worth, I had 2 computers which transitioned very smoothly from 7.04 to 7.10 with the Update Manager, and had no trouble when removing the residual packages.

---

### Post by Don Cox on 2007-10-24
[http://ubuntuforums.org/showthread.php?t=582220&highlight=HP+Pavilion](http://ubuntuforums.org/showthread.php?t=582220&highlight=HP+Pavilion)

---

### Post by Maarten78 on 2007-10-25
Hello,

I'm new to this forum, but I still want to share mine solution.
I had the same problem with Authentication when I updated from 7.04 to 7.10.

But some time ago, I had reset mine keyring and added the [COLOR="Navy"]@include common-keyring[/COLOR] to the /etc/pam.d/gdm file. 

When I read the upper posts, I tried to boot in recovery mode, I deleted the line above and it worked for me!!

Maybe this helps other people..!!!! :lolflag:

Greetz,
Maarten.

---

### Post by Jasman on 2007-11-13
This does work. The only problem is that it defeats the bypass of the keyring manager for networking. It seems that Gutsy allows you do bypass that with a checkbox, but not if you keep your wireless in roaming mode. So I guess for right now there's no fix for bypassing the keyring manager prompt, since trying to do it with pam-keyring results in this gdm login error. Unless someone else has a different solution for that...

---

### Post by dropvision on 2007-11-13
Greetings all, I am a Sabayon Linux user that came across this thread while attempting to solve an identical issue (using GDM.) This actually results from upgrading PAM. I solved the issue on my machine by re-installing packages that depend on PAM, including GDM among many others.

Perhaps this may offer some assistance to anyone that encounters this issue down the road.

If it doesn't, I apologize. :)

Good luck.

---

### Post by ardyn on 2008-01-04
> **fiatguy85 said:**
> ```
gedit /etc/pam.d/gdm
``` remove or comment the line ```
@include common-pamkeyring
``` if it is there.  This solved it for me.


I could kiss you. I spent about an hour trying to fix this in the GDM settings.

Thank you!

---

### Post by vldo on 2008-04-25
thanks...i forgot that i changed that:)

---

### Post by malathion on 2008-05-05
> **fiatguy85 said:**
> ```
gedit /etc/pam.d/gdm
``` remove or comment the line ```
@include common-pamkeyring
``` if it is there.  This solved it for me.

I had this problem too, and this fixed it. Thank you!

---

### Post by namdung on 2008-05-22
Had same issue. Resolved after following the instructions given Thanks!!!

---

