---
title: "Internal error after latest new Linux kernel for 14.10"
date: 2014-12-14
forum: Installation &amp; Upgrades
---

### Post by dell49 on 2014-12-14
On a Toshiba Portege R835-P56X set up as a dual boot with Windows, I have Ubuntu 14.10 on one side. Yesterday morning, there was a security upgrade that, I saw, included a new Linux kernel version. 

Nothing since. Can log in, but beyond that, nothing. Wallpaper shows, mouse moves, but nothing on the top, nothing on sides (I use Unity). The thing just sits there.

Once, it generated a 'serious internal error' message. It seemed to say--if I read it right--that the problem was "kernel oops" and the report was sent. 

Are others experiencing this problem (I looked around here and didn't see anything similar)?

Is there some way--any way--of fixing this? Or are there Ubuntu-experienced repair people in the Minneapolis-Saint Paul area? Or do I just write off that side of this computer?
Any constructive advice would be greatly appreciated--I really prefer to run Ubuntu to Windows--and thanks in advance.

---

### Post by ibjsb4 on 2014-12-16
Have you tried to revert back to previous working kernel at boot?

[https://www.google.com/search?client=ubuntu&channel=fs&q=how+to+revert+back+to+previous+kernel+ubuntu&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=how+to+revert+back+to+previous+kernel+ubuntu&ie=utf-8&oe=utf-8)

---

### Post by dell49 on 2014-12-17
Yes--launched both 3.16.0-28 in safe mode and 3.16.0-25.

It's actually launching--seemingly normally. But in either instance, after log-in, when it opens, and you'd normally be able to launch whatever and do whatever, the wallpaper is taking up all the available screen, and there is nothing (visible or clickable) on the top or at the side.  If you right click on the wallpaper, you do get the settings menu, which works (and I have to log back in after the usual amount of inactivity). I've played with appearance and display, but still nothing on the top or at the side. I shut down--in order to switch over to Windows--by removing the battery...

---

### Post by ibjsb4 on 2014-12-18
We need to try and generate some error reports.  I have some ideas, but its guesswork without something to go on.  Go to safe mode and try ..
```
dpkg --configure -a
apt-get -f install
```
Could this be a driver problem?
```
lspci | grep VGA
```
Also check software sources.
[ATTACH=CONFIG]258669[/ATTACH]
And you should not need to remove the battery.  In safe mode try ..
```
reboot
```

---

### Post by dell49 on 2014-12-19
I'm sorry, but I guess I haven't been clear about what--how little I still have that I can get to.

There is no command line. There is no icon to get to a command line.

I didn't know how to get to safe mode, so I found this: [http://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/](http://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/)

When the computer is started, after the Toshiba logo, I do get GRUB version 2.02 beta2-15. If I click Ubuntu, what I describe above happens. If I choose advanced options, I get a whole bunch of Linux versions, plus the same versions in recovery mode. I've tried a couple of the recovery mode choices.

A whole bunch of (seeming) diagnostics are run through, far too fast to read or comprehend. Then, as the howtogeek piece says, I get a text menu of resume, clean dpkg, failsafeX and so on. So far, I've been afraid to do anything other than hit resume. But when i do that, Ubuntu seems to load, I get the login screen, and, when I do log in, the same results described above.

Should i try to click dpkg? Or perhaps failsafeX? Or...?

(I did check software sources by following the link you provided. It said NVIDIA Corporation: GF108 [GeForce GT 430] This device is using an alternative driver. The choice that said X.Org X server-Nouveau display drive was clicked.)

---

### Post by ibjsb4 on 2014-12-19
> Should i try to click dpkg? Or perhaps failsafeX?
You can try both.

There are drivers available.
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

Maybe for you it would be easier just to do a reinstall.  And I wonder if 14.04 would be a better choice for you.  It has long term support (LTS) and IMO less likely to break.

---

