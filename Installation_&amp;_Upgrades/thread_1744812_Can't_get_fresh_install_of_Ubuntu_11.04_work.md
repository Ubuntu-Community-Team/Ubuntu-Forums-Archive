---
title: "Can't get fresh install of Ubuntu 11.04 work"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by miLl3niUm on 2011-04-30
Hello everyone, I got a headache from all this mess trying to dual boot Ubuntu/Windows 7 on my computer so I decided to ask for your help. Here is my problem:

Info:
I used Wubi and ubuntu-11.04-desktop-amd64.iso.
Main OS: Windows 7 Pro 64bit
Videocard: Nvidia GT 240


Problems (underlined) as they occured:

1) Installed Ubuntu within Windows, rebooted, saw Ubuntu loading screen (with dots) and then I get _graphics corruption_ (it's really bad I can't recognize anything in the screen).

Then I booted in recovery/failsafe graphic mode and I let the installation finish, then automatically rebooted.

2) Let it boot without pressing anything and instead of graphic corruption it _boots in terminal_.

Tried startx command but it says something relative to "x not found".
Then I found out I had to install proprietary Nvidia drivers so I:

3) Booted again in failsafe graphic mode (in recovery mode) and tried to install it but... _no internet connection_.

I tried "sudo ifconfig eth0 up" and I got: eth0: ERROR while getting interface flags: No such device

NOTE: If I let it boot itself (terminal) **I HAVE** internet connection (found out with wget and ping commands).

---

I know that it was boring to read but I was trying to explain the problems the best I could.

---

### Post by mörgæs on 2011-05-01
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

