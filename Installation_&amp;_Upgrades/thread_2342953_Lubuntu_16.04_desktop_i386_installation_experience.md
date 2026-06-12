---
title: "Lubuntu 16.04 desktop i386 installation experience on D420 32bit laptop"
date: 2016-11-11
forum: Installation &amp; Upgrades
---

### Post by elim-qiu on 2016-11-11
It's Dell Latitude D420, Intel U1300@1.06GHz,  1.5Gb Memory,  1280x800 LCD, bcm43xx wifi adaptor.

Originally Ubuntu 14.04 32bit installed with 2 partitions mounted as / and /home.

I made a lubuntu-16.04-desktop-i386 USB installer.

ISSUE #1, The installer's [try without install] option doesn't work.
          It says wifi firmware not found and refuse further booting...c

So I just went to real installation open, specified the same mount points on existing two partitions (the rest 3rd partition is swap area)but just format the one mounted as /. That way I kept my user data... 

ISSUE #2, When the installation completed, the resulting system was not accessiable, error was just like ISSUE #1. The worst thing is that there is no boot option menu displayed. The booting stopped with some check disk result displayed(the disk was fine)

Then I thought my downloaded lbuntu-16.04-desktop-i386.iso might has some problem and tried the alternate iso. Well I aborted the try because I'm not sure it'll give me the choice that keep /home as was....
Then I downloaded lubuntu-16-04-32-bit.iso. Tried the option [try without install], it's not work either. But who knows what I did but suddenly I got the boot menu and I choosed rescure booting, that gave me the chance to download some missing pakages and some auto fixes(I just follow the prompts...). Then it prompts me exit the rescure booting and continue the normal (1st) booting.

ISSUE #3. The system didn't recognize my LCD resolution, give me 1024x768(the best possible) instead of 1280x800.
After run Software Updater, this was automatically fixed.

ISSUE #4. My wifi not working as it always.  It can be fixed by doing
```
[COLOR=#000000][FONT=Courier New]sudo apt-get update[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]sudo apt-get remove bcmwl-kernel-source[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]sudo apt-get install firmware-b43-installer[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]sudo reboot[/FONT][/COLOR]
```

ISSUE #5. Midori sometimes become unresponsive...(not because I run out of system resource)
I don't know how to fix it...  I simply dislike Firefox. It renders #1 ugly MathJax contents among all browsers...

ISSUE #6. Fcitx pinyin shows a big black frame that covers the char choice menu
This is actually an official bug: [https://bugs.launchpad.net/ubuntu/+source/fcitx/+bug/1513571](https://bugs.launchpad.net/ubuntu/+source/fcitx/+bug/1513571)
The following command
```
[COLOR=#333333][FONT=monospace]sudo apt-get install qtdeclarative5-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]qtquick2-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]plugin
[/FONT][/COLOR]
```
Fixed the issue for me:)

I did all the above last night. Will see if there are any morie issues. I don't know which issue is machine dependent... But I'm sure lubuntu 16.04 need more fixings than ubuntu 16.04. My old laptop likes lubuntu.

Wellcome share your lubuntu 16.04 exeriences and advices here.

---

### Post by mörgæs on 2016-11-12
Regardless of hardware it's always a good idea to use wired internet connection during install and the first reboots. Saves a lot of problems.

> **elim-qiu said:**
> The worst thing is that there is no boot option menu displayed.

In a single boot install this is the default behaviour.

---

### Post by elim-qiu on 2016-11-14
ISSUE #7     After set close the lid suspend the system, it asked me re-login twice when I re-open the lid.

---

### Post by elim-qiu on 2016-11-14
Thanks mörgæs' great inputs.

Is there some way to force boot menu displayed?

---

### Post by mörgæs on 2016-11-15
[https://ubuntuforums.org/showthread.php?t=2060292&p=12249599&viewfull=1#post12249599](https://ubuntuforums.org/showthread.php?t=2060292&p=12249599&viewfull=1#post12249599)

---

