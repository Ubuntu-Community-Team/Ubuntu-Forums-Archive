---
title: "screen problems after initial install and initial updates"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by Kevin Jones on 2008-02-21
Dear All,
I recently downloaded ubuntu 7.10 onto an HP pavillion desktop.
I had to install in 'safe graphics mode' .
The install went well, I had internet connection and was able to adjust my screen resolution.
After the initial updates I was asked to restart.
After restarting the screen appears to be split into three or four vertical screens, each seems to be a miniature screen. The whole screen is nearly unreadable, it has lines running horizontally.
I tried rebooting in 'safe mode' (one of the options for Ubuntu, I am not sure of the exact terminology.
I got to a console, but I am so 'newbie' I really did not know what to do. I typed ' init 5 ' and got to the same situation as before.
Can any one help?

Kevin Jones

---

### Post by Partyboi2 on 2008-02-21
What graphics card you using?

---

### Post by Kevin Jones on 2008-02-21
The quick answer is: I have no idea. I have not installed a new video card. It is the video card that came with the desktop.
I can get into windows, and from the control panel I see the following:
device manager
                         Display adapters:
                                                     Intel (R) 82845G/GL/GE/PE/GV Graphics Controller


I am not sure if this is enough, if it is not enough, give me a clue where I can find the information from the windows os system

kevin Jones.
(Must be noon down under?)

---

### Post by Partyboi2 on 2008-02-21
Try booting into recovery mode and when you get to a terminal type
```
 dpkg-reconfigure xserver-xorg
```answer all the questions right through, if unsure what to select choose the default answers, then after you have finished type
```
startx
``` or ```
reboot
```

Its alittle after 3pm down under

---

### Post by Kevin Jones on 2008-02-22
Partyboi2,

Seems to have worked a treat!!!
Nice clear graphics, and the whole thing took about ten minutes.
If you have time:
recommend any tutorials you know. I am interested in the command line. but I am very much a newbie.

Once again...thanks!!!
Problem resolved.

kevin Jones

---

### Post by Partyboi2 on 2008-02-22
[https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=HowToUseTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=HowToUseTheTerminal)
[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)
[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

---

