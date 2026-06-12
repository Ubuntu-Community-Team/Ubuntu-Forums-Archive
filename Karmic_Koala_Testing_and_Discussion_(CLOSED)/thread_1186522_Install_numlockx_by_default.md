---
title: "Install numlockx by default"
date: 2009-06-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2009-06-13
So I'm not sure why, but on about 5 different computers I've tried ubuntu on, numlock is not enabled by default when computer starts. In order to enable it you have to press numlock about 3 times or so.

So I have to install numlockx on every computer in order for numlock to work when computer starts (it works great and does the job).

Why hasn't this been fixed yet? Am I the only person who prefers numlock enabled at boot (desktop)?
Is there a reason why numlock is not enabled by default? Doesn't windows and mac enabled numlock by default?

[https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)
Are people supposed to know to install numlockx after installing ubuntu?

---

### Post by shafin on 2009-06-13
> **andrewabc said:**
> So I'm not sure why, but on about 5 different computers I've tried ubuntu on, numlock is not enabled by default when computer starts. In order to enable it you have to press numlock about 3 times or so.

So I have to install numlockx on every computer in order for numlock to work when computer starts (it works great and does the job).

Why hasn't this been fixed yet? Am I the only person who prefers numlock enabled at boot (desktop)?
Is there a reason why numlock is not enabled by default? Doesn't windows and mac enabled numlock by default?

[https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)
Are people supposed to know to install numlockx after installing ubuntu?
+1
Its same for me, I have to install numlockx everytime I set up a system. At least there should be a way to get this done without installing a new package.

---

### Post by ajgreeny on 2009-06-13
From what I recall in jaunty and all the previous versions, it was simply a case of enabling numlock the first time I used ubuntu and it has always been enabled on startup ever since.  I certainly have not needed to press it about three times, but perhaps this is just something different about 9.10KK?

---

### Post by ronacc on 2009-06-13
numlock was on for me from install .

---

### Post by doas777 on 2009-06-13
Interesting. i have always installed numlockx. and have continued to do so on jaunty, but I do have a terminal that does not register numlock at all, and i think the problem started when I added numlockx to the gdm preinit script. wonder if all will be well when I remove it.

i wonder if the numlock issues with vnc are fixed as well?

---

### Post by shakaran on 2009-06-13
+1 Numnlockx is my first package on install.

---

### Post by MacUntu on 2009-06-13
Are your computer's names 'localhost'? I remember vaguely that there is a problem with saving the numlock state when your machine's name is 'localhost' (no idea why).

---

### Post by novafluxx on 2009-06-13
This very well may be a BIOS setting as well, that Windows does/does not obey. On portable system (notebooks, netbooks, etc) the numlock key can be used to enable the number pad in the middle of the keyboard

---

### Post by Darkshade on 2009-06-13
In KDE you can go to System Settings -> Keyboard and Mouse, and then choose if you want your numlock to be enabled, disabled or left as it was last time you shut down / restarted when you boot again.

---

### Post by andrewabc on 2009-06-13
> **novafluxx said:**
> This very well may be a BIOS setting as well, that Windows does/does not obey. On portable system (notebooks, netbooks, etc) the numlock key can be used to enable the number pad in the middle of the keyboard

That's what I thought at first, but then windows must somehow know this and enable/disable it properly.

I also agree with making sure numlock (NOT numlockx) is enabled (working) before installing. This way it might remember the setting when booting normally.

---

### Post by cariboo on 2009-06-13
I have numlock on enabled at boot in the BIOS and never have a problem. I can't say if it works in Windows or not.

---

### Post by Gourgi on 2009-06-13
> **ajgreeny said:**
> From what I recall in jaunty and all the previous versions, it was simply a case of enabling numlock the first time I used ubuntu and it has always been enabled on startup ever since.  I certainly have not needed to press it about three times, but perhaps this is just something different about 9.10KK?

first time enabling it works here too :popcorn:

---

### Post by LordVeovis on 2009-06-14
Numlock doesn't work in Windows by default either (at least with xp fresh install any version. Not sure of vista). Any XP manually installed has no numlock enabled at first boot. It also only saves the numlock state post logon. This means that during the login screen it will not have enabled numlock yet. After you logon, it checks that user's setting for numlock an either enables or disables it (assuming you enabled during logon, but your user pref was disabled). It also saves that user preference based on the state of numlock on shutdown. This may be different on netbook offerings, and possibly laptops? but every desktop I have installed on (100s) this has been the condition of numlock in windows.

EDIT: Spelling

---

### Post by andrewabc on 2009-06-14
> **LordVeovis said:**
> Any XP manually installed has no numlock enabled at first boot. It also only saves the numlock state post logon. This means that during the login screen it will not have enabled numlock yet. After you logon, it checks that user's setting for numlock an either enables or disables it (assuming you enabled during logon, but your user pref was disabled).

Then hopefully ubuntu can learn that I had numlock enabled next time I reboot on a fresh install, instead of me having to install numlockx.

---

