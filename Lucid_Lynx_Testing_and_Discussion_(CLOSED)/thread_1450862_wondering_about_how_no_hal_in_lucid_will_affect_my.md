---
title: "wondering about how no hal in lucid will affect my system"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hart02 on 2010-04-09
I am wondering about lucid and my post and how there is no hal in 10.04.
I ask because I have had the frozen keyboard issue before. I posted how to fix it here.
[http://ubuntuforums.org/showthread.php?t=1430176]("http://ubuntuforums.org/showthread.php?t=1430176")
It says this:
> Some people have had issues with their keyboard being frozen at login. I was one of those people until I discover a workaround. Here is how I managed to fix it for me:

First when I get to the login screen which is frozen I press and hold **Alt+PrintScrn**
Then I press **R+E** which takes me to the console and login as my user
Next I type **sudo service dbus force-reload**
After that I type **sudo gdm**
I Finally select my user,then I press a key and It's alive NumLock and all.
I have tried this with wdm and it didn't work for me. I am not sure about other login managers working but I will stick with gdm. Also I removed the packages xorg and ubuntu-desktop so you should test this technique with those installed. I am using lxde as my desktop.Now if only someone could automate this with an init.d script.

However I wrote this for 9.10 as a tutorial and sometimes if force reloading dbus was not enough, I would **Alt+PrintScrn** and **R+E** and type
**sudo kill gdm** and then type a command to start hal if it was not running then start gdm. All was well. So if hal is not present in 10.04, Then has it been replaced by something else?:confused:

---

### Post by antsh86 on 2010-04-09
I am having the keyboard freeze issue as well. The splash screen goes for a while, and then all of a sudden it freezes and the only way out is a hard reboot that I am aware of. System specs as follows:

ASUS P5K Premium (Intel P35)
Intel Q6600
Nvidia 9800GTX
Creative X-Fi ExtremeMusic
Storage set to AHCI in BIOS

Any help about how to get around this issue would be really great. Thanks in advance.

---

