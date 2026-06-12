---
title: "no touchpad, no sound"
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by Pedroski55 on 2013-04-29
I installed Ubuntu 13.04, but it had a lot of problems, so I reinstalled 12.04 

Now I have no touchpad. System Settings>Mouse and Touchpad has no tab 'Touchpad', although it did work before, and during the installation, reinstallation.

Also, I now have no sound. System Settings>Sound elicits no sound from the test buttons. The sound card is not set, Output reads 'Dummy Output'

This is a Toshiba 600D Satellite.

Any tips out there???

---

### Post by Pedroski55 on 2013-04-30
Still have no touchpad and no sound, any kind soul have a tip??

---

### Post by manishiitg on 2013-04-30
same problem for me in the latest lenovo laptop

---

### Post by Pedroski55 on 2013-04-30
Something is fishy! I have had such problems with Ubuntu these last 2 days, I nearly went and bought a  new laptop, I was sure this one was broken, but Fedora 18 installs and works no problem, except, I can't get Chinese input working! There is always a catch!!

---

### Post by cortman on 2013-04-30
> **Pedroski55 said:**
> I installed Ubuntu 13.04, but it had a lot of problems, so I reinstalled 12.04 

Now I have no touchpad. System Settings>Mouse and Touchpad has no tab 'Touchpad', although it did work before, and during the installation, reinstallation.

Also, I now have no sound. System Settings>Sound elicits no sound from the test buttons. The sound card is not set, Output reads 'Dummy Output'

This is a Toshiba 600D Satellite.

Any tips out there???

Try running 

```
sudo apt-get install xserver-xorg-input-synaptics
```

---

### Post by Pedroski55 on 2013-04-30
&#30495;&#30340;&#21527;&#65311;
I installed Ubu 12.04 on a computer at work in about 30 mins. Then I used Startup Disk Creator to make a usb boot stick. That got my laptop limping to a start using an older kernel, 3.2. Then I updated, although the touchpad mouse would not work. After an update, I could boot the 3.5 kernel, and suddenly, touchpad and sound were working again!!

The newest kernel 3.8.* will not boot. 
I thought my laptop had memory problems, or some kind of mechanical  failure, but I reinstalled Fedora 18 3 times these last 3 days. No  problems. Also, Windows works. If one kind of Linux can install, and the  other can't, maybe the problem is with the Linux version. I also tried  to install Slackware, but that would not boot. Same kind of problem. 

I  am not an computer person. I just need my laptop to work, and I don't  like windows, especially here in China. It is very intrusive. Maybe I'll  buy a new laptop soon, see if that works ok. 

One thing I learned these last few days: don't upgrade if you don't need to. Don't upgrade just to have the newest version!!

---

