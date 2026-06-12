---
title: "Ubuntu will Crash on Login"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by MrTripi2 on 2007-12-01
oh man, i screwed something up.  Seems everytime i restart the computer ubuntu will get as far as the rc.local file (say OK) then after showing me the Nvidia logo it will show me this dialogue of what appears to be corrupted text and an ok button.  I hit ok and it goes back to rc.local file OK then do it again as though it's in an infinite loop.  Being the total linux noob that i am I googled my problem then tried dpkg-reconfigure xserver-xorg and it's still a no go.  I have no idea how to use the recovery console, and I believe I may  have caused this by screwing up when i installed VLC media player(yes I told you I'm a noob).  Basically I just copied the usr folder over the previous one-assuming it would only overwrite files which where already there, leaving the other ones alone.....anyway, it won't start.  Seriously, any help would be greatly appreciated, I'd rather avoid reinstalling linux all over again.

---

### Post by MrTripi2 on 2007-12-01
oh yea i'm not sure if this is anything, i ran the recovery mode terminal, and when i open nautilus-debug-log.txt it say

BEGIN MILESTONES
Invalid borders spefied for theme /usr/share/themes/NoName(NoName=some theme i don't use anymore)
borders don't fit within the image

Invalid borders specified for theme /usr/share/themes/noname/gtk-2.0/scrollbars/slider-vert.png
borders dont' fit within the image

then it will repeatedly state (for a very long time) (USER) : debug log dumped due to signal 11

---

### Post by MrTripi2 on 2007-12-01
ok i used startx in the recovery console and it started in priveleged user mode

Internal Error:
failed to initialize HAL!

then another Error pops up

"User Switcher" has quit unexpectedly:
If you reload a panel object, it will automatically be added back to the panel
..then i can choose to reload or not to reload

I'm guessing this is what happens when i start ubuntu normally, only I can actually read it now in priveleged mode

---

### Post by MrTripi2 on 2007-12-01
....damn it i'm screwed

---

### Post by xeth_delta on 2007-12-01
> **MrTripi2 said:**
> oh man, i screwed something up.  Seems everytime i restart the computer ubuntu will get as far as the rc.local file (say OK) then after showing me the Nvidia logo it will show me this dialogue of what appears to be corrupted text and an ok button.  I hit ok and it goes back to rc.local file OK then do it again as though it's in an infinite loop.  Being the total linux noob that i am I googled my problem then tried dpkg-reconfigure xserver-xorg and it's still a no go.  I have no idea how to use the recovery console, and I believe I may  have caused this by screwing up when i installed VLC media player(yes I told you I'm a noob).  Basically I just copied the usr folder over the previous one-assuming it would only overwrite files which where already there, leaving the other ones alone.....anyway, it won't start.  Seriously, any help would be greatly appreciated, I'd rather avoid reinstalling linux all over again.

You might have skewed permitions and/or replaced files that should not have been touched.
That is not how you should install software that is available in the repositories, it is much easier. You can either use **apt-get**/**aptitude** from the command line or the provided graphical interfaces, for instance **synaptics** or **adept**. With them you will be able to search for and install programs.

Regarding the system not loading, did you change anything in /etc, too? There are some log files useful to try to find out what the problem is. Could you please post the output of the following commands between code tags:

```
dmesg
cat /var/log/Xorg.0.log
cat /var/log/messages
```
Also the contents of your **/etc/rc.local** file. Please do use the code tags (# button in the forum posting tools) to make it easier to read.

Xeth

---

### Post by xeth_delta on 2007-12-01
> **MrTripi2 said:**
> ok i used startx in the recovery console and it started in priveleged user mode

Internal Error:
failed to initialize HAL!

then another Error pops up

"User Switcher" has quit unexpectedly:
If you reload a panel object, it will automatically be added back to the panel
..then i can choose to reload or not to reload

I'm guessing this is what happens when i start ubuntu normally, only I can actually read it now in priveleged mode

The privileged user (root) accout should be used only for administrative purposes or system configuration. Regular programs and especially internet applications should not be run as root, it is a security risk to do so.

One more thing to check. Can you please confirm that you have enough space on your partition? In a terminal:
```
df -h
```

---

### Post by MrTripi2 on 2007-12-01
Pretty sure i have plentyof space left on my partition.  I actually have no connection to the internet though, so not sure how apt-get will help me, also i have no idea what to get.  I've been using linux for about two weeks ><

---

### Post by Craigus on 2007-12-01
It sounds to me as though simply reinstalling might be the solution. Is there any data you need to recover first ?

---

### Post by Peter09 on 2007-12-01
Note that, having had a similar problem, the HAL message and any associated stuff is due to operating in recovery mode.

See if this thread is of any help.

[http://ubuntuforums.org/showthread.php?t=625230](http://ubuntuforums.org/showthread.php?t=625230)

I think that there is a problem in this area for Ubuntu, not sure what ......

---

