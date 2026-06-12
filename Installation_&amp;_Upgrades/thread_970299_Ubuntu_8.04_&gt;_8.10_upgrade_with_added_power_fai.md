---
title: "Ubuntu 8.04 &gt; 8.10 upgrade with added power failure"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by awalker on 2008-11-04
During an upgrade of my PC from 8.04 to 8.10 the power failed, or actually my wife switched it off as she did not realise it was on.

I do know for a fact it had downlaoded and installed all files as it had just been checked. So I believe it was either doing the file cleanup or was waiting to be rebooted. Not sure exactly where as if I had know it would still have been on;)

So anyway I tried to reboot it with fingers crossed and it came up with the login screen. Hurrah I thought logged in and it went to a black screen with the hour glass ball thingy but then just sat there on teh black screen.

I do have an nvidia card and it did say it would disable third party drivers, which I am sure I was using. I am not sure if this has anything to do with it.

Any help would be appreciated as I am no expert, it was working nicely so I did not fiddle too much.

---

### Post by keplerspeed on 2008-11-04
Hi awalker,

When you log in, can you drop to a terminal?

ctrl-alt-f1 or f2,f3...f6 you should then be prompted to log in through a full screen terminal. ctrl-alt-f7 should take you back to the GUI.

---

### Post by awalker on 2008-11-04
Not sure I can try that later
At work at the moment:cry:

---

### Post by awalker on 2008-11-05
I can get to a terminal screen from the login screen.
Using the options screen I can go to a safe terminal.

I did not use ctrl-alt-f1 or f2,f3...f6 as I forgot it by the time I got home from work:mad:

After trying a normal login again last night it logs in (or accepts it) then the pc just stops and does not go any further.

If I can get to this terminal window should I then be attempting to redo the upgrade as I have seen on other failed upgrade attempts?

Thankyou for your help

---

### Post by Kevbert on 2008-11-05
From the prompt you want to use the following commands (provided you have a live internet connection (wired):
```
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
The first will repair any damaged packages. The second will try to re-install any missing packages. The rest will update software to the latest releases.
If you can't repair, you need to boot with a live CD and backup all your data and then do a clean install (probably your best bet).

---

