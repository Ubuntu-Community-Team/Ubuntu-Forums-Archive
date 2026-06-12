---
title: "Black screen after upgrading to 14.04"
date: 2017-01-11
forum: Installation &amp; Upgrades
---

### Post by gipsyshadow on 2017-01-11
Hi all,
I've got a very old notebook with Pentium M 1.6GHz, 512MB Ram and Intel 855GM chipset and I worked with Lubuntu 12.04. I tried an upgrading to 14.04LTS and en error appeared because my CPU was recognized as non-PAE. So I tried to enable it with these commands:
```
apt-get install linux-image-generic-pae
```
restart and then:
```
cat /proc/cpuinfo | sed 's/flags\t*:/& pae/' > /tmp/cpuinfo_pae
sudo mount -o bind /tmp/cpuinfo_pae /proc/cpuinfo
sudo mount -o remount,ro,bind /proc/cpuinfo
```
and a final check with this:
```
grep flags /proc/cpuinfo
```

After that the upgrading seemed to precede good because after the upgraded packages installation I saw the new look of lubuntu and I was able, for example, to open a pdf.
The problem appeared after restarting the system: firstly the lubuntu logo appeared normally but then the screen was enterely black. Suddenly a window appeared in the upper left corner saying "system program problem detected" then disappeared and the same window appeared in the center of the screen and in my language. After closing this window nothing seems to be possible but the mouse right click. I used the mouse right click menu to get into the terminal and checked lubuntu version and it's "ubuntu 14.04.5 lts" and then I checked something about kernels:
```
dpkg --list | grep linux-image
```
there was a list with the old ones used on 12.04 and the followings too:
```
linux-image-3.13.0-106-generic
linux-image-extra-3.13.0-106-generic
linux-image-generic
linux-image-generic-pae
```
So the best thing is a can get into the terminal 

The only way I found to shut down the system was to close session (I don't know if it's the correct translation) and then a real lubuntu desktop appeared, then I clicked on the shut down button and the system stopped (I didn't log in).

Can I do something to run properly the new 14.04 system? Or only a fresh installation from a live cd can solve it?... I'd not want to loose all my settings with a fresh installation :)

---

### Post by mörgæs on 2017-01-11
14.04 has only a few months left of support so I would suggest that you do a fresh install of Lubuntu 16.04.1, also if it means doing your settings over again.

Here is some advice for the [PAE]("https://help.ubuntu.com/community/PAE") problem.

---

### Post by gipsyshadow on 2017-01-11
Thanks mörgæs for your suggestion :) Firstly I wanted to upgrade to 16.04 but I red it works better with 1GB ram and that notebook has only 512MB and it's too old to spend money for extra ram ;) so I tried 14.04. So I wander if there's a very light lubuntu 16.04 setting to run on my old notebook as good as 12.04 did. Else I'd go back to 12.04 or 14.04. What can you suggest me?

---

### Post by maxbb on 2017-01-12
> **mörgæs said:**
> 14.04 has only a few months left of support so I would suggest that you do a fresh install of Lubuntu 16.04.1, also if it means doing your settings over again.


14.04 is supported until 2019: [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by mörgæs on 2017-01-12
I think you should install 16.04.1 and see for yourself it it's much slower than 12 and 14. I don't see much difference myself.

What slows down the operation are the applications, first of all browsers, not the operative system itself. Try some of the light browsers for comparison.

If you want to go as light as possible then this method is worth trying:
[https://ubuntuforums.org/showthread.php?t=2346891](https://ubuntuforums.org/showthread.php?t=2346891)

---

### Post by mörgæs on 2017-01-12
> **maxbb said:**
> 14.04 is supported until 2019: [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

Only Ubuntu. The other Buntus have three years.

---

### Post by gipsyshadow on 2017-01-16
Sorry for delay but I had some connection troubles.
I finally got a possible way of solution to my problem: I created a new user then I could enter the desktop environment. I did the followings:
when black screen loads press ctrl+alt+f2
after normal login with your user name and password, type
```
sudo adduser hope1
```
and choose your password for "hope1" user
then press ctrl+alt+f7 and login with the new user profile
desktop environment will appear correctly running (at least so happened to me)

I guess the error in the upgrading relied upon "systemd" step because I get this error when I try to stop the system: *"gdbus.error:org.freedesktop.systemd1.loadfailed: unit systemd-poweroff.service failed to load: no such file or directory. see system logs and 'systemctl status systemd-poweroff.service' for details."*

Now I'd like to save my current settings (/home/OldUser) in windows partition or in the other logical (ntfs) partition in my hd but I don't know how to do. Can you help me? I'll add [solved] after that. Thanks

---

### Post by mörgæs on 2017-01-17
> **gipsyshadow said:**
> Can you help me?
If you mean me, then I can't, sorry. I would have taken another approach.

---

