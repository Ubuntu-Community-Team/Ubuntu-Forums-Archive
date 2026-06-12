---
title: "upgrade to 12.04 have to wait 3 minutes after login"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by oc_alex86 on 2012-04-30
Hello,

I just upgraded my xubuntu 11.10 to 12.04 and now, when I login, I have to wait about 3 minutes before the desktop appears. Only the background image is displayed. 
Where can this come from?

---

### Post by sparklyprgs on 2012-04-30
At the login screen, press ctrl-alt-f3 to activate a console login and try logging in that way. Do you still get a delay? if not, then you can activate "top" in that console to monitor the cpu (just type top and the command prompt), then switch back to the GUI login with ctrl-alt-f7, login, switch back to the console and watch what might be chewing up CPU time and delaying the login.

---

### Post by Toz on 2012-04-30
Also have a look at the log file ~/.xsession-errors (hidden file in your home directory) - it might yield some clues. If you don't have any access to the desktop from the gui login, you can always, from the console window:
```
pastebinit ~/.xsession-errors
```
...to copy the contents of the file up to pastebin so that you can view it online. Feel free to post back the pastebin link it generates if you'd like a second set of eyes to look at it.

---

### Post by oc_alex86 on 2012-05-01
Thanks for your replies. 
I can indeed login instantaneously in the console. 
However, in top, no process seems to use the CPU. 

I don't have the ~/.xsession-errors file at all.

I also noticed this strange behavior:
If I login first in the console and then in the GUI, it boots quickly. 
If I login first in the GUI, switch to console and login, it takes 3 minutes to boot in the GUI.

---

### Post by Tanker Bob on 2012-05-01
> **oc_alex86 said:**
> Thanks for your replies. 
I can indeed login instantaneously in the console. 
However, in top, no process seems to use the CPU. 

I don't have the ~/.xsession-errors file at all.

I also noticed this strange behavior:
If I login first in the console and then in the GUI, it boots quickly. 
If I login first in the GUI, switch to console and login, it takes 3 minutes to boot in the GUI.

Sounds like you have an nVidia GeForce 6, 7, or 8800 card. I had the same problem. See [this post](http://ubuntuforums.org/showthread.php?t=1969754) for the situation and its resolution.

---

### Post by oc_alex86 on 2012-05-02
No, I don't have one of these graphic cards. 
I have a Thinkpad T420s.

---

