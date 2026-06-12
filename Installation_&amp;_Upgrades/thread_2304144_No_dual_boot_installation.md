---
title: "No dual boot installation"
date: 2015-11-24
forum: Installation &amp; Upgrades
---

### Post by Barbu37 on 2015-11-24
Hi , i'm a beginner i read some ubuntu guide for installation but not sure what to do .

First of all i paste my boot-info :
[http://paste.ubuntu.com/13494580/](http://paste.ubuntu.com/13494580/)

As you can see i got 2 disks i want to add one only for ubuntu but i don't want to have a dual boot i want to choose at bios setup either boot on windows installation or linux one .
What's the simpliest way to do that ?

Thanks

---

### Post by sudodus on 2015-11-24
Welcome to the Ubuntu Forums :-)

The easiest way to install is to remove the Windows disk and install automatically to the disk, where you want Ubuntu.

So please tell more about the computer. It makes it easier to help.

1. I found that Windows is installed in BIOS mode.

2. Please specify the hardware of your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

---

### Post by Barbu37 on 2015-11-25
Thx Sudodus , i try with only one disk and it seems ok .I need to use all F6 acpi and the one for graphic adaptater to disable cause livecd crashed.
I think it's due to my exotic PC : Asus p5k/epu with modded 775->771 (xeon x5470) 8 go ram amd 7870 xt.
Ubuntu says me after installation that software cause probleme (in additional drivers it detect my xeon driver as proprietor).
Ubuntu is very slow with the open source amd driver so i change with the lfgr update one and it's very reactive now .
But ... my probleme now i can't reset or shut down ubuntu . I need to force powerbutton shutdown :( 
Any idea ? Thanks

ubuntu x64 15.10

---

### Post by sudodus on 2015-11-25
The first rescue to avoid powerbutton shutdown alias 'hard shutdown' is

***SysRq  [SIZE=3]r e i s u b[/SIZE]***

SysRq is often (but not always) activated with the alt key and the Print Screen key. Keep those keys pressed all the time, and slowly press the key sequence.

See this link [Wikipedia - Magic SysRq key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

-o-

It might be worthwhile to keep looking for and testing other versions of the proprietary drivers.

---

### Post by grahammechanical on 2015-11-25
There are also a couple of useful terminal commands. We can open a terminal by Crtl+Alt+T. Or by right clicking the desktop and selecting Open terminal. If either of those two methods do not work we can open a Linux console with Ctrl+alt+F1. In this case we need to login

to shutdown

```
sudo shutdown -h now
```

To restart

```
sudo shutdown -r now
```

A few clean shut downs and restarts will create a good profile for Ubuntu to do these things.

Regards

---

### Post by Barbu37 on 2015-11-25
Thx both of you . I'll have a look at the Sysrq fonction cause shutdown don't work i tried a few times :(

---

