---
title: "black screen during install on SL510, kubuntu 9.10"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by lunk on 2010-02-01
Hello,

I have a Lenovo SL510 thinkpad (CPU 1.80GHz / 2GB / 250GB SATA / Intel GMA X4500 / 15.6" HD LED says the website), totally fresh, just got it today.
My goal would be to install Kubuntu 9.10 on this machine.
When I try the live CD, screen just goes black, after a while it plays what I assume to be the welcome music.
If I try the conventional install screen is just black.
The safe graphic mode yielded two grey _, one in the 1/5 and one in the 4/5 of the screen.

I begin to suspect my computer hates me.
Any help is very much appreciated.

---

### Post by presence1960 on 2010-02-01
Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso before burning it to CD?

Did you burn the iso at a slow speed (4x-8x is perfect)?

If you pass the above without a hitch boot the Cd and choose "check disk for defects". If a file(s) is found to be bad your disk is no good.

I see you already tried safe graphics mode, but here is a [link]("https://help.ubuntu.com/community/BootOptions") for that and other options at boot.

If all else fails try the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

### Post by lunk on 2010-02-01
I always burn things at slow speed and I'll be sure to MD5SUM future Isos.

In the end I caved in and downloaded the alternative installer, which seemed to have worked just fine.

However, after the installation finished I rebooted and was greeted (after grub and such loaded) with the same unwelcoming black screen (I also noticed a flicker of a grey splot, just before the blackness set in).
I tried logging on (as in entering my user name and then password) and the welcome music played, as if to mock me.

I'm now pretty much sure the problem is caused by the graphic card, however I have no idea how to solve it.
I'll try to reinstall it with 8.10, but in case somebody has a better idea, I would love to hear it.

---

### Post by presence1960 on 2010-02-01
> **lunk said:**
> I always burn things at slow speed and I'll be sure to MD5SUM future Isos.

In the end I caved in and downloaded the alternative installer, which seemed to have worked just fine.

However, after the installation finished I rebooted and was greeted (after grub and such loaded) with the same unwelcoming black screen (I also noticed a flicker of a grey splot, just before the blackness set in).
I tried logging on (as in entering my user name and then password) and the welcome music played, as if to mock me.

I'm now pretty much sure the problem is caused by the graphic card, however I have no idea how to solve it.
I'll try to reinstall it with 8.10, but in case somebody has a better idea, I would love to hear it.

If it is your graphics card post the make & model so someone who has the knowledge can help you out on this.

---

### Post by henius on 2010-02-26
Guys you are really makeing me nervous....What the hell are u talking about, damn noobs ;(....This machine is really heaving problem detecting display...I tryed to conect 22inch monitor and do all the updates....it still doesnt work...
If we wanna solve this its obvious that is nothing wrong with CD...Some guru tech support would be nice.

---

### Post by silencej on 2010-02-26
I am using SL510 too. My ubuntu 9.10 works well, although there are some display mess-ups when booting up, especially when booting up from hibernation. They live in a short time less than 2 seconds and flush away soon.

---

### Post by presence1960 on 2010-02-26
> **henius said:**
> Guys you are really makeing me nervous....What the hell are u talking about, damn noobs ;(....This machine is really heaving problem detecting display...I tryed to conect 22inch monitor and do all the updates....it still doesnt work...
If we wanna solve this its obvious that is nothing wrong with CD...Some guru tech support would be nice.

And just where do you come in on this thread, you haven't posted anything previously? So what are you nervous about?

---

### Post by henius on 2010-02-26
Becouse i tryed ubuntu, ubuntu ultimate, mint and they all have  the same problem....display is not detected corectly...I have the same machine ....Now im just using OpenSuse... So as i said this is not ISO or CD problem guys...

---

### Post by silencej on 2010-03-17
> **henius said:**
> Becouse i tryed ubuntu, ubuntu ultimate, mint and they all have  the same problem....display is not detected corectly...I have the same machine ....Now im just using OpenSuse... So as i said this is not ISO or CD problem guys...

Were you trying to use a dual monitor?
If that is the case, you need to go to system->preferences->display, and option 'on' the second monitor, click 'Apply'.

My Karmic didn't recognize the secondary monitor automatically after i connected the monitor. But after setting in the display dialogue, both monitors work fine, mirrored or extended.

However, there were some messed-up when i changed the primary monitor back and forth, so that i had to reboot.

---

### Post by davidsam on 2010-03-18
I had the same problem, but found a fix on a frensh site. Here is the translated page, see the last post:
[http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fid%3D380075&sl=fr&tl=en](http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fid%3D380075&sl=fr&tl=en)

There is one typo in the guide, the command to update GRUB is:
```
sudo update-grub
```Now the display works fine on my ThinkPad SL510!

---

### Post by silencej on 2010-03-19
My SL510 doesn't have such a problem. So according to your solution, what might be the cause of the problem? The driver of Intel Graphics Card?
P.S. Mine is ATI Raedon 4500.

---

### Post by davidsam on 2010-03-19
> **silencej said:**
> My SL510 doesn't have such a problem. So according to your solution, what might be the cause of the problem? The driver of Intel Graphics Card?
P.S. Mine is ATI Raedon 4500.

Well, I have the Intel GMA 4500MHD, so that may explain why you don't have the same problem. I don't really know exactly what's causing the problem, but according to [http://wiki.sugarlabs.org/go/Nomodeset](http://wiki.sugarlabs.org/go/Nomodeset) it has something to do with communication problems between the kernel and the graphics card.

The issue appear to have been fixed in Ubuntu 10.04, though.

---

