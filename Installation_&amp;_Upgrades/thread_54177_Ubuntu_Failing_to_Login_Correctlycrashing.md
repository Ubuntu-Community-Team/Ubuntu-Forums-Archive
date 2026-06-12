---
title: "Ubuntu Failing to Login Correctly/crashing"
date: 2005-08-03
forum: Installation &amp; Upgrades
---

### Post by kNiFE01 on 2005-08-03
I've Installed ubuntu on my nice new system.  I'm dual booting it with Windows x64 pro edition, on an amd athlon 64 3000+.  Windows logs in and works fine, and ubuntu installed ok. My problem is getting into ubuntu actually. 

When I start the computer I have four or five options for loading ubuntu:
Generic Default
Generic Default (Recovery Mode)
Generic
Generic (recover mode)
something else 
Windows

So If I go to either Generic or Generic Default Ubuntu loads fine straight into the login screen. BUT if I try to change any of the session options on the login screen It freezes everything but the mouse. 
But if I just type in my login and password without messing with any of those settings It logs me into a Blank Brown Desktop with nothing anywhere and no options.  All I can do is move the mouse.

Any help would be appreciated. 

--Green Bear

---

### Post by amohanty on 2005-08-03
What happens when you right click?

---

### Post by kNiFE01 on 2005-08-04
Absolutely nothing. It brings me to a  brown screen where you can play with the mouse but nothing else.  I've even tried some hotkey combos, you know shortcuts, those don't work either.

---

### Post by amohanty on 2005-08-05
Can you drop into the failsafe mode and post the result of:

>> dmesg| tail -n 50

AM

---

### Post by Shinigami-Sama on 2005-08-06
[QUOTE=amohanty]Can you drop into the failsafe mode and post the result of:

>> dmesg| tail -n 50

AM[/QUOTE]
 ahh
almost the exact same problem, only I can't change sessions or move my mouse after the horay slapsh screen and sound (which crackles and fails)
running on a persario 4000series (amd64 3500+ - 1028mb ram - 80gb hdd - ati radon xpress 200m)
dual boot with win xp sp2
xp runs fine
ubuntu is installed on an ext3 partition of 5.4gb
has a 2.02gb swap
11.1gb fat32 shared with windows
and a 20gb ext3 for linux files
the rest is on an ntfs partition

---

### Post by amohanty on 2005-08-06
Type in  Ctrl+Alt+F1 . This will drop you to a console, and then type in 
>> dmesg | tail -n 50

AM

---

