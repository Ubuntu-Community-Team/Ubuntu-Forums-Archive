---
title: "drivers installed, odd screen on boot up"
date: 2015-08-17
forum: Installation &amp; Upgrades
---

### Post by cody26 on 2015-08-17
I am new to Ubuntu and I just installed some new drivers on my computer using the "sudo ubuntu-drivers autoinstall" command. I did this to get my nvidia drivers working (they seem to be working, its using my nvidia graphics card now what's displayed on system settings/details instead of my on-board one) but I get a weird screen (black with white text, terminal style) when I boot up. it says 
[     1.426298] hid (null): usage index exceeded
[     1.417677] hid-generic 0003:264A:1004.0002: usage index exceeded
[     1.417717 hid-generic  0003:264A:1004.0002: item 0 2 2 2 parsing failed
(I don&#8217;t think the numbers except for (item 0 2 2 2 are consistent between reboots)
and then I can log in normally, although I tried updating drivers before (didn't know what I was doing, used command line commands that I found on line) and got this screen and then I couldn&#8217;t even get my GUI to work and had to reinstall Ubuntu.

ps I also now get another screen that flashes for about a quarter second when I shut down, it has the same color/text scheme that the starting screen does (the one that asks how you want to boot, normal, recovery mode etc but I cant get it on long enough to read or take a picture of it).

Can anyone help me with this?

EDIT:I am running Ubuntu 14.04 LTS. Just what I got from the website and put on a flash drive as a system image.

---

### Post by v3.xx on 2015-08-17
```
ub@ub:~$ sudo ubuntu-drivers autoinstall
sudo: ubuntu-drivers: command not found
```

What are you running??

---

