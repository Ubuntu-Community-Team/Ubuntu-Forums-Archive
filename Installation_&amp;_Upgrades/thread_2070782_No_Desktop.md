---
title: "No Desktop"
date: 2012-10-13
forum: Installation &amp; Upgrades
---

### Post by TimB48 on 2012-10-13
I have just upgraded from 11.10 to 12.04.1, following the upgrade I can log on but following that no top or side tool bars are visible.
I did a clean install (with Format) but the result was the same. I can right click on the desktop and look at settings, I can also shell out to a terminal.
Other posts I have read suggest this may be a graphics driver issue ( card is Nvidia 9600GT). Tried updating the driver but with negative result.
There are 3 other operating systems on this PC all of which function fine. My previous incarnation of Ubuntu also ran without apparent problems.
Can anyone shed anly light on this problem.
12.04 runs ok directly from live cd.

---

### Post by Bashing-om on 2012-10-13
TimB48; Hi ! Welcome to the forum.

Maybe a graphics card situation, maybe just that the GUI is not loading.
what results from the terminal command:
```
sudo service lightdm start
```warm regards <==BDQ

---

### Post by TimB48 on 2012-10-15
Result for running 'sudo service lightdm start' was the following.
 
Start: Job is already running: lightdm
 
Forgot to mention in my original post that the top and side bars appear briefly during startup and dissappear leaving me with just the desktop background with no visible icons.
 
 
Regards,
 
 
TimB48

---

### Post by Bashing-om on 2012-10-15
looking like to me the desktop manager might have problems, But lets see if it is graphics driver related:

When booting hold the shift key after the bios screen clears -> grub menu
choose to boot with the "recovery mode" kernel//

do you now have a desk top ?
[INDENT]regards <==BDQ

[/INDENT]

---

### Post by TimB48 on 2012-10-16
Initial attempt to enter recovery mode failed apparently linked to the nvidia graphics. The following lines were the last few before the recovery boot stopped.
 
[4.985757] nvidia:module license 'NVIDIA' taints kernel
[4.985804] Disabling lock debugging due to kernel taint
[5.300064] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level,low)-> IRQ 16
[5.300127] vggarb: device changed decodes: PCI : 000:01:00.0, old decodes = io+mem, decodes = none:owns = io+mem
[5.300371] NVRM : loading NVIDIA UNIX X86 kernel module 295.49 Mon Apr 30 23:30:07 PDT 2012
 
As a ubuntu novice the above lines mean very little to me but suggest that there is some sort of problem with the graphics.
 
A second attempt to enter recovery mode got me to the recovery menu but I was able to do very little from there.
 
There is a newer Nvidia driver available (not the 295.47 listed above) which I have downloaded but am unable to install it.
 
Regards,
 
TimB48

---

### Post by PowerBarry43 on 2012-10-16
This may be a silly suggestion but have you tried running

```
startx
```
you could also try reinstalling unity by running

```
sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop
```

hope this helps!

Barry

---

### Post by TimB48 on 2012-10-17
Running 'startx' only produced the following messages.
Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again
 
 
ddxSigGiveUp: closing log
X10: fatal 10 error 11 (resource temporarily unavailable) on X server ":0"
after 7 requests (7 known processed) with 0 events remaining
 
 
Removing Ubuntu desktop and installing it had no apparent effect.
 
Any further ideas anyone?
 
Regards,
 
TimB48

---

### Post by jerrrys on 2012-10-17
Could it be nomodeset?

[http://ubuntuforums.org/showthread.php?t=2056136](http://ubuntuforums.org/showthread.php?t=2056136)

---

### Post by TimB48 on 2012-10-18
I have successfully reinstalled 12.04 using the 'nomodeset' option mentioned in your link.
The desktop appears normal now but the mouse function is peculiar in that the pointer dissapears when you move it over an icon. I have not updated the nvidia driver because I am not able to access the alternative drivers icon, clicking on it has no effect.
I tried updating the nvidia driver from terminal but all that did was trash the install so it wouldnt run at all resulting in another re-install.
So apparently curing one problem creates another. The original problem is obviously caused by the nvidia drivers but I havew not as yet achieved a full result.
 
Anymore suggestions anyone?
 
Regards,
 
 
TimB48

---

### Post by jerrrys on 2012-10-18
You say that you have reinstalled, have you updated?

sudo apt-get update && sudo apt-get upgrade

---

### Post by TimB48 on 2012-10-20
I have reinstalled and everything appeared to be ok apart from the problems mentioned in my last reply.
I then updated and ended up back to square one with no desktop bars or icons. Unfortunately I did not observe which updates were applied, update just said there were 135 to install. I presume at least one of them was graphics related and I presume there is a log somewhere of what was updated.
When I was able to access the additional drivers there was a beta driver from nvidia which I tried activating but nothing useful happened.
Is there any further information I could provide which would assist anyone in finding a workeable solution to this problem.
It is very frustrating because all previous incarnations of ubuntu have worked 'straight out of the box' as it were but 12.04 seems to be a whole different ball game.
 
Regards,
 
TimB48

---

### Post by TimB48 on 2012-10-25
Still looking for an answer for this problem, looks like my posts have not been viewed for several days.
Anyone out there who can help?
 
TimB48

---

### Post by phoenix90005 on 2013-03-26
for the code : STARTX 
gave me the following :
X: user not authorized to run the X server, aborting.
xinit: giving up
xinit: unable to connect  to X server: connection refused
xinit: server error

still can't return my desktop as it was; what i have is the wallpaper aznd thank GOD that managed to firefox via TERMINAL to look up for some solutions. anyone?

---

### Post by steeldriver on 2013-03-26
Does the desktop work if you log in as guest (or create another user and login as that)? This would help understand whether it is a basic graphics config problem, or just something in the session of your current user.

If it's only a problem with the current user account, then resetting unity may help :- 

[http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html](http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html)

---

### Post by Bashing-om on 2013-03-26
+1
[INDENT=3]

awaiting results

[/INDENT]

---

