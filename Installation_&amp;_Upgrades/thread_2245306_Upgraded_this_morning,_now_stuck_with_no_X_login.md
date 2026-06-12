---
title: "Upgraded this morning, now stuck with no X login"
date: 2014-09-22
forum: Installation &amp; Upgrades
---

### Post by memilanuk on 2014-09-22
So... have had a fully functional Ubuntu 14.04 system installed dual-boot with Win 7 on my Lenovo T530 ThinkPad for months... 12.10, 13.04 & 13.10 before that.  Some hiccups with 14.04, but overall a stable system.

Until this morning. 

The regular system update was grumbling about wine-compholio again as per usual.  So I opened a terminal and manually ran "sudo apt-get update" followed by "sudo apt-get upgrade" with no problems.   Then I rebooted the system,  and now the gui startup hangs @ the "ubuntu" with the five status dots indefinitely. 

I can get to a terminal via Ctrl+Alt+F1, and back via Ctrl+Alt+F7, but no idea where to go from there. 

I can reboot into Win7 just fine, FWIW.

I really need to get to some work I have on my Linux desktop ASAP so any help would be greatly appreciated!

---

### Post by grahammechanical on 2014-09-22
Try Advanced Options for Ubuntu and then Recovery mode and then Resume. And if you get to a desktop try experimenting with video drivers.

Regards.

---

### Post by memilanuk on 2014-09-22
Well... that might have been a step in the right direction,  but still no luck. 

I'd done that once before actually and it just gave a couple popups about entering recovery / low-results mode, may not work, may need to reboot again, etc.

Went thru the process twice in a row and this time it brought me to a login screen.... which I them logged into and.... nothing.  Just a blank bruised purple back ground and a cursor.  No dock no unity, nothing.  I can move the mouse but clicks/keystrokes do nothing.  Ctrl+Alt+F1 just takes me to a blank purple console window from where there is no escape short of power cycling the machine.

---

### Post by memilanuk on 2014-09-22
Figures... only other option I hadn't tried... went from new/current kernel - 3.13-30 - to 3.13-24 (normal mode) and voila!  booted right up to the login window as it should.  Wonder WTF changed... something between the new kernel and my video driver, I imagine?

---

### Post by mastablasta on 2014-09-23
if your driver was properly installed then it should upgrade along with kernel. or at least "patch" the kernel on upgrade.

---

### Post by memilanuk on 2014-09-23
Anything more specific and/or helpful, like how to check if the driver was 'properly installed'?

---

### Post by mreider2 on 2014-09-23
do you know your vid drivers, is it nvidia? I had the same exact issue on my dell latitude E6530 lap with nvidia, i resolved it


[http://ubuntuforums.org/showthread.php?t=2245320](http://ubuntuforums.org/showthread.php?t=2245320)

---

### Post by memilanuk on 2014-09-24
Yep, Nvidia binary/proprietary drivers (331.38 for NVS5400M).

Went thru the process you did in the other thread... seems to be working for now.

Thanks!

Monte

---

### Post by mastablasta on 2014-09-25
well that's good to hear. people can't give more specific and detailed advice unless they know the PC specs. luckily one user had similar issue and directed you to a solution. the solution could be there a lot faster. here is how: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by mreider2 on 2014-09-26
follow up to this solution, there something wrong with latest ubuntu update (few days ago), its still messing up my screen when I close the laptop lid and it goes to sleep. When opening the laptop, its completely frozen, never wakes up, i have to reboot it. Something w nvidia drivers not responding.

---

