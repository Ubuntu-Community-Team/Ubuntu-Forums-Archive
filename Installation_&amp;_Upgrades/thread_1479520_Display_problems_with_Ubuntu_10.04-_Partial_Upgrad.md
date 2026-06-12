---
title: "Display problems with Ubuntu 10.04- Partial Upgrade"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by junio_buntu on 2010-05-10
Hi,

I am new to Linux, I was using ubuntu 9.04 & 9.10. Recently I  upgraded to 10.04, while doing it I was asked for a **partial upgrade**.  I accepted.

And now I am messed up. Its a worst experience.

I cant see mouse pointer (displayed as 'X'). No maximise, minimise &  close buttons on windows. Cant maximise any window. When I click on  "show desktop button", it says "**Your window manager does not support  the show desktop button, or you are  not running a window manager**".  Complete display is messed up. 

I sorted it out, by changing the visual effects to "Normal" from "None"  in "Appearance preferences". But it is temporary.(plz see the attached  for screen shot)

Every time I reboot, I need to do this.

Can some one fix this, and provide me a permanent solution.

Thanks in advance.

---

### Post by cariboo on 2010-05-11
Have you got the correct drivers for your graphics card installed?

---

### Post by junio_buntu on 2010-05-14
Yes, I have right drivers installed.

Please see the below screen shot.

Thanks.
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by cariboo on 2010-05-17
You may need to run:

```
sudo nvidia-xconfig
```

in a terminal, then reboot.

---

### Post by junio_buntu on 2010-05-17
You may need to run:

Code:
sudo nvidia-xconfig
in a terminal, then reboot.

>>>>>
I did it, still no change.

---

### Post by Lince88 on 2010-05-17
I have the same problem. My graphic card is an integrate form intel I think and does not use privative driver. What can i do?

---

### Post by samolang on 2010-05-24
I have the same problem.  I went to System->Preferences->Appearance, clicked on the "Visual Effects" tabs and changed it from "None" to "Normal".  The problem disappears until I reboot.

---

### Post by hsoulen on 2010-05-24
Check out the following threads:


Why Partial Upgrades should always be refused:

[http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434)

Some help if you get into trouble with a partial upgrade and video issues:

[http://ubuntuforums.org/showthread.php?t=1450282](http://ubuntuforums.org/showthread.php?t=1450282)

Good luck,

Hank

---

### Post by bkburket on 2010-06-09
Same problem as everyone else. Links don't seem to resolve issue. I can fix laptop temp but goes back on reboot. Did NOT chose PARTIAL install on 10.04, but have exactly the same problem.

---

### Post by kelvinator on 2010-06-09
After my upgrade to 10.04 I also had Partial Upgrade messages.
Tonight I looked at my list of repositories and discovered that I had a number of obsolete repositories. Once I unchecked them the problem went away.

[QUOTE=junio_buntu;9276504]Hi,

I am new to Linux, I was using ubuntu 9.04 & 9.10. Recently I  upgraded to 10.04, while doing it I was asked for a **partial upgrade**.  I accepted.

---

