---
title: "Can't boot into anything (Ubuntu, Windows) on Samsung RV518"
date: 2014-08-20
forum: Installation &amp; Upgrades
---

### Post by steve150 on 2014-08-20
Hi,

I've decided to install Ubuntu (14.04 LTS) on my laptop (Samsung RV518) to run alongside with Windows installed. I've installed Ubuntu many times on other computers (dual boot too) and it just worked fine. However, in this time, I encountered a problem. After installing Ubuntu, it booted directly to Ubuntu and when using, sometimes it automatically locked the screen and required to sign in again. I decided to solve the boot menu problem to make the Windows show up first. And then by typing some commands that I even don't understand from Internet with the hope that they will help me solve the problem, the laptop ended up like this guy's computer: [https://www.youtube.com/watch?v=eptpyMbnY4o](https://www.youtube.com/watch?v=eptpyMbnY4o)

I can't boot into anything. I tried to boot from Ubuntu USB, run boot-repair and I got this: [http://paste.ubuntu.com/8100135/](http://paste.ubuntu.com/8100135/)

Any helps will be appreciated. Sorry for my English if you can't get it.

Thanks.

---

### Post by Bashing-om on 2014-08-20
steve150; Hi Welcome to the forum .

You do not say, UEFI ?
UEFI is a whole new ball game, and many of us are just now coming to grips with it .
If we are in fact dealing with UEFI, have a read:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
Then show us what we are working with:
Post back - Between code tags - the out puts of terminal commands:
```

sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f
ls -l /dev/sd*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we see what we can make of this booting situation.

[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT]

---

