---
title: "Xubuntu 14.04 + Acer 532h: black screen after last update"
date: 2014-07-18
forum: Installation &amp; Upgrades
---

### Post by unhappy_troll on 2014-07-18
Hello ppl. sorry for my english in advance, it's not my native. 
I have old Acer Aspire One NAV50 (532h-2Dbk) with Xubuntu. Last month I upgraded 12.10 to 14.04 and all was fine, until today some updates (new kernel, lightdm, and some else?) was installed manually by apt-get. after reboot xorg is  showing no GUI, just black screen with backlighting. no mouse cursor either. I had read about similar problems on nvidia cards, but this is intel Atom, so what the heck?

lspci -k | grep "VGA" -A2
```
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
        Subsystem: Acer Incorporated [ALI] Device 0349
        Kernel driver in use: i915
```

xrandr -q says ```
Can't open display
```

booting in previous kernel ain't help. restarting lightdm ain't help too. 
well, what was changed for so drastical results, and where?

upd. little update - grub is loaded, i can access console by ctrl-alt-number. it even shows xubuntu loading screen. but after that is a black screen instead of desktop.

Solutions tried so far:
- i915.modeset - no help
- xforcevesa - no help
- nomodeset - no help
- removing .Xauthority, .ICEauthority, .Xdefaults - no help
- Xorg.0.log has no errors
- lightdm.log has no errors
- removing autologin from lightdm.conf get me a login window; after login there is just wallpaper and mouse, nothing else
- it[ looks like that bug]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1283826")

---

### Post by raphael-cohen on 2014-07-18
same on my side since this morning's upgrade. at first I thought it was the graphics drivers and then realized it seems to be lightdm. I decided to boot to wind0ws for now cause I need to get some work done.

---

### Post by unhappy_troll on 2014-07-18
lightdm.log contained no errors. may be xfce failing somehow?

.xsession-init has last string
```
init: process xsession-init pre-start (looks_like_pid) closed with code 1
```

---

### Post by a-you on 2014-07-20
Hi [**[COLOR=#000000]unhappy_troll[/COLOR]**]("http://ubuntuforums.org/member.php?u=1934871"). You may remember me form this thread:

[http://ubuntuforums.org/showthread.php?t=2235030](http://ubuntuforums.org/showthread.php?t=2235030)

you commented there too (thanks). It turns out that in my case the problem seems to have been that I had just before running the "Software Updater" gui tool enabled the "pre-released updates" source. I have just now tested disabling all of the sources and re-enabling them one at a time (but not that one) and the issue is apparently solved for me. Maybe this is useful for you to know??? I just wanted to mention it, in case.

---

### Post by unhappy_troll on 2014-07-21
well, afaik I did not enabled that, but will look into this, thanks.

---

### Post by unhappy_troll on 2014-07-21
btw ```
sudo adduser user1
``` hangs terminal absolutely. after that even ```
sudo su
``` won't work from another tty

---

### Post by unhappy_troll on 2014-07-23
Well, issue did not solved. Moving to Debian.

---

### Post by QIII on 2014-07-23
Best wishes.

---

### Post by Ben_Mather on 2014-08-19
I had this same problem with Ubuntu 14.04, but I managed to fix it by purging everything Nvidia.

By everything I mean EVERYTHING:
```
sudo apt-get remove --purge nvidia-*
```
from [http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely)

Then I was able to login using Nouveau. I use DisplayPort to power one of my monitors so I wasn't content with using Nouveau but it might suit other people.
I installed the latest Nvidia binary driver using the additonal driver (settings > software & updates > additional drivers) and everything is working normally again.

Hope this helps someone. I spend waaay too long troubleshooting this bug and still don't know what the cause was.

---

